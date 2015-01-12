---
title: Tipos de datos
layout: default
---

Hasta el momento nos hemos limitado a sumar números enteros. Es lógico representar
el número dos con el símbolo `2`, y el número 4317 con el símbolo `4317`. También
podemos usar números decimales, usando un punto (`.`) para separar la parte entera de
la parte decimal. Llegará un momento en el que quieras decir *Hola* al mundo, y para eso
no nos valen los números.

> Ha, eso es falso. Puedes escribir *Hola* haciendo esto:
{% highlight js %}
String.fromCharCode(72, 111, 108, 97);
{% endhighlight %}

## Strings

Para representar texto tenemos algo llamado *Strings*. Cadenas de caracteres, 
uno tras otro, que forman textos. A nivel técnico, todos los datos se almacenan 
como números, pero los lenguajes de programación son capaces de reconocer secuencias
de caracteres y realizar operaciones especiales con ellas. En la mayoría de lenguajes,
se pueden crear strings rodeando el texto con dobles comillas (`"`). Por ejemplo,
esto es JavaScript:

{% highlight js %}
var miNombre = "Ramón García";
{% endhighlight %}

Esto es Java:

{% highlight java %}
string miNombre = "Julen Guerrero";
{% endhighlight %}

Esto es PHP:

{% highlight java %}
$miNombre = "Iulian Iantzi";
{% endhighlight %}

Y esto es Ruby:

{% highlight ruby %}
miNombre = "Iñaki Perurena";
{% endhighlight %}

Las cosas de alrededor cambian, pero la forma de **representar los datos** es idéntica:
dobles comillas para indicar el inicio de una cadena, los datos, y otras dobles comillas para
indicar el fin de los datos. Muchos lenguajes también permiten insertar dobles comillas
en los datos usando un método llamado *secuencias de escapes*:

{% highlight js %}
var miNombre = "Juanito \"The Man\" Oiarzabal";
{% endhighlight %}

Muchos lenguajes permiten usar comillas simples también:

{% highlight python %}
miNombre = 'Talo con "txistorra"';
{% endhighlight %}

## Tipos de datos

El caso es que para hacer programas, necesitamos usar diferentes formas de
describir nuestros datos.

Todos los lenguajes de programación<sup>1</sup> tienen algo llamado *palabras claves*. Son palabras
que significan algo especial para el lenguaje. Por ejemplo, cuando JavaScript ve la palabra clave
`function`, se prepara para leer la definición de un sub-programa. Cada lenguaje tiene diferentes
palabras clave

> <sup>1</sup>: Esto no es cierto. Por ejemplo Lisp no tiene palabras claves. List es *raro*.
