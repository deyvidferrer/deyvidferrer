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

## Cómo actualizar sus credenciales de Git en Windows
----------

Git es una herramienta increíble. Sin embargo, hay ocasiones en que las cosas dentro de Git se rompen. Como por ejemplo: mis credenciales de git en Windows habían caducado, así que las cambié.

Luego intenté hacer un git pull y recibí este bonito mensaje de error:

```terminal
$ git pull
fatal: Error de autenticación para `repo url /`
 ```

Aparentemente, actualizar mis credenciales de dominio también rompió mis credenciales de Git.

Entonces, para actualizar sus credenciales, vaya a:

**Panel de control -> Administrador de credenciales -> Credenciales web o Credenciales Windows.**

Encuentre las credenciales relacionadas con su cuenta de git y edítelas para usar las contraseñas actualizadas según la imagen a continuación:

{% include elements/figure.html image="/assets/SharedScreenshot1.jpg" caption="The Ocean" %}

Espero que esto te ayude con tus problemas de Git.

------------------------

Si estas aprendiendo a usar Git entonces te recomiendo ver mi serie de video Tutoriales de Git en mi Canal de Youtube.

{% include elements/video.html id="FwasOr6BexA" %}
