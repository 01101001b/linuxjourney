# Upstart Overview

## Lesson Content

Upstart fue desarrollado por Canonical, por lo que fue la implementación de init en Ubuntu por algún tiempo; sin embargo, en las instalaciones más recientes de Ubuntu ahora se usa systemd. Upstart se creó como una respuesta mejorada a los problemas de Sys V, como ser un proceso de inicio rígido, tareas bloqueadas, etc. El modelo regido por eventos y trabajos de Upstart le permite responder a los eventos a medida que aparecen.

Para concluir si estás usando Upstart, tener el directorio /usr/share/upstart es un indicador bastante bueno.

Se les llama trabajos a las acciones que realiza Upstart y eventos a los mensajes recibidos de otros procesos para iniciar (disparar) trabajos. Para ver una lista de trabajos y su configuración:

<pre>
pete@icebox:~$ ls /etc/init
acpid.conf                   mountnfs.sh.conf
alsa-restore.conf            mtab.sh.conf
alsa-state.conf              networking.conf
alsa-store.conf              network-interface.conf
anacron.conf                 network-interface-container.conf
</pre>

En estas configuraciones, se incluye información de cómo y cuando iniciar los trabajos.

Por ejemplo, en el archivo networking.conf, se podría decir algo tan simple como:

<pre>
start on runlevel [235]
stop on runlevel [0]
</pre>

Esto significa que empezará preparando el soporte de red en los niveles de ejecución 2, 3 o 5 y que lo detendrá en el nivel 0. Hay muchas formas de escribir el archivo de configuración y descubrirás eso cuando mires en las diferentes configuraciones de trabajo disponibles.

El modo en que Upstart trabaja es este:

<ol>
<li>Carga las configuraciones de los trabajos desde /etc/init.</li>
<li>Una vez que sucede un evento de inicio, ejecutará trabajos disparados por tal evento.</li>
<li>Estos trabajos generarán nuevos eventos y estos eventos dispararán más trabajos.</li>
<li>Upstart continua haciendo esto hasta que completa todos los trabajos necesarios.</li>
</ol>

## Exercise

Si corres Upstart, ve si puedes entender las configuraciones de trabajo en /etc/init.

## Quiz Question

¿Qué implementación init usa Ubuntu?

## Quiz Answer

upstart
