---
title: Instalando PHP
layout: default
---

En este artículo voy a explicar, con los detalles necesarios, cómo instalar y configurar PHP
para programar un poquito. Doy por hecho que estás usando Windows y no sabes muy qué estás 
haciendo o porqué lo tienes que hacer.

Grosso modo, vamos a descargar PHP, configurarlo para poder usar el comando `php`, e instalar
una herramienta para gestionar las librerías, y montar un proyecto de prueba.

## Descargandi, paya

Navega hacia [la sección de descargas para Windows de PHP.net](http://windows.php.net/download/) y haz clic en 
el link que dice **Zip** debajo de VC11 x86 Thread Safe. La versión actual es PHP 5.6 (5.6.4), pero
descarga siempre la primera en la lista que cumpla estas condiciones.

- Es x86
- Es Thread safe
- Es Zip

Haz doble clic en el fichero ZIP cuando termine la descarga y extráelo a `C:\php`. Asegúrate 
de que hay un fichero `C:\php\php.exe`.

## Primera carrera

Abre el Panel de Control de Windows, y busca *Sistema y Seguridad*. Dentro de esa sección
hay otra llamada simplemente *Sistema*. Si entras verás una lista de opciones en la
columna de la izquierda. Haz clic en *Opciones avanzadas* para abrir un cuadro de 
diálogo y haz clic en el botón *Variables de Entorno* que hay abajo. Verás otro 
diálogo con dos listas. Busca una variable de nombre `PATH` en el cuadro de arriba,
haz doble clic en ella y añade `;C:\php` al final de su valor. Acepta todos los 
cuadros de diálogo que has abierto.

Ahora abre una línea de comandos. La forma más rápida de hacer esto es pulsando 
la combinación de teclas `Windows + R` en el teclado. Cuando la línea de comandos
aparezca, teclea `php -v` y pulsa `Enter`. Podrás leer algo como esto:

    $ php -v
    PHP 5.5.7 (cli) (built: Dec 11 2013 13:48:27)
    Copyright (c) 1997-2013 The PHP Group
    Zend Engine v2.5.0, Copyright (c) 1998-2013 Zend Technologies
        with Zend OPcache v7.0.3-dev, Copyright (c) 1999-2013, by Zend Technologies
        with Xdebug v2.2.3, Copyright (c) 2002-2013, by Derick Rethans

Un éxito abrumador.
