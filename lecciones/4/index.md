---
title: 4. Control de flujo
layout: default
---

<div style="width: 100%; padding: 40px; color: white; font-weight: bold; text-align-enter">flujo</div>

Vamos a programar de verdad. Creo que lo mejor va a escriba un trozo de código y lo explique línea 
por línea.

{% highlight php %}

$nombreDeLaPersona = "Garikoitz Subijana Lertxundi";
$pesoTotal = 0;

for ($i = 0; $i < strlen($nombreDeLaPersona); $i++) {
    $pesoTotal = $pesoTotal + ord($nombreDeLaPersona[$i]);
}

echo $nombreDeLaPersona . ' pesa ' . $pesoTotal . ' kg.';

{% endhighlight %}

Esto es una versión simplificada de aquel ejemplo de la [lección 1](/lecciones/1/), ahora en PHP en lugar de JavaScript. Hay un montón nde cosas que ver.

## Variables!

El programa comienza **declarando** dos variables, `nombreDeLaPersona` y `pesoTotal`. En PHP las variables
llevan un `$` delante del nombre. En este caso también **inicializamos** las variables, usando el operador
de asignación. Cada línea termina con un punto y coma (`;`), que se usa para terminar *sentencias*.

## Bucles!

## Funciones!

## Datos de salida!

