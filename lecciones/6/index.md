---
title: 6. Funciones
layout: default
---

Así que podemos contar letras, sumar números y ponerlos en la pantalla. El siguiente paso es
hacerlo con más gente, para comparar el peso de Garikoitz con el de Agurtzane Mendikozelaia Agirrebeitia.
¿Quién es más pesado?

{% highlight php %}
<?php

// primero Garikoitz

$garikoitz = "Garikoitz Subijana Lertxundi";
$pesoDeGarikoitz = 0;

for ($i = 0; $i < strlen($garikoitz); $i++) {
    $pesoDeGarikoitz = $pesoDeGarikoitz + ord($garikoitz[$i]);
}

echo $garikoitz . ' pesa ' . $pesoDeGarikoitz . ' kg.';

// y ahora Agurtzane

$agurtzane = "Agurtzane Mendikozelaia Agirrebeitia";
$pesoDeAgurtzane = 0;

for ($i = 0; $i < strlen($agurtzane); $i++) {
    $pesoDeAgurtzane = $pesoDeAgurtzane + ord($agurtzane[$i]);
}

echo $agurtzane . ' pesa ' . $pesoDeAgurtzane . ' kg.';

{% endhighlight %}

Esto no es buena práctica, por motivos obvios. Estamos comparando a dos personas, pero ¿qué
pasa cuando tengamos diez? No podemos copiar y pegar el mismo código cada vez que queramos añadir
una persona. ¡Necesitamos una función!

## Segunda mano

Cuando escribimos programas nos encontramos con pequeños problemas que tenemos que nresolver una y otra vez,
y pronto nos cansaremos de repetir el mismo trozo de código una y otra vez. Por suerte, podemos extraer
las partes comunes de un trozo de código, ponerlas en lugar común, y simplemente hacer referencia a ese
lugar común cuando queramos realizar la operación de nuevo. En nuestro caso, el bucle `for` y la sentencia
`echo` son idénticas en ambas secciones del programa: lo único que cambia es el nombre de cada persona.

Vamos a crear una función: un bloque de código que puede recibir datos, realiza una serie de operaciones (probablemte
usando esos datos que ha recibido) y devuelve (opcionalmente) un valor. Las funciones reciben nombres distintos
en distintos lenguages de programación. En C/C++, PHP JavaScript o Python se llaman simplemente funciones, pero
en Java sólo existen  *métodos*, en Lisp además de funciones hay *expresiones lambda*, Pascal y Delphi tienen
también *procedimiento* y otros programas tiene subrutinas. La idea siempre es la misma: reutilizar código
para no escribir siempre lo mismo, reduciendo el tamaño del programa y la probabilidad de cometer errores.

## Redundantemente

Si miramos el código de arriba de nuevo podemos ver que `$garikoitz` y `$agurtzane`, las variables, tienen el
mismo papel (almacenar el nombre de la persona), al igual que `$pesoDeGarikoitz` y `$pesoDeAgurtzane` (almacenar el 
peso total). Empecemos por homogeneizar un poco el código, reemplazando el nombre de las variables que almacenan 
el nombre y el peso pero con otras iguales para ambas secciones:

{% highlight php %}
<?php

// primero Garikoitz

$nombre = "Garikoitz Subijana Lertxundi";
$peso = 0;

for ($i = 0; $i < strlen($nombre); $i++) {
    $peso = $peso + ord($nombre[$i]);
}

echo $nombre . ' pesa ' . $peso . ' kg.';

// y ahora Agurtzane

$nombre = "Agurtzane Mendikozelaia Agirrebeitia";
$peso = 0;

for ($i = 0; $i < strlen($nombre); $i++) {
    $peso = $peso + ord($nombre[$i]);
}

echo $nombre . ' pesa ' . $peso . ' kg.';

{% endhighlight %}

Ahora las dos secciones del programa, para ambas personas, sólo difieren en el valor de la variable `$nombre`.
Estamos listos para crear una función que contenga en resto del programa:


{% highlight php %}
<?php

// nuestra función
function peso()
{
    $peso = 0;

    for ($i = 0; $i < strlen($nombre); $i++) {
        $peso = $peso + ord($nombre[$i]);
    }

    echo $nombre . ' pesa ' . $peso . ' kg.';
}

// primero Garikoitz
$nombre = "Garikoitz Subijana Lertxundi";

// y ahora Agurtzane
$nombre = "Agurtzane Mendikozelaia Agirrebeitia";

{% endhighlight %}

Ahora mismo este programa no hace nada, porque el código que ponemos dentro de las funciones no se
ejecuta mientras no llamemos a la función. En nuestro caso, tenemos que llamar a `peso()` dos veces:

{% highlight php %}
<?php

// nuestra función
function peso()
{
    $peso = 0;

    for ($i = 0; $i < strlen($nombre); $i++) {
        $peso = $peso + ord($nombre[$i]);
    }

    echo $nombre . ' pesa ' . $peso . ' kg.';
}

// primero Garikoitz
$nombre = "Garikoitz Subijana Lertxundi";
peso();

// y ahora Agurtzane
$nombre = "Agurtzane Mendikozelaia Agirrebeitia";
peso();

{% endhighlight %}

Pero esto todavía no es suficiente; dentro de la función `peso()` estamos usando la variable `$nombre`, pero
las funciones tienen su propio *ámbito*, lo que significa que no saben qué sucede a su alrededor. La variable
`$nombre` está definida fuera de la función `peso()`, y por lo tanto no podemos usarla dentro. Literalmente,
`peso()` no tiene ni idea de quiénes son Garikoitz y Agurtzane.

La mejor forma de decirle a `peso()` que calcule el peso de una persona es diciéndole quién es la persona.
Las funciones aceptan **parámetros de entrada**, que se pueden *pasar* a la función poniéndolos dentro de los 
paréntesis que se usan en la llamada.

{% highlight php %}
<?php

// nuestra función
function peso()
{
    $peso = 0;

    for ($i = 0; $i < strlen($nombre); $i++) {
        $peso = $peso + ord($nombre[$i]);
    }

    echo $nombre . ' pesa ' . $peso . ' kg.';
}

// primero Garikoitz
$nombre = "Garikoitz Subijana Lertxundi";
peso($nombre);

// y ahora Agurtzane
$nombre = "Agurtzane Mendikozelaia Agirrebeitia";
peso($nombre);

{% endhighlight %}

Peeeeeeero eso aún no arregla el programa. Cuando definimos la función, tenemos que especificar los parámetros que
acepta:

{% highlight php %}
<?php

// nuestra función
function peso($nombre)
{
    $peso = 0;

    for ($i = 0; $i < strlen($nombre); $i++) {
        $peso = $peso + ord($nombre[$i]);
    }

    echo $nombre . ' pesa ' . $peso . ' kg.';
}

// primero Garikoitz
$nombre = "Garikoitz Subijana Lertxundi";
peso($nombre);

// y ahora Agurtzane
$nombre = "Agurtzane Mendikozelaia Agirrebeitia";
peso($nombre);

{% endhighlight %}

Ten en cuenta que llamar a las variables de abajo `$nombre` y al parámetro de la función también `$nombre` no
es necesario. Lo que importa en realidad es el orden de los parámetros:

{% highlight php %}
<?php

// nuestra función
function f($primero, $segundo)
{
    echo $primero . ' ' . $segundo;
}

$mi_nombre = "Koldobika";
$mis_apellidos = "Guridi Elkorobarrutia";

f($mi_nombre, $mis_apellidos);
{% endhighlight %}

En este ejemplo, cuando llamamos a la función `f()` le pasamos el valor de `$mi_nombre` primero y el de
`$mis_apellidos` después. En la definición de la función hemos declarado dos argumentos, `$primero` y `$segundo`.
Cuando la función es llamada, el primer parámetro, `$primero`, recibe el valor de `$mi_nombre`, y el segundo parámetro,
`$segundo`, recibe el valor de `$mis_apellidos`.

Lo mismo ocurre con la funciópn `peso()` y el parámetro `$nombre`: cada vez que llamemos a `peso()`, su parámetro 
`$nombre` va a almacenar el valor de la variable `$nombre` que usamos en la llamada, va a ejecutar el bucle 
`for` usando ese valor, y va a imprimir el nombre de la persona y su peso:

## Valores de retonno

Estoy pensando que nuestra función `peso()`, a pesar de ser pequeña, hace demasiado: calcula el peso *y lo imprime*.
Es lógico pensar que no siempre vamos a querer imprimir el peso, o igual lo queremos imprimir de otra forma. Es 
muy importante limitar las responsabilidades de las funciones que creemos, porque las funciones que hacen muchas 
cosas tienen a  producir problemas más adelante, cuando nuestro programa evoluciona.

Si tenemos una función llamada `peso()`, probablemente queremos que calcule el peso y nada más. Ya nos encargamos
nosotros de imprimirlo, si es necesario. O podemos crear otra función que lo imprima, si vemos que estamos 
imprimiendo pesos continuamente, como los cárteles de la droga.

{% highlight php %}
<?php

// nuestra función
function peso($nombre)
{
    $peso = 0;

    for ($i = 0; $i < strlen($nombre); $i++) {
        $peso = $peso + ord($nombre[$i]);
    }

    return $peso;
}

// primero Garikoitz
$pesoDeGarikoitz = peso("Garikoitz Subijana Lertxundi");

// y ahora Agurtzane
$pesoDeAgurtzane = peso("Agurtzane Mendikozelaia Agirrebeitia");

{% endhighlight %}

Dentro de la función podemos usar el comando `return` para que la función devuelva un valor. A la hora de la llamada, 
podemos usar la función como si fuese un valor, y asignarlo a variables. Ahora tenemos el peso de ambas
personas en dos variables, y podemos imprimir ambos valores a nuestra manera:

> He eliminado, de paso, las variables `$nombre`, porque eran supérfluas.

{% highlight php %}
echo "Garikoitz pesa " . $pesoDeGarikoitz . " y Agurtzane pesa " . $pesoDeAgurtzane.
{% endhighlight %}

Jo, da gloria verlo.
