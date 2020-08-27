---
title: Git de Novato a experto
tags: [Git]
style: border
color: primary
description: Aprenderemos las bases de git para ir avanzando y profundizando en todos las opciones que nos ofrece esta herramienta para gestionar nuestro código y convertirnos en unos expertos!.
---

{% include elements/video.html id="z6NgqU8jEVI" %}


## ¿Qué es y por qué utilizar un manejador de versiones
----------

Seguramente, te has encontrado en la situación de tener 10 veces duplicada la carpeta del proyecto en el que estás trabajando y cada una de ellas llamada.
version-final, version-final1, version-final2 y así sucesivamente.

Sin usar un versionador o manejador de versiones, es normal que tengamos un proyecto desordenado y con pocas opciones para gestionarlo y mucho menos trabajar en equipo de manera simultanea. Usemos como ejemplo una página web, que ya está publicada, pero que el cliente quiere seguir haciendo cambios, desarrollando nuevas funcionalidades, módulos etc. Entonces, mientras nosotros trabajamos en esos cambios, supongamos que la página empieza a fallar o el cliente quiere hacer un cambio urgente.

Sin un manejador de versiones estariamos trabajando mas o menos de la siguiente manera:
Cómo en la carpeta donde estamos trabajando hay cambios que están en progreso y no están terminados, no podemos hacer la corrección ahí, por lo que vamos a tener que duplicar el proyecto base, hacer los cambios y subirlos y luego retomar nuestro desarrollo en la otra carpeta 2.0. pero si queremos ahora actualizar los cambios hechos en el proyecto base, tendremos que copiar los archivos modificarlos y pegarlos en el proyecto 2.0

Pero qué pasa si, nosotros habíamos hecho cambios en nuestra versión 2.0 de ese mismo archivo?

No podríamos solo sobreescribir el archivo porque los perderíamos.
Por lo que tendríamos que ir a la carpeta original, abrir el archivo y copiar el fragmento de código que queremos agregar para actualizar nuestro proyecto 2.0

Imagina tener que recordar todos los cambios que has ido haciendo y sumandole a esto, tener que trabajar con otras personas en el mismo proyecto y que cada uno esté desarrollando una funcionalidad específica.

Se volvería muy difícil y costoso el seguimiento y mantenimiento.

Por eso surgen los repositorios y manejadores de versiones.

Para gestionar nuestro proyecto y segmentar el desarrollo para su posterior combinación/fusión y control de cambios, ademas de la posibilidad de trabajar en equipo y poder revertir cambios en caso de que algo salga mal.

A esto se le puede añadir el control de roles y permisos para la gestión y manejo del código base.

Pero mantengamos esto, simple y empecemos por partes, vamos allá!


---------------

## Instalación:

Lo primero es instalar un manejador de versiones, para este tutorial, estaremos usando Git, que es el más famoso del mercado, pero existen diferentes en el mercado cómo:
- git
- mercurial
- Svn

#### Les dejo el link para su descarga:

- Windows
[Descargar](https://git-scm.com/downloads)

- Mac
[Descargar](https://sourceforge.net/projects/git-osx-installer/files/)

desde la terminal ejecutando

```terminal
$ brew install git
```

#### Linux: Desde la terminal

```terminal
$ sudo apt-get install git
```

En el caso de Linux, este sería el comando para instalarlo desde la terminal, aunque ya viene instalado por defecto en muchas distribuciones como Ubuntu. También está disponible desde la tienda de software de Ubuntu.

------------

## Iniciar el manejador en el proyecto

Git es una herramienta hecha principalmente para usar vía terminal/consola/cmd. Pero con el pasar de los años se desarrollaron muchas aplicaciones e interfaces para facilitar la interacción en el día a día.

Al día de hoy se encuentra integrado a la mayoría de editores de código, con una interfaz gráfica sencilla e intuitiva.

**Pero en este tutorial aprenderemos las bases con comandos.**

Lo primero es activar o iniciar el git en nuestro proyecto, para eso vamos a la ruta donde se encuentra nuestro proyecto y en la carpeta base ejecutamos el comando.
```terminal
$ git init
```

Listo, con esto Git creará una carpeta .Git
Oculta y empezará a hacer magia.

El siguiente comando será:

```terminal
$ git status
```

Con esto nos mostrará todos los archivos y carpetas de nuestro proyecto que Git detectó para empezar a hacer tracking o seguimiento.

Por el momento síganme y ejecuten los siguientes comandos.

Más adelante les explicaré que hace cada uno.
```terminal
$ git add .
$ git commit -m "proyecto base"
```

**Listo! hicimos nuestro primer commit, Wujuuu!! ¡Esto tenemos que celebrarlo!**

Entonces ahora expliquemos en detalle cada uno de los comandos anteriores.

Empecemos con el

```terminal
$ git add <file>
```
y si queremos agregar todos los archivos

```terminal
$ git add .
```
el punto indica que se agreguen todos!

Cabe destacar en la linea de comandos no es necesario colocar el simbolo $, el uso de <esto> es para indicar que es una variable que sera reemplaza por la ruta y nombre de archivo, los <> no son necesarios, cuando ejecutes tu comando en la terminal.

Entonces.
El comando git add, nos permite agregar archivos a nuestra area de preparacion.
en ingles: Staging Area.

Esto trae 2 nuevos elementos a la mesa:

Staged area
Unstaged area

para ver el estado de donde se encuentran nuestros archivos ubicados usaremos el siguiente comando.

```terminal
$ git status
```

Esto nos mostrará, nuestros archivos y su ubicacion en las areas antes mencionadas.
las que estan en unstaged ( por default ) los muestra en rojo y los que están en Staged  las mostrara en verde.

para entender mejor esto, todos los archivos que sumemos al area de preparacion:
staged changes. van a ser tomados en cuenta para cuando hagamos un commit.
Es decir, para cuando queramos tomar una foto del estado del proyecto, estos elementos son los que van a ser guardados y mostrados en esa foto.

Supongamos un set de grabación, todo lo que está en escena, es lo que va a mostrarse al espectador.

Esa es nuestra area de preparacion ( staged )

y lo que está en el backstage es lo que estaría en unstaged, lo que no se muestra en escena.

la creación de esta escena o fotografía ( marcador en la línea de tiempo de nuestro proyecto ) se crea usando el comando.

```terminal
$ git commit -m “ un mensaje descriptivo de los cambios que se hicieron para esta escena”
```

Seguramente vas a estar interactuando con diferentes archivos y moviendolos entre un area a otra.

Si ya hiciste un git add, pero luego te das cuenta que ese archivo no quieres que quede en el siguiente commit.

para sacarlo del staged área el comando seria:

```terminal
$ git reset HEAD <file>
```

y si queremos sacar todos los archivos del staged ared

```terminal
$ git reset
```

Estos serían todos los comandos básicos para manejar un flujo inicial de git.

¡Felicidades! ¡Ya estás empezando a utilizar una maravillosa herramienta!

Continuaremos con conceptos más avanzados próximamente….
