---
title: Git de Novato a experto - Parte 2
tags: [Git, Tutorial]
style: border
color: primary
description: Ahora vamos a aprender la funcionalidad más importante, la piedra angular de git y para lo que fue hecha, La creación de Ramas / Branches.
---

{% include elements/video.html id="Rboyznyszgs" %}

## Parte II - Creación y manejo de Ramas ( Branches ) y fusiones ( Merging ) entre ellas.
----------

Como vimos en nuestra primera parte, ya aprendimos los comandos basicos para movernos dentro de la herramienta de git.

Ahora vamos a aprender la funcionalidad más importante, la piedra angular de git y para lo que fue hecha.

La creación de Ramas / Branchs

Anteriormente vimos que un commit es un punto de referencia que marcamos en la línea de tiempo de nuestro proyecto, entonces un branch sería una bifurcación en esa línea de tiempo y esta bifurcación crea un camino nuevo en paralelo, que puede contener cambios significativos en comparación con nuestra rama principal, sin afectar a la misma, que posteriormente podemos llegar a fusionar ( merge ).

**Comandos que usaremos en esta segunda parte:**

```terminal
git Branch nombre_de_rama
git checkout nombre_de_rama
git checkout -b
git log
git branch -d
```

El primer comando ( git branch ) nos sirve para poder ver desde la terminal
todos los branches que tengamos creados localmente, por defecto solo tenemos uno y es llamado Master.

Si queremos crear uno nuevo entonces debemos usar el comando

git branch acompañado del nombre que queramos ponerle a nuestra rama.
Por ejemplo: cambio-estilos

```terminal
git branch cambio-estilos.
```

Este nos creará un nuevo branch, usando como referencia nuestro branch master, en su último commit. es decir, va a replicar nuestra versión actual.

Con esto hecho, ya podemos movernos a nuestra nueva rama creada

para eso usamos el comando:

```terminal
git checkout cambio-estilos
```

que sirve para movernos entre las diferentes ramas y commits de nuestro proyecto.

una vez ubicados en nuestro nuevo branch, podemos hacer todos los cambios que queramos, incluso simplemente probar a cambiar algunas cosas y hacer commits de ellos.

con esto al cambiar y posicionarnos nuevamente en nuestra rama master

```terminal
git checkout master
```

vamos a ver que los cambios que hicimos en nuestro branch cambio-estilos
no estarán disponibles y tenemos que volver a nuestro branch cambio-estilos para volver a verlos. Entonces un branch crea una bifurcación en nuestra rama de proyecto principal, para que podamos desarrollar en paralelo sin afectar nuestra rama principal.

Posteriormente cuando los cambios ya esten aprobados y se deseen fusionar en nuestra rama master, podemos hacerlo con el comando

```terminal
git merge cambio-estilos
```

**Antes de hacer el merge, nos debemos de asegurar que estamos posicionados sobre el branch en el que queremos recibir los cambios. En este caso es Master.**

```terminal
git checkout master
git merge cambio-estilos
```

Esto nos devolverá un fast forward si todo salió bien y nuestros cambios ahora estarán disponibles en nuestra rama master.

Si queremos eliminar la rama, porque ya no la vamos a necesitar usamos el siguiente comando

```terminal
git branch -d cambio-estilos.
```

Con estos comandos nuevos, vas a ser capaz manejar tantas versiones / ramas / branches como necesites.


<div id="checkout-commit"></div>
# Parte 2.1 Git checkout commit
-------------------------------------------------------------

{% include elements/video.html id="ZpMlLL-mnyA" %}

git checkout hash del commit
por ejemplo:

git checkout edfb7e1501fb5942e3f25799c35294ede15ba7a8

En la clase de hoy veremos el comando git checkout y como viajar a commits anteriores, ya vimos el comando checkout anteriormente en la clase de como crear branches y movernos entre ellos, pero nos quedó pendiente el viaje entre commits.

Cabe destacar que debemos tener nuestro staged area y untaged area limpios, para poder movernos entre los diferentes commits.

Para poder obtener el hash del commit

git log

con este comando veremos el codigo unico de cada commit, solo tenemos que copiarlo y luego ejecutar

git checkout edfb7e1501fb5942e3f25799c35294ede15ba7a8
