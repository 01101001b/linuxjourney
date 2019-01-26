# Power States

## Lesson Content

Es de no creer que hasta ahora no viéramos los distintos modos de controlar tu sistema usando la línea de comandos. Cuando se trata de init, hay modos de iniciar nuestro sistema y modos de detenerlo.

Para detener el sistema

<pre>$ sudo shutdown -h now</pre>

Esto apagará el sistema inmediatamente (now = ahora). Siempre debes indicar cuándo quieres que eso ocurra. Puedes hacerlo usando minutos.

<pre>$ sudo shutdown -h +2</pre>

Con esto el sistema apagará en dos minutos. Con el comando shutdown, incluso puedes reiniciar el sistema:

<pre>$ sudo shutdown -r now</pre>

O si prefieres, usa (el comando) reboot.

<pre>$ sudo reboot</pre>

## Exercise

¿Qué imaginas que ocurre con init cuando apagas tu equipo?

## Quiz Question

¿Qué comando apagaría tu sistema en 4 minutos?

## Quiz Answer

sudo shutdown -h +4
