# Upstart Jobs

## Lesson Content

Upstart puede iniciar muchos eventos y trabajos. Desafortunadamente no hay manera simple de ver dónde se originó uno u otro: tendrás que sondear las configuraciones de trabajos en /etc/init. Las más de las veces jamás necesitarás mirar las configuraciones de trabajo de Upstart, pero sí querrás controlar algún trabajo específico más fácilmente. Hay un montón de comandos útiles que puedes usar en un sistema Upstart. 

<b>Ver trabajos</b>

<pre>initctl list

shutdown stop/waiting
console stop/waiting
...
</pre>

Verás una lista de trabajos Upstart con diferentes estados aplicados a ellos. En cada línea, el nombre del trabajo es el primer valor, y el segundo campo (antes de /) es el objetivo del trabajo. El tercer valor (despues de /) es el estado actual. Así vemos que nuestro trabajo de apagado (shutdown) eventualmente quiere parar, pero se halla en estado de espera. Los estados y objetivos de un trabajo cambiarán a medida que inicies o detengas (otros) trabajos. 

<b>Ver un trabajo específico</b>

<pre>initctl status networking
networking start/running
</pre>

No entraremos en detalles de cómo escribir una configuración de trabajo en Upstart; pero sabemos  que se inician, detienen y reinician trabajos en estas configuraciones. Estos trabajos también emiten eventos, es decir que pueden iniciar otros trabajos. Veremos los comandos manuales de operación de Upstart, pero si eres curioso, tienes los archivos .conf para mirar con detenimiento.

<b>Iniciar un trabajo manualmente</b>

<pre>$ sudo initctl start networking</pre>

<b>Detener un trabajo manualmente</b>

<pre>$ sudo initctl stop networking</pre>

<b>Reiniciar un trabajo manualmente</b>

<pre>$ sudo initctl restart networking</pre>

<b>Emitir un evento manualmente</b>

<pre>$ sudo initctl emit some_event</pre>

## Exercise

Observa tu lista de trabajos Upstart y cambia el estado de un trabajo con los comandos que aprendimos hoy. ¿Qué notas a continuación?

## Quiz Question

¿Cómo reiniciaría yo manualmente un trabajo de nombre peanuts?

## Quiz Answer

sudo initctl restart peanuts
