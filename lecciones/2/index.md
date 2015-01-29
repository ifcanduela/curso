---
title: 2. Variables y números
layout: default
---

Vamos a empezar a programar con los primero elementos de la sintaxis de un lenguaje de programación: 
operadores e identificadores. Palabras raras como esas van a ser el pan de cada día, así que cuanto 
antes nos familiaricemos con ellas, mejor. En esta lección veremos cómo se escribe un programa sencillo que
usa operaciones matemáticas sencillas para calcular valores. El programa en sí es inútil; nadie
va a usar JavaScript para hacer cálculos sencillos, pero como ejemplo ilustrativo va a ser muy útil.

> Es muy recomendable terminar la primera lección del curso de JavaScript de CodeCademy antes de leer 
> esta lección. un montón de texto no es la mejor manera de aprender a programar, por muchos ejemplos
> que tenga. Este texto va a ser más fácil de entender después de hacer algunos ejemplos prácticos, y va a
> ayudar (en teoría) a dar una forma más concreta a las muchas de las cosas que se hacen en COdeCademy.

## Preparativos

Vamos a escribir algo de *código fuente*, pero ¿dónde? Usaremos una aplicación web llamada 
[JsFiddle](http://jsfiddle.net/) para escribir JavaScript, y veremos los resultados en el 
mismo navegador, abriendo las **herramientas de desarrollo** con la tecla `F12` y seleccionando
*Console* (o la variedad regional apropiada, como *Konsola* en Euskal Herria o *הסוגר* en Israel &mdash; no
estoy 100% seguro de este último).

Aquí hay un ejemplo de un programa creado en **JsFiddle** con el resultado en la consola de Google Chrome:

[![Has clic para agrandizar]({{ site.baseurl }}/images/2-chrome-console.png)]({{ site.baseurl }}/images/2-chrome-console.png "Has clic para agrandizar")

Y el mismo programa, ejecutado desde Mozilla Firefox:

[![Has clic para agrandizar]({{ site.baseurl }}/images/2-firefox-console.png)]({{ site.baseurl }}/images/2-firefox-console.png "Has clic para agrandizar")

Iré explicando qué hacer y qué botones pulsar cuando llegue el momento, así que vamos a calmarnos, 
poner un poco de música y empezar.

> Este es un buen momento para visitar el aseo, porque lo que viene
a continuación es difícil que te cagas.

<script>
    var nombre = "Sabin Arana ta Goiri";
</script>

Suponiendo que Firefox o Chrome está abierto y estás leyendo esta página, haz lo siguiente:

1. Pulsa la tecla `F12` de tu teclado.
2. En el panel que ha aparecido en pantalla, busca la palabra *Console* (o la traducción correspondiente) y haz clic en ella para cambiar al modo de consola interactiva. 
3. Asegúrate de que hay un cursor parpadeando en pantalla y teclea `nombre`.
4. Pulsa la tecla `Enter` de tu teclado.

El resultado de seguir esos pasos es que el navegador te responde con el nombre de alguien importante. Ey, eso tiene que ser un programa, ¿no? Sí. Sí, pero lo importante es que este proceso es el que vamos a seguir
para aprender algunas cosas acerca de la sintaxis de JavaScript.

## Nuestro primer programa es... decepcionante

Teclear `nombre` y pulsar enter no se puede considerar un gran paso adelante; tendremos que hacer algo distinto, pero primero algo de teoría.

JavaScript puede hacer cálculos matemáticos muy complicados. Todos los lenguajes de programación son,
en esencia, calculadoras muy complicadas. En la Casio que tenías en la ikastola escribías un número,
después un signo de suma, resta, multiplicación o división, y otro número. Al pulsar el botoncillo
de `=`, el resultado aparecía en pantalla. JavaScript puede hacer lo mismo: si en lugar de teclear
`nombre` y pulsar `Enter`, tecleas `2+2` y pulsas `Enter`, verás que el navegador te responde con el
resultado (es `4`). Chrome (o Firefox) le ha pasado nuestro primer programa (`2+2`) al intérprete de 
JavaScript, que lo ha procesado, lo ha dividido en sus partes constituyentes, las ha transformado y
se las ha devuelto al navegador. Y ¿cuáles son esas partes constituyentes?

## Números y operadores

Nuestro primer programa se componía de 3 *símbolos*

1. Un número entero, el `2`,
2. un signo `+`, y
3. otro número entero, igualito al primero.

En términos de programación, esos números se llaman *valores literales*, y representan datos que se pueden
escribir de manera sencilla. Son muy útiles para representar números, como el 2 o el 3.1415. Casi todos los
lenguajes de programación nos dejan representar números igual que los representamos con papel y boli o
en una calculadora.

El signo `+` es un elemento de la sintaxis de JavaScript &mdash; algo que el lenguaje de programación simplemente *entiende*. En este caso, cuando JavaScript ve un signo `+` entre dos números, simplemente suma
los números. No es adecuado decir que el signo `+` es un signo *"más"*, porque no sólo sirve para sumar. JavaScript es capaz de usar el signo `+` entre dos elementos que no son números, y es posible que el resultado sea totalmente válido. En la sintaxis de JavaScript, el signo `+` significa diferentes cosas
en función del contexto. Hay más signos como `+`, y se llaman **operadores**. La cantidad de ellos puede ser un poco abrumadora:

~~~
= + - * / %
+= -= *= /= ++ --
== != === !== > >= < <=
& | ^ ~ && || << >> !
? : ' " . , ; ( ) []
~~~

Si te fijas, muchos de ellos son signos de puntuación; los operadores en un lenguaje de programación tienen
un papel similar, porque suelen aparecer separando los demás elementos sintácticos del lenguaje.

## Este número me lo quedo

Seguro que recuerdas la gloriosa aparición de nuestro líder espiritual hace unos minutos, cuando invocamos su
`nombre` en la consola del navegador. Al escribir `nombre` y pulsar Enter, JavaScript se pregunta si la 
palabra *nombre* tiene algún significado. Normalmente no lo tiene, porque no hay nada definido en JavaScript
con ese nombre. La palabra `nombre` es algo que he definido yo en esta página. Palabras como esta,
creadas por el programador, se llaman **variables**, y se usan para guardar números u otros valores y poder
usarlos en otras partes del programa. Teclea `numero = 2` en la consola del navegador y pulsa `Enter`. 
Si a continuación tecleas `numero`, el navegador imprimirá `2`, porque JavaScript ha creado una palabra
llamada `numero` y le ha asignado el valor del número entero `2`. Así, sin darle mucha importancia, 
acabo de introducir un nuevo operador: el *operador de asignación*, `=`.

Podemos ver estas palabras creadas por el programador como etiquetas. Si calculamos un número sumando
otros dos números, y tenemos pensado usar el nuevo número, es muy útil poderlo usar con un nombre especial.

> Alerta: ejemplo estúpido en camino.

Si vamos a usar el resultado de sumar 2 más 2 a menudo, lo lógico será que almacenemos ese resultado en 
algún sitio. Al fin y al cabo, no queremos estar calculándolo una y otra vez. Por eso podemos hacer algo como
`cuatro = 2 + 2`, y en el futuro la palabra `cuatro` significará lo mismo que `2 + 2`.

Normalmente las variables se usan en lugar de valores calculados, y por
eso es necesario *definirlas* (asignarles un valor) previamente. Algunos lenguages (como C o Java) requieren que las variables tengan un *tipo*:

{% highlight java %}
int doce = 12;
{% endhighlight  %}

En realidad, las variables siempre tienen un tipo. Lenguajes como
JavaScript o PHP son capaces de detectar el tipo de una variable a
partir del tipo de los datos que asignamos:

{% highlight js %}
trece = 12 + 1;
{% endhighlight  %}

En JavaScript, una variable creada como `trece` en el ejemplo anterior
tendrá un tipo `Number`, que hace que se comporte como un número. Más 
información acerca de tipos de datos en la próxima lección.

---

En el próximo episodio vamos a hacer algo más que sumar números.
