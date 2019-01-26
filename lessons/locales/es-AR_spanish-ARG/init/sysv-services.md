# System V Service

## Lesson Content

Hay muchas herramientas de línea de comando que puedes utilizar para administrar servicios de Sys V.

<b>Listar servicios</b>

<pre>$ service --status-all</pre>

<b>Iniciar un servicio</b>

<pre>$ sudo service networking start</pre>

<b>Detener un servicio</b>

<pre>$ sudo service networking stop</pre>

<b>Reiniciar un servicio</b>

<pre>$ sudo service networking restart</pre>

Estos comandos no son específicos de sistemas que usan Sys V; puedes usarlos también con servicios de Upstart. Aunque Linux está distanciandose de a poco de los más tradicionales scripts de Sys V, algunas cosas perduran para ayudar a esa transición.

## Exercise

Elige un par de servicios y cambia su estado ¿qué observas?

## Quiz Question

¿Qué comando en Sys V detendría un servicio de nombre peanut?

## Quiz Answer

sudo service peanut stop
