---
title: Cómo configurar el editor de texto de Git en WINDOWS 👽👽
tags: [Git, Errores]
style: border
color: primary
description: Cuando realizaste la instalación por primera vez de GIT en windows, es posible que no te hallas fijado en el editor de texto que elegiste.
---

## Cómo actualizar sus credenciales de Git en Windows

Seguramente, cuando realizaste la instalación por primera vez de GIT en windows, no te hallas dado cuenta, que debes escoger el editor de texto para git pueda abrir los cuadros de dialogo, que nos permitiran interactuar en los diferentes procesos y acciones de la herramienta.

Entonces es probable que quieras confiurar algun editor de texto de tu preferencia, en este caso particular vamos a usar a Atom como nuestro editor de texto por defecto en GIT.

Esto lo puedes cambiar de una forma muy fácil:  

*** Usa Git Bash como ventana de comandos ***

```terminal
$ git config --global core.editor "atom --wait"
```

**core.editor** es la variable de configuración que puedes modificar para usar un editor de texto determinado, al usar --global significa que lo vas a usar para todos tus repositorios, si o quieres usar solamente el repositorio actual puedes usar --local

Ahora vamos a verificar nuestra lista de configuracion de git

```terminal
$ git config --list
```

te debe aparecer algo como esto:

```terminal

core.symlinks=true
core.autocrlf=true
core.fscache=true
color.diff=auto
color.status=auto
color.branch=auto
color.interactive=true
help.format=html
rebase.autosquash=true
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
http.sslbackend=openssl
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
credential.helper=manager
core.editor=atom --wait
user.name=deyvidferrer
user.email=deyvidferrer@mimail.com
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.ignorecase=true
atomgithub.historysha=3b9822d2f204f660d2d30cd89797f4fb4716e204

```

Destacar que la propiedad:

**core.editor=atom --wait**

Este seteada de esta manera, de esta forma queda configurado git con Atom como editor de texto.

Espero que esto te ayude con tus problemas de Git.

------------------------

Si estas aprendiendo a usar Git entonces te recomiendo ver mi serie de video Tutoriales de Git en mi Canal de Youtube.

{% include elements/video.html id="FwasOr6BexA" %}
