---
title: Cómo SUBIR un PROYECTO A GITHUB desde CONSOLA
tags: [Git, Github]
style: border
color: primary
#thumbs: 2020-09-15-agregar-repositorio-remoto-git.png
description: En este video, vamos a aprender como es la creación de un repositorio y como conectarlo a nuestro proyecto local con git y su subida a Github.
---

# Cómo SUBIR un PROYECTO A GITHUB desde CONSOLA

{% include elements/video.html id="8cLpuSHBBx8" %}

Para agregar un  Repositorio remoto nuevo, se usa el comando
```terminal
$ git remote add
```

Nota: debes estar dentro del directorio donde está almacenado tu repositorio.

El comando git remote add recibe dos parametros:
Un nombre remoto, como por ejemplo: origin

Una URL remota, por ejemplo, https://github.com/tunombredeusuariodegit/repo.git

```terminal
$ git remote add origin https://github.com/tunombredeusuariodegit/turepo.git
```

## Ver repositorios remotos vinculados al proyecto

```terminal
$ git remote -v

> origin  https://github.com/user/repo.git (fetch)
> origin  https://github.com/user/repo.git (push)
```

Posibles problemas
Puedes encontrar estos errores al tratar de agregar un remoto.

**El nombre remoto ya existe**
Este error significa que trataste de agregar un remoto con un nombre que ya existe en tu repositorio local:

```terminal
$ git remote add origin https://github.com/tunombredeusuariodegit/repo.git
> fatal: remote origin already exists.
 ```

Tienes diferentes opciones de arreglar estos problemas y te las explico acontinuacion.

## Renombrar un repositorio remoto
Utiliza el comando
```terminal
$git remote rename
```
para renombrar un repositorio remoto existente.

El comando git remote rename recibe dos parametros:
Un nombre de remoto existente, por ejemplo, origen
Un nombre nuevo para el remoto, por ejemplo, destino
Algo como esto:

```terminal
$ git remote rename origin nuevo_nombre
```
### Cambiar el nombre del remoto de 'origen' a 'nuevo_nombre'

```terminal
$ git remote -v
```
### Verificar el nombre nuevo del remoto
> nuevo_nombre   https://github.com/tunombredeusuariodegit/repo.git (fetch)
> nuevo_nombre   https://github.com/tunombredeusuariodegit/repo.git (push)


## Eliminar un repositorio remoto
Con el comando

```terminal
git remote rm
```

podras eliminar una URL remota de tu repositorio
El comando git remote rm recibe un parametro:
El nombre de un remoto, por ejemplo nuevo_nombre (nuevo_nombre)

```terminal
$ git remote -v
# Ver los remotos actuales
> origin  https://github.com/tunombredeusuariodegit/turepo.git (fetch)
> origin  https://github.com/tunombredeusuariodegit/turepo.git (push)
> nuevo_nombre  https://github.com/OTRO/REPOSITORY.git (fetch)
> nuevo_nombre  https://github.com/OTRO/REPOSITORY.git (push)
```

```terminal
$ git remote rm nuevo_nombre
# Eliminar remoto
$ git remote -v
# Verificar que se haya ido
> origin  https://github.com/tunombredeusuariodegit/turepo.git (fetch)
> origin  https://github.com/tunombredeusuariodegit/turepo.git (push)
```
