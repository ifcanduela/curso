---
title: 3. Tipos de datos
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

## Stringuificación

Para representar texto tenemos algo llamado *string*s. Cadenas de caracteres, 
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
var miNombre = "Juanito \"Animal\" Oiarzabal";
{% endhighlight %}

Muchos lenguajes permiten usar comillas simples también:

{% highlight python %}
miNombre = 'Talo con txistorra de la "güena"';
{% endhighlight %}

## Otros tipos de tipos de datos simples

El caso es que para hacer programas, necesitamos usar diferentes formas de
describir nuestros datos. No todo es un número entero. Por ejemplo, el Pagasarri tiene 673,1 metros
de alto. Por suerte quienquiera que inventase los lenguajes de programación de alto nivel pensó en
la orografía vasca largo y tendido, y decidió que además de los números enteros y las cadenas de texto,
los números decimales podrían ser muy útiles. Normalmente se llaman *float* o *double*, igual que los
enteros se llaman *int* y las cadenas de texto se llaman *string*.

## Con tipo y sin tipo

En la lección 2 definimos un entero usando Java:

{% highlight java %}
int doce = 12;
{% endhighlight %}

y luego otro en JavaScript así:

{% highlight js %}
trece = 12 + 1;
{% endhighlight %}

JavaScript no requiere que especifiquemos el tipo de datos de una variable. De hecho, la misma variable
puede almacenar diferentes tipos de datos en sucesión:

{% highlight js %}
trece = 12 + 1;
trece = 13.0;
trece = "XIII"
{% endhighlight %}

Cosas como esa no están permitidas en Java, porque en Java el tipo de una variable es * para siempre*. Y Java se encarga
de comprobar, cada vez que usas una variable, que la usas en el contexto adecuado. PHP te permite hacer esto:

{% highlight php %}
$el_numero_uno = 1;
$el_numero_doce = "12";
$el_numero_trece = $el_numero_uno + $el_numero_doce;
{% endhighlight %}

Y funciona, a pesar de que `$el_numero_doce` es un *string* y no un número. Eso es porque PHP es un poco
laxo con sus reglas. No pasa lo mismo en Java:

{% highlight java %}
int el_numero_uno = 1;
string el_numero_doce = "12";
int el_numero_trece = el_numero_uno + el_numero_doce;
{% endhighlight %}

Eso no va a funcionar, confía en mi que lo he probado. Vamos, lo probé una vez y no funcionó.

## Que sí y que no

A veces los números y las palabras sobran. Cuando te preguntan "¿A ganado el Athletic?", tú simplemente
mueves la cabeza de un lado a otro. "¿Quieres más marmitako?". Mueves la cabeza de arriba a abajo. El
mundo es más sencillo cuando puedes responder a todo con *bai* o *ez*. Los ordenadores, siendo de pocas
palabras de toda la vida, están optimizados para decir que sí y que no:

{% highlight java %}
bool haGanadoElAthletic = false;
bool quieresMasMarmitako = true;
{% endhighlight %}

El tipo de datos `bool` (booleano, a partir del apellido [un señor británico](http://es.wikipedia.org/wiki/George_Boole "George Boole"))
se usa para representar valores que sólo pueden tener dos estados: sí o no, apagado o
encendido, del Partido o no del Partido.

Los booleanos son importantes porque muchas operaciones en un programa dependen
de estados binarios, como comparaciones entre otros números. Los resultados de estas comparaciones suelen
ser *verdadero* o *falso*, y se representan con valores del tipo *bool*.

## Un txikiejemplo

Combinando variables, tipos de datos y operadores se pueden crear pequeños programas
que no cumplen ninguna función:

{% highlight js %}
var miNombre = "Igor";
var miEdad = 12;
var miAltura = 1.77;

var yo = "Me llamo " + miNombre + ", tengo " + miEdad + " años y mido " + miAltura;
{% endhighlight %}

Las primeras tres líneas definen tres variables distintas, `miNombre`, `miEdad` y `miAltura`. 
Usando el operador de asignación (`=`) *inicializamos* cada una de ellas con
valores apropiados; un *string*, un *int* y un *float*, respectivamente.

La última línea es diferente: creamos una nueva variable, `yo`, pero no le asignamos un valor directo. Puede ser un poco
difícil de leer, pero por suerte podemos dividirlo en líneas:

{% highlight js %}
var yo = "Me llamo " 
       + miNombre 
       + ", tengo " 
       + miEdad 
       + " años y mido " 
       + miAltura;
{% endhighlight %}

En este contexto, el operador `+` va a concatenar todos los trozos en un 
solo *string*. El resultado será `"Me llamo Igor, tengo 12 años y mido 1.77"`;

## Literalmente

Todos estos tipos de datos tienen cosas en común: cada variable almacena un solo valor de un solo tipo,
se pueden escribir fácilmente y hay operaciones con ellos que simplemente tienen sentido, como sumar dos
números enteros o unir dos cadenas de texto. Como en el mundo real, cuando encontramos algo en común entre
un montoncito grupo de cosas le ponemos una etiqueta. En este caso, a los enteros, los decimales, las cadenas
y los booleanos se les suele llamar *primitivas*. Son datos que no se pueden descomponer más, la parte
fundamental, indivisible de la información que los programas manejan.

> En *C/C++* en lugar de `string` se usa `char`, que representa un solo carácter, y muchos `char`s componen
un `string`, pero tanto JavaScript como PHP usan `string` como primitiva.

Los tipos de datos primitivos se pueden representar usando notación *literal*; eso significa que el valor *5* se
representa con un solo símbolo (el `5`), y el valor *Verdadero* se representa con un solo símbolo (`true`).
Cuando quieres una variable que almacena el nombre más bonito del mundo simplemente escribes
`string elNombreMasBonitoDelMundo = "Eguskine"`.

La existencia de tipos primitivos es una buena pista acerca de la existencia de...

## Tipos compuestos

Pocos de nuestros programas van a gestionar una lista de números decimales. Lo común es que queramos
representar algún concepto del mundo real, y esos conceptos suelen ser más complicados que un solo número.
Para representar estos elementos necesitamos agrupar datos en formas claras que nos ayuden a entender lo
que estamos haciendo. Por ejemplo, si queremos hacer un programa que gestione cocineros, podemos escribir esto:

{% highlight js %}
var cocinero_1_nombre = "Karlos Argiñano",
    cocinero_1_año_de_nacimiento = 1753,
    cocinero_1_alcohólico = true;

var cocinero_1_nombre = "Juan Mari Arzak",
    cocinero_1_año_de_nacimiento = 1942,
    cocinero_1_alcohólico = false;
{% endhighlight %}

Pero no es manejable, especialmente en Euskal Herria, donde cualquiera es un cocinero digno de la guía Michelin. Los tipos compuestos
son una solución práctica al problema:

{% highlight js %}
var cocineros = [
        {
            nombre: "Karlos Argiñano",
            año_de_nacimiento: 1753,
            lcohólico: true,
        },
        {
            nombre: "Juan Mari Arzak",
            año_de_nacimiento: 1942,
            alcohólico: false,
        },
    ];
{% endhighlight %}

Eso de ahí arriba es un trozo de JavaScript. La variable cocineros es un `array`, que es una forma técnica de decir * lista*, y esta lista contiene dos
elementos que a su vez son del tipo `object`. Los arrays se delimitan (en JavaScript) usando corchetes (`[` y `]`), y los objetos se delimitan con llaves
(`{` y `}`). La diferencia se ve más claramente aquí:


 al problema:

{% highlight js %}
var cocineros = [
        {
            nombre: "Karlos Argiñano",
            año_de_nacimiento: 1753,
            lcohólico: true,
        },
        {
            nombre: "Juan Mari Arzak",
            año_de_nacimiento: 1942,
            alcohólico: false,
        },
    ];
{% endhighlight %}

---

Probablemente haya más lecciones totalmente dedicadas a estructuras de datos en el futuro, porque son
importantillas, pero de momento esto es lo básico. Ahora vamos a aprender alguna sentencia de control de 
flujo para hacer las cosas interesantes.

<!--
## Palabras clave

Todos los lenguajes de programación<sup>1</sup> tienen algo llamado *palabras clave*. Son palabras
que significan algo especial para el lenguaje. Por ejemplo, cuando JavaScript ve la palabra clave
`function`, se prepara para leer la definición de un sub-programa. Cada lenguaje tiene diferentes
palabras clave

> <sup>1</sup>: Esto no es cierto. Por ejemplo Lisp no tiene palabras clave. Lisp es *raro*.
-->