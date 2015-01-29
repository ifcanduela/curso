---
title: 4. Control de flujo
layout: default
---

<div style="background-color: #900; text-align: center; width: 100%; padding: 40px; color: white; font-weight: bold; text-align-enter; font-family: monospace">(>'.')>&nbsp;&nbsp;&nbsp;flow&nbsp;&nbsp;&nbsp;<('.'<)</div>

Vamos a programar de verdad. Creo que lo mejor va a ser que escriba un trozo de código y lo explique línea 
por línea.

Puedes usar [esta app](http://codepad.viper-7.com/) para escribir PHP y ejecutar el programa haciendo clic 
en el botón **Paste**.

{% highlight php %}
<?php

$nombreDeLaPersona = "Garikoitz Subijana Lertxundi";
$pesoTotal = 0;

for ($i = 0; $i < strlen($nombreDeLaPersona); $i++) {
    $pesoTotal = $pesoTotal + ord($nombreDeLaPersona[$i]);
}

echo $nombreDeLaPersona . ' pesa ' . $pesoTotal . ' kg.';

{% endhighlight %}

Esto es una versión simplificada de aquel ejemplo de la [lección 1](/curso/lecciones/1/), ahora en PHP en lugar de JavaScript. Hay un montón de cosas que ver.

## Códigos!

Los programas en PHP empiezan con `<?php`. Nada más. Normalmente es el único texto en la primera línea.

## Variables!

El programa comienza **declarando** dos variables, `nombreDeLaPersona` y `pesoTotal`. En PHP las variables
llevan un `$` delante del nombre. En este caso también **inicializamos** las variables, usando el operador
de asignación. Cada línea termina con un punto y coma (`;`), que se usa para terminar *sentencias*.

PHP no requiere (*no permite*, en realidad) especificar el tipo de las variables al definirlas. Escribimos 
el nombre la la variable y su valor y el intérprete (un programa llamado `php.exe`) se encarga de llevar 
la cuenta de qué tipo tiene una variable. Esta estrategia se llama **duck typing**, porque si camina como
un pato, suena como un pato y parece un pato, probablemente sea un pato (esto va totalmente en serio, es [una
cosa que existe en el mundo real](http://en.wikipedia.org/wiki/Duck_typing)).

## Bucles!

Éste es nuestro primer bucle. Los bucles son estructuras de código que nos permiten repetir una serie de acciones
un número de veces. Normalmente cada paso del bucle (cada *iteración*) realiza la misma acción con una lista de
elementos. A veces es difícil ver cuál es la lista de elementos. En nuestro caso es la lista de letras en el
nombre de la persona.

Vamos a usar un bucle `for`, que nos permite especificar un elemento de inicio, cambiarlo en cada iteración 
y comprobar tras cada iteración si la siguiente iteración debe tener lugar. La variable `$i` es inicializada a `0`,
como valor de inicio del bucle. Esta variable se suele llamar *variable de control*. La parte del bucle que va
dentro de los paréntesis suele usarse para inicializar, comprobar y modificar la variable de control, en 
tres secciones.

### Inicialización

{% highlight php %}
$i = 0;
{% endhighlight %}

La primera sección inicializa la variable de control a `0`, es sencillo cual deporte rural.

### Control

{% highlight php %}
$i < strlen($nombreDeLaPersona)
{% endhighlight %}

Uh, esto es nuevo. La segunda sección contiene una **condición**. La condición se comprueba al inicio de cada 
iteración del bucle. Si la condición es *verdadera*, la iteración del bucle se ejecuta. Si la condición es 
*falsa*, la iteración no se ejecuta y el bucle termina.

Nuestra  condición, en palabras, es *"si el valor de la variable `$i` es menor que la longitud de la cadena `$nombreDeLaPersona`"*. La parte `strlen()` es una *llamada a función*, en concreto a la 
función `strlen` o *string length*, 
que se encarga de contar el número de letras, números y signos en una cadena, y devuelve ese número. Es equivalente
a `28`, porque la cadena `"Garikoitz Subijana Lertxundi"` tiene 26 letras y 2 espacios. La condición es, por lo tanto,
*"si el valor de la variable `$i` es menor que 28"*. En la primera iteración del bucle `$i` tiene valor `0`, así 
que el código dentro del bucle `for` va a ejecutarse.

### Modificación

{% highlight php %}
$i++
{% endhighlight %}

La tercera sección que tenemos que escribir al usar un bucle `for` es la de modificación. El comando de modificación 
se ejecuta al final de cada iteración. En nuestro estamos recorriendo cada letra del nombre, empezando desde 0, 
y para cada siguiente iteración queremos queremos que la variable se incremente en 1. La manera más tradicional 
y sencilla de hacerlo es usando el **operador de post-incremento**, `++`, que suma 1 al valor de una variable. 
Para entender mejor lo que está pasando, ten en cuenta que estas dos líneas hacen lo mismo:

{% highlight php %}
$i++;           // usando el operador de post-incremento
$i = $i + 1;    // usando una suma y una asignación
{% endhighlight %}

El bucle se va a ejecutar 28 veces, empezando con `$i` igual a `0` y terminando con `$i` igual a `27`.

## Funciones!

Dentro del bucle tenemos sólo una línea de código, pero da mucho juego:

{% highlight php %}
    $pesoTotal = $pesoTotal + ord($nombreDeLaPersona[$i]);
{% endhighlight %}

Esta línea asigna a la variable `$pesoTotal` la suma del valor actual de `$valorActual` y el resultado de 
la *llamada a función* `ord` con el parámetro `$nombreDeLaPersona[$i]`.

Sabemos que `$nombreDeLaPersona` es una cadena de texto y que `$i` es un número entero entre 0 y 27, que cambia
en cada iteración del bucle. Sólo nos queda saber qué es eso de `[$i]`, ¿no? ¿Te acuerdas cuando tus padres te 
daban una hostia en la mano y decían muy bajito "¡No señales!"? Pues esto es señalar. Estamos diciendo, más
o menos, *"dame esa letra"*, la que está en `$i`. Las cadenas tienen letras y símbolos que se pueden acceder de
uno en uno, empezando por el primero, que tiene el índice `0`, hasta el último, cuyo índice es igual a la longitud 
de la cadena menos 1.

Así que estamos llamado a `ord` con una letra. En la primera iteración del bucle `$i` es `0`, así que 
`$nombreDeLaPersona[$i]` es `$nombreDeLaPersona[0]`, que a su vez significa *el carácter en la posición 0* de 
la cadena `Garikoitz Subijana Lertxundi`: `ord("G")`. La función `ord` convierte una letra en su código ASCII, y
devuelve el código en la forma de un número entero.

> Puedes [leer más en el manual online de PHP](http://www.php.net/ord).

Según [la tabla ASCII](http://en.wikipedia.org/wiki/ASCII#ASCII_printable_code_chart), el código de la letra `G` es `71`. 

Ya casi Hemos resuelto la línea. Ahora mismo tiene este aspecto:

{% highlight php %}
    $pesoTotal = $pesoTotal + 71;
{% endhighlight %}

Sólo nos queda sumar `71` a `$pesoTotal`, y poner el resultado en `$pesoTotal` de nuevo. Habíamos inicializado
`$pesoTotal` con un `0`, lo que significa que el nuevo valor de `$pesoTotal` va a ser 71.

### La siguiente iteración

Cuando la iteración termine `$i` será incrementada en 1. Valía `0`, ahora vale `1`. Es menor que 28, así 
que la siguiente iteración se va a ejecutar. `$nombreDeLaPersona[1]` se convierte en `a`, y según la tabla ASCII
la `a` minúscula vale 97. Si sumamos 97 al anterior valor de `$pesoTotal` (`71`), obtenemos `168`. Tras la 
segunda iteración del bucle el peso total de Garikoitz ha subido a 168, y todavía quedan un montón de letras.

## Datos de salida!

Cuando el bucle termine, tras 28 iteraciones, el valor de `$pesoTotal` será el equivalente a sumar los códigos ASCII
de todas las letras del nombre de Garikoitz, incluidos los dos espacios: 2478. Sólo nos queda imprimirlo en pantalla.
Eso es muy fácil en PHP, tenemos que usar el comando `echo` (se pronuncia *eco*):

{% highlight php %}
echo $nombreDeLaPersona . ' pesa ' . $pesoTotal . ' kg.';
{% endhighlight %}

`echo` pone lo que viene a continuación en algo llamado *output stream*. Cuando hacemos páginas web con PHP 
el *output stream* suele ser un fichero HTML, y cuando ejecutamos PHP en la línea de comandos el *output stream*
es la propia línea de comandos.

Si te fijas, separamos los diferentes trozos que queremos imprimir con puntos (`.`). En PHP, para unir cadenas
de texto tenemos que usar el punto, no el signo `+`. El resultado de este comando `echo` será:

    Garikoitz Subijana Lertxundi pesa 2478 kg.

Y con eso termina el programa, de momento. Lo siguiente es el `if`.


