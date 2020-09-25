---
title: CHEAT SHEET GIT 👽👽
tags: [Git, Cheatsheet]
style: border
color: primary
description: Todas las instrucciones elementales para trabajar con git.
---
## Comandos Basicos:
------------------------------------------------
```terminal
$ git init <directory>
```
Cree un repositorio de Git vacío en el directorio especificado. Corre sin
argumentos para inicializar el directorio actual como un repositorio git.


```terminal
$ git clone <repo>
```
Clone el repositorio ubicado en <repo> en la máquina local. El repositorio original puede ser ubicado en el sistema de archivos local o en una máquina remota a través de HTTP o SSH.


```terminal
$ git config user.name <name>
```
Defina el nombre del autor que se utilizará para todas las confirmaciones en el repositorio actual. Desarrolladores comúnmente usa --global flag para establecer opciones de configuración para el usuario actual.


```terminal
$ git add <directory>
```
Organice todos los cambios en <directorio> para la próxima confirmación.
Reemplace <directorio> con un **archivo** para cambiar un archivo específico.


```terminal
$ git commit -m
```
Confirme la instantánea por etapas, pero en lugar de iniciar un editor de texto, use **mensaje** como mensaje de confirmación."<message>"


```terminal
$ git status
```
Lista los archivos que están almacenados, no organizados y sin seguimiento.


```terminal
$ git log
```
Muestra todo el historial de confirmaciones utilizando el formato predeterminado.
Para personalizarlo, consulte las opciones adicionales.


```terminal
$ git diff
```
Muestra cambios sin etapas entre su índice y
directorio de trabajo.

## DESHACER CAMBIOS:
------------------------------------------------
```terminal
$ git revert <commit>
```
Crear un nuevo commit que deshaga todos los cambios realizados en el commit que se quiere revertir,
luego se aplica a la rama actual.


```terminal
$ git reset <file>
```
Elimine <archivo> del área de preparación, pero deje el directorio de trabajo
sin alterar. Esto desestabiliza un archivo sin sobrescribir ningún cambio.


```terminal
$ git clean -n
```
Muestra qué archivos se eliminarían del directorio de trabajo.
Utilice el indicador -f en lugar del indicador -n para ejecutar la limpieza.

## REESCRIBIR LA HISTORIA DE GIT
------------------------------------------------
```terminal
$ git commit --amend
```
Reemplaza el ultimo commit y agrega los nuevos cambios de nuestro staging area para modificar nuestro ultimo commit.  Se puede usar para editar el mensaje de la última confirmación.


```terminal
$ git rebase <base>
```
Vuelva a basar la rama actual en <base>. <base> puede ser un ID de confirmación, nombre de la rama, una etiqueta o una referencia relativa a HEAD.


```terminal
$ git reflog
```
Muestra un registro de cambios en HEAD del repositorio local.
Agregue la marca --relative-date para mostrar la información de la fecha o --all para mostrar todas las referencias


## GIT BRANCHES
------------------------------------------------
```terminal
$ git branch
```
Muestra todas las ramas en su repositorio. Si Agregua un argumento **nombrederama** esta creara una nueva rama con ese nombre.


```terminal
$ git checkout -b <nombrederama>
```
Crea y se mueve a una nueva rama llamada <nombrederama>.


```terminal
$ git merge <branch>
```
Fusiona la rama enviada en **branch** con la rama en la que estas posicionado actualmente.

Continara...
------------------------
Espero que esto te ayude en tu dia a dia usando Git.

Si estas aprendiendo a usar Git entonces te recomiendo ver mi serie de video Tutoriales de Git en mi Canal de Youtube.

{% include elements/video.html id="eHIsHiaddwk" %}
