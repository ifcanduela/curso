---
title: Objetos y Clases
layout: default
---

Cuando los programas crecen es fácil perderse en ellos: muchas líneas de 
código de aspecto similar, variables con nombres simples y genéricos,
poco contexto del que obtener significado. Cuando un programa alcanza
un tamaño difícil de mantener se pueden usar distintas técnicas para
mantener el código fuente abjo control. Una de ellas es la creación de abstracciones
para nuestros datos, que nos permiten agrupar datos en colecciones lógicas y
aplicar operaciones en estas colecciones, de tal manera que cada colección sea
autosuficiente y reutilizable.

La manera más extendida de crear abstracciones es a través del paradigma de orientación
a objetos. Es un campo muy extenso que no vamos a explorar en profundidad, pero
el uso básico de objetos puede ayudar mucho a organizar el código fuente de un
programa.

## Abstractificarlo Todo

Diferentes lenguajes de programación tienen diferentes ideas de cómo definir y crear
objetos, pero la más extendida fue popularizada por C++ en los años 80: unas estructuras
especiales, llamadas **clases**, describen tipos de objetos. El programa puede tomar estas
*clases* y crear objetos a partir de ellas. Por ejemplo, una abstracción del concepto
de "Persona" en nuestro programa podría parecerse a esto:

{% highlight php %}
class Persona
{
    public $nombre;
    public $rh = false;
}
{% endhighlight %}

La palabra clave `class` marca la definición de una clase. Dentro de una clase podemos
definir muchas otras cosas que *componen* la clase, como el nombre de una persona o el
color de una txapela. En nuestro caso estamos usando la palabra clave `public` para 
definir dos **propiedades**, que son variables propias de la clase, pero también podemos 
definir funciones dentro de una clase, llamadas habitualmente **métodos**. Definir 
propiedades y métodos dentro de una clase es muy parecido a hacerlo fuera.
Una vez definida, la clase `Persona` se puede usar de esta manera:

{% highlight php %}
$anneIgartiburu = new Persona();
$anneIgartiburu->nombre = 'Anne Igartiburu';
{% endhighlight %}

Hay un par de cosas muy nuevas en ese bloque de código. La primera es la palabra clave `new`, que
nos permite usar una clase para crear un objeto. La segunda, el operador `->`, nos permite acceder 
a propiedades y métodos definidos dentro de la clase, como el nombre, en este caso.

## Métodos y Métodos

Sí, he escrito *métodos* dos veces en la cabecera. No se me ocurría nada mejor. Como he dicho
antes, un *método* es una función definida dentro de una clase. Cuando una función
se define de ese modo, obtiene mágicamente una serie de habilidades que la hacen diferente
de las funciones normales. La primera es que no está disponible para todo el mundo:

{% highlight php %}
class Persona
{
    public $nombre;
    public $rh = false;

    function peso()
    {

    }
}

peso(); // error!
{% endhighlight %}

Si intentamos llamar a la función `peso()` de esta forma obtendremos un error. `peso()` sólo
se puede invocar a través de un objeto de la clase *Persona*:

{% highlight php %}
$anneIgartiburu = new Persona();

$anneIgartiburu->nombre = 'Anne Igartiburu';
$anneIgartiburu->peso();
{% endhighlight %}

Esta forma de llamar a una función es característica de los lenguajes orientados a objetos,
y en algunos contextos se llama *paso de mensajes*. Es más o menos equivalente a esto:

{% highlight php %}
Persona_peso($anneIgartiburu);
{% endhighlight %}

Pero tiene propiedades especiales, como por ejemplo la imposición de que `$persona` tiene
que ser del tipo `class Persona`. El uso de `->` es simplemente una forma sencilla de indicar que
estamos llamando a `peso()` usando `$persona`.

## Mi propio peso

Al contrario que cuando usábamos la función `peso()` en lecciones anteriores, con nuestro nuevo
*método* no necesitamos especificar un nombre para calcular el peso, porque el objeto ($anneIgartiburu, en
este ejemplo), tiene una propiedad llamada `$nombre` que podemos usar dentro del método `peso()`.

{% highlight php %}
class Persona
{
    public $nombre;
    public $rh = false;

    function peso()
    {
        $pesoTotal = 0;
        $longitudDelNombre = strlen($this->nombre)

        for ($i = 0; $i < $longitudDelNombre; $i++) {
            $pesoTotal += ord($this->nombre[$i]);
        }

        return $pesoTotal;
    }
}
{% endhighlight %}

Podemos acceder a las propiedades (y métodos) de un objeto dentro de los métodos definidos por su clase
usando la variable mágica `$this`. Así es como accedemos a la propiedad `$nombre`, primero para contar el número de
caracteres que tiene y después para acceder a uno de ellos usando un índice.

> ¿Recuerdas que en PHP debemos usar un `$` antes del nombre de una variable? Cuando accedemos a una propiedad **no**
> podemos usar el signo de dólar. Usar el `$` en esa situación tiene otro significado que es mejor no descubrir.

La variable `$this` sólo se puede usar dentro de los métodos de una clase, y siempre tiene el valor de la variable
que hemos usado para llamar al método. En el caso de `$anneIgartiburu->peso()`, `$this` tiene el mismo valor que
`$anneIgartiburu`, y por lo tanto `$this->nombre` tiene el mismo valor que `$anneIgartiburu->nombre`, y hemos asignado
`"Anne Igartiburu"` a esa propiedad anteriormente. Voy a dejar de escribir *Anne Igartiburu* porque no 
quiero aparecer en las búsquedas de Google.

Si quisiéramos calcular otro peso deberíamos crear otra variable de la clase *Persona*, como en este ejemplo:

{% highlight php %}
$ilaskiSerrano = new Persona();

$ilaskiSerrano->nombre = "Ilaski Serrano";

echo $ilaskiSerrano->nombre . " pesa " . $ilaskiSerrano->peso() . " kilos.";

{% endhighlight %}

