---
title: 5. Alternativas
layout: default
---

La sentencia `for` sirve para repetir comandos en secuencia, pero no siempre queremos repetir el comando. 
Un caso práctico sería la lista de socios del Athletic: queremos enviar un regalo a todos, excepto os que cumplan
una condición específica. Para eso tenemos la sentencia `if`, que nos permite bifurcar la ejecución del programa
en función de valores y condiciones:

{% highlight js %}
for (var i = 0; i < socios.length; i++) {
    var socio = socios[i];

    if (socio.esFanDeZiganda == true) {
        enviar_regalo(socio);
    }
}
{% endhighlight %}

## Un pájaro gordo en una rama

La forma más básica de escribir una sentencia alternativa es ésta:

{% highlight js %}
if (condición) {
    hacer_una_cosa()
}
{% endhighlight %}

En este ejemplo, `condición` es una *expresión*, lo que significa que es un trocito de código que
devuelve un solo valor. Por ejemplo, `2 + 2` es una expresión que devuelve `4`. Otra ejemplo de
expresión, más complejom es `(3 > 2) && is_valid(10)`. Ambos trozos de código pueden ser
reducidos a un solo valor, y se pueden usar como condiciones, pero es mejor limitarse a expresiones
que se reducen a *valores booleanos* (`true` y `false`).

{% highlight php %}
if (3 > 2) {
    echo "3 es mayor que 2.";
}
{% endhighlight %}

## Alternativas a las alternativas

¿Qué pasa cuando la condición no se cumple? El
bloque `if` es totalmente ignorado y la ejecución del programa continua como si nada. Sin embargo, 
podemos hacer que otro bloque de código se ejecute en el caso de que la condición no se cumpla,
añadiendo un bloque `else` tras el bloque `if`:

{% highlight php %}
if (3 > 2) {
    echo "3 es mayor que 2.";
} else {
    echo "3 no es mayor que 2.";
}
{% endhighlight %}

No hay mucho que explicar; la estructura `if (condición) then { do this} else { do that }` es muy 
común en todos los lenguajes de programación y resulta natural para la mayoría de la gente. Algunos
lenguajes la extienden, añadiendo opciones o cambiando palabras, pero es raro encontrar un lenguaje
que no tenga una sentencia if/else que no siga esta estructura.

## El Camino Se Divide Mil Veces Frente A Tus Pies

Es perfectamente posible tener una cadena de bloques `if/else` como la siguiente:

{% highlight php %}
if ($numero == 1) {
    echo "El número es 1.";
} elseif ($numero == 2) {
    echo "El número es 1.";
} elseif ($numero == 3) {
    echo "El número es 3.";
} elseif ($numero == 4) {
    echo "El número es 4.";
} elseif ($numero == 5) {
    echo "El número es 5.";
}
{% endhighlight %}

...pero no es práctico. Cuando nos encontramos con una situación como esa, en la que comparamos el mismo
valor (`$numero`) con una lista (`1`, `2`, `3`, etc...), podemos usar otro tipo de sentencia alternativa:

{% highlight php %}
switch ($numero) {
    case 1:
        echo "El número es 1.";
        break;
    case 1:
        echo "El número es 1.";
        break;
    case 3:
        echo "El número es 3.";
        break;
    case 4:
        echo "El número es 4.";
        break;
    case 5:
        echo "El número es 5.";
        break;
    default:
        echo "No sé qué número es...";
}
{% endhighlight %}

El código es más largo, pero representa una solución mejor al problema (desde un punto de vista 
semántico, al menos).

La sentencia `switch` no está disponible en todos los lenguajes (JavaScript, por ejemplo, no 
tiene `switch`), pero está lo bastante extendida como para resultar interesante.
