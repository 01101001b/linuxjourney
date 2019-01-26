# System V Overview

## Lesson Content

El propósito principal de init es iniciar y detener procesos esenciales del sistema. Hay tres grandes implementaciones de init en Linux: System V, Upstart y systemd. En esta lección, veremos la versión mas tradicional de init: System V init o Sys V (pronunciado como 'System Five').

Para saber si la estás utilizando, verifica si tienes el archivo /etc/inittab. 

Sys V inicia y detiene procesos secuencialmente; de modo que si quisieras iniciar un servicio de nombre foo-b, tienes que asegurarte que foo-a ya se encuentre corriendo. Sys V hace esto mediante scripts que inician y detienen servicios por nosotros. Podemos escribir nuestros propios scripts o las más de las veces usar los que ya vienen implementados en el sistema operativo para cargar servicios esenciales. 

La ventaja de esta implementación de init es lo relativamente fácil de resolver dependencias, pues sabes que foo-a viene antes de foo-b. Sin embargo la performance no es genial pues usualmente se inicia o detiene una cosa por vez.

Al usar Sys V, el estado de la máquina lo definen niveles de ejecución que van del 0 al 6. Estos diferentes niveles variarán según la distro (distribución) pero la mayoría de las veces se verán así:

<ul>
<li>0: Apagar</li>
<li>1: Modo monousuario</li>
<li>2: Modo multiusuario sin (soporte de) red</li>
<li>3: Modo multiusuario con (soporte de) red</li>
<li>4: No utilizado</li>
<li>5: Modo multiusuario con (soporte de) red y GUI (interfaz gráfica)</li>
<li>6: Reiniciar</li>
</ul>

Cuando inicia, tu sistema busca en qué nivel de ejecución estás y ejecuta los scripts ubicados en la configuración de tal nivel. Los scripts están en <b>/etc/rc.d/rc[número de nivel de ejecución].d/</b> o <b>/etc/init.d</b>. Los scripts que empiecen con S (start) o K (kill) correrán al iniciar o apagar el sistema respectivamente. Los números al lado de esas letras son la secuencia en que se ejecutarán.

Por ejemplo:

<pre>
pete@icebox:/etc/rc.d/rc0.d$ ls
K10updates  K80openvpn
</pre>

Vemos cuando cambiamos al nivel de ejecución 0 (modo apagar), nuestro equipo intentará ejecutar un script para matar el servicio de "updates" (actualización) y luego el de "openvpn". Para conocer el nivel de ejecución (por defecto) con que inicia tu sistema mira el archivo /etc/inittab. Ahí puedes modificar tu nivel de ejecución por defecto si lo deseas.

Hay que señalar aunque System V está siendo lentamente reemplazado, eso no sucederá hoy ni en varios años. Sin embargo, verás niveles de ejecución en otras implementaciones de init para dar soporte a servicios que solo son iniciados o detenidos con scripts de System V init. 

## Exercise

Si estás ejecutando System V init, cambia el nivel de ejecución por defecto de tu máquina a otro y ve qué sucede.

## Quiz Question

¿Qué nivel (número) de ejecución generalmente apaga el sistema?

## Quiz Answer

0
