---
title: Cómo reescribir el historial en GIT 👽👽
tags: [Git, Tutoriales]
style: border
color: primary
description: Una de las reescrituras históricas más simples que podemos hacer con git es cambiar el último mensaje de confirmación.
---

{% include elements/video.html id="eHIsHiaddwk" %}
-------------------------
## Reformula el último mensaje de confirmación

Una de las reescrituras históricas más simples que podemos hacer con git es cambiar el último mensaje de confirmación. Supongamos que, justo después de realizar una confirmación, encuentra un error tipográfico en su descripción o encuentra una mejor manera de describir el conjunto de cambios.

Para hacer la corrección, ejecuta:
```terminal
$ git commit --ammend
 ```
el parámetro **--ammend ( Enmendar )** Abrirá un editor con el último mensaje de confirmación, para que puedas modificarlo. Después de guardar, esta acción va a sobreescribir el último commit y por ende contendrá los mismos cambios y pero con el nuevo mensaje.

Esto puede ser útil para incluir archivos que olvidó rastrear o incluir modificaciones a los archivos que acaba de confirmar. Para hacerlo, puede agregar los cambios y luego realizar la modificación:
 ```terminal
$ git add  README.md
$ git rm notes.txt
$ git commit --amend
 ```
Además de editar el mensaje de confirmación, la nueva confirmación contendrá los cambios especificados con git add y git rm. También puede editar el autor. Por ejemplo:
 ```terminal
git commit --amend --author = "Deyvid Ferrer <deyvidferrer@mail.com>"
 ```
**¡Logro desbloqueado!**

Ahora puede cambiar el último commit de su repositorio para incluir cambios más recientes en los archivos y / o mejorar el mensaje de confirmación.

**Importante: Pero no empiece a enmendar todo, antes de comprender la última sección descrita más abajo titulada "PELIGRO".**

--------------------------

# Reformular otros mensajes de confirmación

 ```terminal
$ git Interactive Rebase
 ```

git rebase vuelve a aplicar los commits, uno por uno, en el mismo orden, de tu rama actual a otra. Acepta varias opciones y parámetros, por lo que es una explicación  bastante por encima, de lo contrario podríamos escribir un libro solo sobre esto.

Una opción interesante que acepta es --interactive (-i para abreviar), que abrirá un editor con una lista de las commits que están a punto de cambiarse. Esta lista acepta comandos, lo que te permitira editar la lista antes de iniciar la acción de rebase.

**Veamos un ejemplo.**

Supongamos que quiero reformular cualquiera de los últimos 4 commits de este blog.
 ```terminal
$ git rebase -i HEAD~4, y esto es lo que veo:

pick 07c5aes Arreglando la distribucion de listas en el index
pick de9b1eb Fix verificador de articulos
pick 2d66753 Elminando todos los resaltados en la pagina
pick fa20af3 git interactive rebase, squash, amend

# Rebase 8db7e5d..fa20ar9 onto 8db7e5d
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
 ```
Vemos los cuatro últimos commits, de la más antigua a la más reciente.

¿Ven el comentario debajo de la lista de commits?

Buen trabajo explicando, git!
pick (p para abreviar) es la acción predeterminada. En este caso, volvería a aplicar la confirmación tal cual, sin cambios en su contenido o mensaje. Guardar (y ejecutar) este archivo no haría cambios en el repositorio.

**Si digo reescribir (r para abreviar)** en una confirmación, quiero editar:

 ```terminal
pick 07c5aes Arreglando la distribucion de listas en el index
pick de9b1eb Fix verificador de articulos
r 2d66753 Elminando todos los resaltados en la pagina
pick fa20af3 git interactive rebase, squash, amend
 ```
Cuando guarde y salga del editor, git seguirá los comandos descritos, aterrizando en el editor nuevamente, como si hubiera enmendado el commit 2d66753. Edito este mensaje de confirmación, guardo y salgo del editor, y aquí está el resultado:
```terminal
deyvidferrer.com tc-git-rebase % git rebase -i HEAD~4
[detached HEAD dd62a66] deja de resaltar las lineas
 Author: **MiOtroYo**
 Date: Fri Oct 31 10:52:26 2020 -0500
 2 files changed, 39 insertions(+), 42 deletions(-)
Successfully rebased and updated refs/heads/tc-git-rebase.
 ```
Ahora el **MiOtroYo**, dice en su mensaje de commit "deja de resaltar las lineas"

**¡Logro desbloqueado!**

Ahora puede cambiar el mensaje de cualquier información que desee. Puede hacerlo, sólo asegúrese de comprender la sección "PELIGRO".
------------------------------

# Squash

Otros dos comandos que nos ofrece rebase interactive son:

**squash (s para abreviar)**, que fusiona el commit con el anterior (el de la línea anterior)

**fixup (f para abreviar)**, que actúa como "squash", pero descarta el mensaje de esta confirmación

Continuaremos trabajando en el ejemplo de rebase en el que trabajamos antes. Tuvimos cuatro commits, la mía y otras tres de **MiOtroYo**, que estaban relacionadas con su publicación anterior de las listas en el index:

```terminal
pick 07c5aes Arreglando la distribucion de listas en el index
pick de9b1eb Fix verificador de articulos
pick 2d66753 Elminando todos los resaltados en la pagina
pick fa20af3 git interactive rebase, squash, amend
 ```

Supongamos que quiero fusionar las commits de **MiOtroYo**, porque pertenecen al mismo conjunto de cambios lógico, por lo que podemos revertirlo fácilmente si descubrimos que preferimos no tener esos cambios en este repositorio.

Queremos mantener el primer mensaje de confirmación y aplastar las dos commits posteriores en la anterior. Cambio de pick a squash donde sea apropiado:

```terminal
pick 07c5abd Arreglando la distribucion de listas en el index
s de9b1eb Fix verificador de articulos
s 3e7ee36 Elminando todos los resaltados en la pagina
pick fa20af3 git interactive rebase, squash, amend
```

Guarde, y aterrizó en el editor para decidir el mensaje de confirmación de las tres commits combinadas (vea cómo se concatenan una tras otra):

```terminal
# This is a combination of 3 commits.
# The first commit's message is:
Arreglando la distribucion de listas en el index
Besides demystifying a relatively complex tool, protocol, and etiquette, this post is intended to help with problems such as the one outlined in this tweet:
> la lista de distribucion del index se encontraba desorganizada
> y contenia datos importantes que se cargaron sin darse cuenta.

# This is the 2nd commit message:
Fix verificador de articulos
# This is the 3rd commit message:
Elminando todos los resaltados en la pagina

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Author:    **MiOtroYo**
# Date:      Tue Sep 2 09:39:07 2020 -0500
#
# rebase in progress; onto 71d4789
# You are currently editing a commit while rebasing branch 'tc-git-rebase' on '71d4789'.

```
Decido eliminar el tercer mensaje de confirmación y agregar una nota más relevante al segundo mensaje de confirmación.

Guarde el editor y las cuatro commits se transformaron en dos: la de **MiOtroYo** y la mía después.

**¡Bueno!**

Podríamos haber usado el comando fixup, si hubiéramos visto antes qué queremos los cambios, pero no el mensaje de confirmación, de la tercera confirmación. En ese caso, los comandos se verían así:

```terminal
pick 07c5abd Introduce OpenPGP and teach basic usage
s de9b1eb Fix verificador de articulos
f 2d66753 Elminando todos los resaltados en la pagina

pick fa20af3 git interactive rebase, squash, amend
```
Cuando se guardó, el editor habría incluido el tercer mensaje de confirmación ya comentado para nosotros.

Al guardar se generará el mismo resultado: 2 commits en lugar de 4, cada una con una única publicación de blog diferente.

**¡Logro desbloqueado!**

Ahora puede fusionar commits. Como siempre, tenga en cuenta la sección PELIGRO.
-------------------------------

# Rebase encima del Máster

Bifurcamos una rama y comenzamos a trabajar en otra rama de funcionalidades y avanzamos en esta nueva rama. Nuestra historia se parece a:

```terminal
      A---B---C feature
     /
D---E---F---G upstream/master
```
El mantenedor de la biblioteca pregunta cómo "rebasar sobre el Master", por lo que solucionamos cualquier conflicto de fusión que pueda surgir entre ambas ramas y mantenemos nuestro conjunto de cambios juntos. Al mantenedor le gustaría ver un historial como:
```terminal
              A'--B'--C' feature
             /
D---E---F---G upstream/master
```
Queremos volver a aplicar nuestras commits, una por una, en orden, en el Master de upstream. ¡Suena como la descripción del comando rebase! Veamos qué comandos nos llevarían al escenario deseado:

```terminal
# Point our `upstream` remote to the original fork
$ git remote add upstream https://github.com/thoughtbot/factory_girl.git

# Fetch latest commits from `upstream` (the original fork)
$ git fetch upstream

# Checkout our feature branch
$ git checkout feature

# Reapply it onto upstream's master
$ git rebase upstream/master

# Fix conflicts, then `git rebase --continue`, repeat until done
# Push to our fork
$ git push --force origin feature
```

**¡Logro desbloqueado!**

Su rama de características se aplicará sobre el último Master de la bifurcación original.
----------------------------------------------

# PELIGRO: Estás reescribiendo la historia.
----------------------------------------------

¿Ves el **--force** en el último comando git push? Eso significa que estamos sobrescribiendo el historial del repositorio. Esto siempre es seguro en las commits que no compartimos con otros miembros del equipo o en las ramas que nos pertenecen.

Pero si fuerza las ediciones push que ya se compartieron con el equipo (commits que existen fuera de mi repositorio, como los cambios que hice en las commits de PGP que ya se han compartido), entonces la rama de todos se desincroniza.

Reescribir el historial significa abandonar los commits existentes y crear nuevas, que pueden ser muy similares pero son diferentes.

**Si otros basan el trabajo en sus commits anteriores, y luego usted reescribe y fuerza sus commits, los miembros de su equipo tendrán que volver a fusionar su trabajo (si notan la pérdida potencial).**

Es una buena práctica, **colocar en el prefijo de nuestras ramas, nuestras iniciales**, lo que indica que esas commits pueden reescribirse y otras no deben agregar commits a la rama. Cuando esos commits aterrizan en master o en una rama compartida, nunca los volvemos a escribir.

Por lo tanto, reescriba el historial de git, siempre que las commits reescritas existan solo en su repositorio, o usted y su equipo sepan que nadie más debería basar el trabajo en ellas.
