---
title: Git de Novato a experto
tags: [Git]
style: border
color: primary
description: Aprenderemos las bases de git para ir avanzando y profundizando en todos las opciones que nos ofrece esta herramienta para gestionar nuestro código y convertirnos en unos expertos!.
---

{% include elements/figure.html image="https://cdn-images-1.medium.com/max/1000/0*MAeS-4fEc0Y7T4VB.jpg" caption="iOS" %}

## ¿Qué es y por qué utilizar un manejador de versiones
----------

Seguramente, te has encontrado en la situación de tener 10 veces duplicada la carpeta del proyecto en el que estás trabajando y cada una de ellas llamada.
version-final, version-final1, version-final2 y así sucesivamente.

Sin usar un versionador o manejador de versiones, es normal que tengamos un proyecto en un cliente, por ejemplo una página web, que ya está funcionando, pero que el cliente quiere seguir desarrollando nuevas funcionalidades, módulos etc. Que mientras nosotros trabajamos en esos cambios, supongamos que la página que está al aire, está fallando o el cliente quiere hacer un cambio urgente.

Cómo en la carpeta donde estamos trabajando hay cambios que están en progreso y no están terminados, no podemos hacer la corrección ahí, por lo que vamos a tener que duplicar el proyecto base, hacer los cambios y subirlos y luego retomar nuestro desarrollo en la otra carpeta 2.0. pero si queremos ahora actualizar los cambios hechos en el proyecto base, tendremos que copiar los archivos modificarlos y pegarlos en el proyecto 2.0

Pero qué pasa si, nosotros habíamos hecho cambios en nuestra versión 2.0 de ese mismo archivo?

No podríamos solo sobreescribir el archivo porque los perderíamos.
Por lo que tendríamos que ir a la carpeta original, abrir el archivo y copiar el fragmento de código que queremos agregar para actualizar nuestro proyecto 2.0

Imagina tener que recordar todos los cambios que has ido haciendo y súmale a esto tener que trabajar con otras personas en el mismo proyecto y que cada uno esté desarrollando una funcionalidad específica.

Se volvería muy difícil y costoso el seguimiento y mantenimiento.

Por eso surgen los repositorios y manejadores de versiones.

Para centralizar el código y segmentar el desarrollo para su posterior combinación/fusión y control de cambios.

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

#### Continuara...
