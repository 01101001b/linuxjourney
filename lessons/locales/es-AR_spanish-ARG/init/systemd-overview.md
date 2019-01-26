# Systemd Overview

## Lesson Content

Systemd lentamente se está perfilando como un standard de init. Si tienes el directorio /usr/lib/systemd, es probable que lo estés utilizando.

Systemd utiliza objetivos para que tu sistema marche y funcione. Basicamente, tienes un objetivo (target) que quieres alcanzar y este objetivo tiene dependencias que tenemos que cumplir. Systemd es extremadamente flexible y robusto; no sigue una sequencia estricta para iniciar procesos. A continuación, un arranque normal de systemd:

<ol>
<li>Systemd carga sus archivos de configuración, generalmente ubicados en /etc/systemd/system o /usr/lib/systemd/system</li>
<li>Determina el objetivo de arranque (usualmente default.target).</li>
<li>Systemd deduce las dependencias del objetivo (de arranque) y las activa.</l>
</ol>

Similar a los niveles de ejecución de Sys V, systemd puede bootear (iniciar) en diferentes targets (objetivos):

<ul>
<li>poweroff.target - apagar sistema</li>
<li>rescue.target - modo monousuario</li>
<li>multi-user.target - modo multiusuario con (soporte de) red</li>
<li>graphical.target - modo multiusuario con (soporte de) red e interfaz gráfica</li>
<li>reboot.target - reiniciar</li>
</ul>

El objetivo del arranque por defecto de defaults.target usualmente es graphical.target.

El componente principal con el que systemd trabaja se conoce como "unidad". Systemd no detiene e inicia servicios únicamente, puede montar sistemas de archivo, monitorear sockets de red, etc. y por tal robustez tiene y opera con diferentes tipos de unidades. Las más comunes son:

<ul>
<li>Unidades "service" (de servicio) - los servicios que hemos estado iniciando y deteniendo; estos archivos de unidades terminan en .service</li>
<li>Unidades "mount" (de montaje) - montan sistemas de ficheros; estos archivos de unidades terminan en .mount</li> 
<li>Unidades "target" (de objetivo) - agrupan otras unidades; estos archivos de unidades terminan en .target</li>
</ul>

Como ejemplo, supongamos que arrancamos en nuestro default.target. Esta unidad de objetivo agrupa unidades como networking.service, crond.service, etc. así que cuando activamos esta sola unidad, todo lo que dependa de ella será activado tambíén.

## Exercise

No hay ejercicios para esta lección.

## Quiz Question

¿Qué tipo de unidad se usa para agrupar otras unidades?

## Quiz Answer

target
