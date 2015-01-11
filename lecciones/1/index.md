---
title: 1. Introducción
layout: default
---

Un ordenador puede hacer muchas cosas, y eso es bastante útil. Lo malo es
que las puede hacer de muchas maneras distintas; es malo para los programadores
de ordenadores, que tienen que conocer muchas formas de hacer todas esas, 
experimentar con la mayoría, y elegir la más adecuada.

Hay lenguajes de programación para todo, y 
[algunos son bastante especiales](http://esoteric.sange.fi/brainfuck/bf-source/prog/99botles.bf).
En este curso nos vamos a centrar en una serie de lenguajes de programación conocidos
como *La familia de C*. Se llaman así porque heredan la sintaxis del lenguaje de 
programación C, creado en los años setenta por tres personas con barba.

Hablando de sintaxis, la sintaxis de un lenguaje de programación es una serie de 
reglas que describen (y limitan) las *palabras* que componen el lenguaje y cómo se
deben combinar para crear programas. Es como el euskera, con la fundamental diferencia de
que si rompes las reglas de un lenguaje de programación, nadie te va a entender. Cada lenguaje
tiene una sintaxis diferente, pero todos los lenguajes de la familia de C siguen unas 
reglas sintácticas muy similares, y dado que son los lenguajes más extendidos, la mayoría de 
la gente aprende a programar con uno de estos lenguajes.

Los programas de ordenador se escriben en texto plano. Por ejemplo, esto es un programa:

{% highlight js %}
//! La funcion pesar() calcula el peso de una persona usando un método
//! científicamente probado.
//! 
//! @param nombre [string] Nombre de la pesona a pesar
//! @return int Peso de la persona
function pesar(nombre)
{
    // inicializamos el peso a 0
    var pesoTotal = 0;
    
    // un bucle que recorre el nombre letra a letra
    for (var i = 0; i < nombre.length; i++) {
        // obtenemos el código ASCII de la letra y lo añadimos al peso total
        pesoTotal += nombre.charCodeAt(i);
    }
    
    // devolvemos el peso total
    return pesoTotal;    
}

var nombreDeLaPersona = prompt("¿A quién queres pesar?");
var pesoDeLaPersona = pesar(nombreDeLaPersona);

console.log("El peso de " + nombreDeLaPersona * " es " + pesoDeLaPersona " kgs.");
{% endhighlight %}

Ese programa se podría ejecutar en el mismo navegador que usas para leer
esta página. Lo que el navegador hace con ese texto es demasiado complicado como
para explicarlo, y se puede decir que es irrelevante: el resultado es un programa
que pide un nombre e imprime un número. Cuando te piden que levantes una piedra no
preguntas cómo: simplemente coges la piedra más grande que ves y la levantas. Un 
programa hace lo mismo.

Es un ejemplo sencillo, pero demuestra la parte más fundamental de un programa: su 
resultado depende de los datos que le demos. Los datos pueden venir de muchos 
orígenes diferentes, incluidos el reloj del sistema operativo, un fichero de nuestro
disco duro, un servidor de internet o el avance del tiempo de Ana Urrutia. El programa 
almacena los datos en *memoria* (un sitio especial dentro del ordenador) y los usa 
cuando le conviene.

---

Ya estamos preparados para el primer contacto con el vertiginoso mundo de los 
números enteros positivos!
