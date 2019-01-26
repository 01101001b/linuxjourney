# Systemd Goals

## Lesson Content

No entraremos en detalle de cómo escribir archivos de unidades de systemd. Sin embargo, veremos muy por encima un archivo de unidad y cómo controlar las unidades manualmente.

A continuación un archivo bastante básico de unidad de servicio: foobar.service

<pre>
[Unit]
Description=My Foobar
Before=bar.target

[Service]
ExecStart=/usr/bin/foobar

[Install]
WantedBy=multi-user.target
</pre>

Este es un objetivo simple de servicio. Al principio del archivo vemos la seccion [Unit] que permite una descripcion de nuestro archivo de unidad y controlar en qué orden activarla. Le sigue la sección [Service], donde podemos iniciar, detener y reiniciar un servicio. Y la sección [Install] es para dependencias. Esto es apenas el abc de escribir archivos de systemd; si el tema te interesa, hallarás en internet mucho material que leer.

Ahora, metámonos con algunos comandos para usar con unidades de systemd:

<b>Listar unidades</b>

<pre>$ systemctl list-units</pre>

<b>Ver el estado de una unidad</b>

<pre>$ systemctl status networking.service</pre>

<b>Iniciar una unidad</b>

<pre>$ sudo systemctl start networking.service</pre>

<b>Detener una unidad</b>

<pre>$ sudo systemctl stop networking.service</pre>

<b>Reiniciar una unidad</b>

<pre>$ sudo systemctl restart networking.service</pre>

<b>Habilitar una unidad</b>

<pre>$ sudo systemctl enable networking.service</pre>

<b>Deshabilitar una unidad</b>

<pre>$ sudo systemctl disable networking.service</pre>

Recuerda, systemd es un tema muy amplio. Si investigas, sabrás de él tanto como quieras.

## Exercise

Observa el estado de las unidades e inicia y detén algunos servicios ¿Notas algo?

## Quiz Question

¿Qué comando inicia un servicio de nombre peanut.service?

## Quiz Answer

sudo systemctl start peanut.service
