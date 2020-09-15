---
title: Cómo actualizar sus credenciales de Git en Windows 👽👽
tags: [Git, Credenciales, Windows]
style: border
color: primary
description: $ git pull
fatal: Error de autenticación para `repo url /`
Aparentemente, actualizar mis credenciales de dominio también rompió mis credenciales de Git.
.
---

## Parte III - Como hacer un git stash fácil y rápido
----------

Git es increíble y me encanta. Simple y llanamente. Funciona. Sin embargo, hay ocasiones en que las cosas dentro de Git se rompen. Y luego tienes que buscar en Google la solución.
Para resumirlo, mis credenciales de git en Windows habían caducado, así que las cambié.

Luego intenté hacer un git pull y recibí este bonito mensaje de error:

```terminal
$ git pull
fatal: Error de autenticación para `repo url /`
 ```

Aparentemente, actualizar mis credenciales de dominio también rompió mis credenciales de Git.
Para actualizar sus credenciales, vaya a

**Panel de control -> Administrador de credenciales -> Credenciales web o Credenciales Windows.**

Encuentre las credenciales relacionadas con su cuenta de git y edítelas para usar las contraseñas actualizadas según la imagen a continuación:

{% include elements/figure.html image="/assets/SharedScreenshot1.jpg" caption="The Ocean" %}

Espero que esto te ayude con tus problemas de Git.
