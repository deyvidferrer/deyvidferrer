---
title: Como cambiar de rama en git
tags: [Git, Tutorial]
style: border
color: primary
description: En la clase de hoy veremos como el comando git stash nos ayuda a guardar todos nuestros cambios o trabajo en progreso que no ha sido commiteado y que se encuentra en nuestra staged o unstaged área.
---

{% include elements/video.html id="FwasOr6BexA" %}

## Parte III - Como hacer un git stash fácil y rápido
----------

**Comandos que usaremos en esta segunda parte:**

```terminal
git stash
git stash apply
git stash list
git stash apply stash{25}
```

En la clase de hoy veremos como el comando git stash nos ayuda a guardar todos nuestros cambios o trabajo en progreso que no ha sido commiteado y que se encuentra en nuestra staged o unstaged área.

Es muy común que estes trabajando en una rama y por diferentes motivos tengas que moverte a otra rama o commit, esto aveces arroja un mensaje de alerta indicando que no se puede cambiar de rama, porque tus cambios aun no estan guardados o commiteados y te pide que hagas un stash para guardarlos temporalmente y limpiar tu area de stage, lo cual te va a permitir moverte al branch que quieres.

Una vez que ya hiciste tu trabajo en el otro branch y quieres volver a lo que estabas haciendo WIP ( work in progress ), simplemente puedes moverte al branch donde estabas y ejecutar el comando

```terminal
git stash apply
```

para recuperar los últimos cambios que habías stasheado con tu trabajo en progreso.

Cabe destacar que puedes hacer tantos stash como desees y que los puedes aplicar en cualquier branch que desees, solo tienes que posicionar en el branch que deseas aplicar los cambios y ejecutar git stash apply.

Además, si tenemos varios stashes, podemos ver la lista del stash

```terminal
git stash list
```

y nos muestra una breve descripción del branch y el commit en el que hicimos el stash. Esto permite una identificación más rapida.

y para aplicarlo solo deberemos copiar el nombre que nos muestra en la lista del stash.

por ejemplo:

```terminal
git stash apply stash{25}
```

Esto seria todo por la clase de hoy.
