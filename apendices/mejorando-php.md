---
title: Mejorando PHP
layout: default
---

## Librerías

> Este paso es opcional, pero si vas a trabajar con PHP es muy recomendable.

Vamos a instalar **Composer**, el estándar para la gestión de dependencias en PHP.
Composer es un programa escrito en PHP y distribuido en un solo archivo.

Descarga [este archivo](https://getcomposer.org/composer.phar) y guárdalo en 
`C:\php`, de manera que su nobre completo es `C:\php\composer.phar`.

En la línea de comandos, teclea `php composer.phar about`. Si ves un texto similar a
este...

    $ php composer.phar about
    Composer - Package Management for PHP
    Composer is a dependency manager tracking local dependencies of your projects and libraries.
    See http://getcomposer.org/ for more information.

...ponte otra medallita.

Yo normalmente creo un fichero `C:\php\composer.bat` para usar Composer simplemente con el 
comando `composer`. Puedes crear un fichero `composer.txt`, pegar el texto de abajo, guardar 
el fichero y cambiarle la extensión después.

    @echo off
    php %~dp0\composer.phar %*

## Pruebas en línea de comandos

Vamos a instalar un tipo de programa llamado *REPL*. REPL son unas siglas que significan 
*Read, Evaluate, Print and Loop*; es un programa de línea de comandos que lee comandos en PHP, 
las evalúa, imprime el resultado y vuelve a empezar. Es muy útil para averiguar el resultado de expresiones o para ejecutar código de forma aislada.
