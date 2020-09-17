---
title: Cómo resolver conflictos de fusión en Git (Merge) 👽👽
tags: [Git, Tutorial]
style: border
color: primary
description: Los sistemas de control de versiones tienen que ver con la gestión de contribuciones entre varios autores distribuidos (normalmente desarrolladores). A veces, varios desarrolladores pueden intentar editar el mismo contenido.
---

{% include elements/video.html id="cBMu43Uj9tA" %}

## Conflictos de fusión de Git
---------------------------------

Para empezar, los sistemas de control de versiones tienen que ver con la gestión de contribuciones entre varios autores distribuidos. A veces, varios desarrolladores pueden intentar editar el mismo contenido. Si el desarrollador A intenta editar el código que el desarrollador B está editando, puede producirse un conflicto. Para aliviar la aparición de conflictos, los desarrolladores trabajarán en ramas aisladas separadas.

La responsabilidad principal del comando git merge es combinar ramas separadas y resolver cualquier edición conflictiva. Git hace que la fusión sea muy fácil. La mayoría de las veces, Git descubrirá cómo integrar automáticamente nuevos cambios.

Los conflictos generalmente surgen cuando dos personas han cambiado las mismas líneas en un archivo, o si un desarrollador borró un archivo mientras otro desarrollador lo estaba modificando. En estos casos, Git no puede determinar automáticamente qué es correcto. Los conflictos solo afectan al desarrollador que realiza la fusión, el resto del equipo desconoce el conflicto.

Git marcará el archivo como conflictivo y detendrá el proceso de fusión. Entonces, es responsabilidad de los desarrolladores resolver el conflicto.

Tipos de conflictos de fusión
Una combinación puede entrar en un estado de conflicto en dos puntos separados. Al iniciar y durante un proceso de fusión. La siguiente es una discusión sobre cómo abordar cada uno de estos escenarios de conflicto.

**Git no puede iniciar la fusión**

Una fusión no se iniciará cuando Git vea que hay cambios en el directorio de trabajo o en el área de preparación del proyecto actual.

Git no puede iniciar la fusión porque estos cambios pendientes podrían ser sobrescritos por las confirmaciones que se están fusionando. Cuando esto sucede, no se debe a conflictos con otros desarrolladores, sino a conflictos con cambios locales pendientes. El estado local deberá estabilizarse mediante git stash, git checkout, git commit o git reset. Un error de fusión en el inicio generará el siguiente mensaje de error:

la entrada '<nombre de archivo>' no está actualizada. No se puede fusionar. (Cambios en el directorio de trabajo)


**Git falla durante la fusión**

Un error DURANTE una fusión indica un conflicto entre la rama local actual y la rama que se está fusionando. Esto indica un conflicto con el código de otro desarrollador. Git hará todo lo posible para fusionar los archivos, pero dejará cosas para que usted las resuelva manualmente en los archivos en conflicto. Una falla a mitad de fusión generará el siguiente mensaje de error:

la entrada '<nombre_archivo>' se sobrescribirá mediante la combinación. No se puede fusionar. (Cambios en el área de preparación)


**Creando un conflicto de fusión**

Para familiarizarse realmente con los conflictos de fusión, la siguiente sección simulará un conflicto para luego examinarlo y resolverlo. El ejemplo utilizará una interfaz Git de línea de comandos similar a Unix para ejecutar la simulación de ejemplo.

```terminal
$ mkdir git-merge-test
$ cd git-merge-test
$ git init.
$ echo "este es un contenido con el que meterse"> merge.txt
$ git agregar merge.txt
$ git commit -am "estamos confirmando el contenido inicial"

[master (root-commit) d48e74c] estamos confirmando el contenido inicial
1 archivo modificado, 1 inserción (+)
modo de creación 100644 merge.txt
```

Este ejemplo de código ejecuta una secuencia de comandos que logran lo siguiente.

Cree un nuevo directorio llamado git-merge-test, cambie a ese directorio e inicialícelo como un nuevo repositorio de Git.

Cree un nuevo archivo de texto merge.txt con algo de contenido.

Agregue merge.txt al repositorio y consúltelo.
Ahora tenemos un nuevo repositorio con un maestro de rama y un archivo merge.txt con contenido. A continuación, crearemos una nueva rama para usar como fusión conflictiva.

```terminal
$ git checkout -b nueva_ rama_a_merge_later
$ echo "contenido totalmente diferente para fusionar más tarde"> merge.txt
$ git commit -am "editó el contenido de merge.txt para causar un conflicto"

[new_branch_to_merge_later 6282319] editó el contenido de merge.txt para causar un conflicto
1 archivo modificado, 1 inserción (+), 1 eliminación (-)
```

La secuencia de comandos en curso logra lo siguiente:
crea y echa un vistazo a una nueva rama llamada new_branch_to_merge_later
sobrescribir el contenido en merge.txt
cometer el nuevo contenido
Con esta nueva rama: new_branch_to_merge_later hemos creado una confirmación que anula el contenido de merge.txt

Cambiado a la rama 'maestra'

```terminal
$ git checkout master

$ echo "contenido para agregar" >> merge.txt

$ git commit -am "contenido agregado a merge.txt"

[master 24fbe3c] agregó contenido a merge.tx
1 archivo modificado, 1 inserción (+)
```

Esta cadena de comandos comprueba la rama maestra, agrega contenido a merge.txt y lo confirma. Esto ahora coloca nuestro repositorio de ejemplo en un estado en el que tenemos 2 nuevas confirmaciones. Uno en la rama maestra y otro en la rama new_branch_to_merge_later. ¡En este momento vamos a fusionar git new_branch_to_merge_later y ver qué pasa!

```terminal
$ git merge new_branch_to_merge_later

Fusionar automáticamente merge.txt
CONFLICTO (contenido): Fusionar conflicto en merge.txt
Error de fusión automática; arregle los conflictos y luego confirme el resultado.
```
BOOM 💥. Aparece un conflicto. ¡Gracias, Git por informarnos sobre esto!

**Cómo identificar conflictos de fusión**

Como hemos experimentado en el ejemplo anterior, Git producirá una salida descriptiva que nos permitirá saber que ha ocurrido un CONFLICTO. Podemos obtener más información ejecutando el comando git status

```terminal
$ git status

(arregla los conflictos y ejecuta "git commit")
(use "git merge --abort" para cancelar la combinación)
```

Caminos no fusionados:

```terminal
(use "git add <file> ..." para marcar la resolución)
```

ambos modificados: merge.txt
La salida del estado de git indica que hay rutas no fusionadas debido a un conflicto. El archivo merge.text ahora aparece en un estado modificado. Examinemos el archivo y veamos qué se modificó.

```terminal
$ cat merge.txt
```

En nuestro editor de texto de la terminal se deberia mostrar algo como esto:

```terminal
<<<<<<< HEAD este es un contenido con el que meterse contenido para agregar ======= contenido totalmente diferente para fusionar más tarde >>>>>>> nueva_rama_para_fusionar_later
Aquí hemos utilizado el comando cat para publicar el contenido del archivo merge.txt. Podemos ver algunas nuevas incorporaciones extrañas.
<<<<<<< HEAD
=======
>>>>>>> nueva_rama_para_fusionar_later
```

Piense en estas nuevas líneas como "divisores de conflictos". La línea ======= es el "centro" del conflicto. Todo el contenido entre el centro y la línea <<<<<<< HEAD es contenido que existe en el maestro de rama actual al que apunta la referencia HEAD. Alternativamente, todo el contenido entre el centro y >>>>>>> new_branch_to_merge_later es contenido que está presente en nuestra rama de fusión.

## Cómo resolver conflictos de fusión usando la línea de comando

La forma más directa de resolver un conflicto de fusión es editar el archivo en conflicto. Abra el archivo merge.txt en su editor favorito. Para nuestro ejemplo, simplemente eliminemos todos los divisores de conflictos. El contenido de merge.txt modificado debería verse así:

este es un contenido con el que meterse
contenido para agregar
contenido totalmente diferente para fusionar más tarde

Una vez que el archivo ha sido editado, use git add merge.txt para preparar el nuevo contenido combinado. Para finalizar la fusión, cree una nueva confirmación ejecutando:

```terminal
git commit -m "fusionó y resolvió el conflicto en merge.txt"
```

Git verá que el conflicto se ha resuelto y crea un nuevo compromiso de fusión para finalizar la fusión.

**Comandos de Git que pueden ayudar a resolver conflictos de fusión**

**Herramientas generales**
```terminal
$ git status
```

El comando de estado se usa con frecuencia cuando se trabaja con Git y durante una fusión ayudará a identificar archivos en conflicto.
```terminal
git log --merge
```
Pasar el argumento --merge al comando git log producirá un registro con una lista de confirmaciones que entran en conflicto entre las ramas fusionadas.
```terminal
git diff
```
diff ayuda a encontrar diferencias entre los estados de un repositorio / archivos. Esto es útil para predecir y prevenir conflictos de fusión.

**Herramientas para cuando git no puede iniciar una fusión**
```terminal
git checkout
```
el checkout se puede usar para deshacer cambios en archivos o para cambiar ramas
```terminal
git reset - mezclado
```
Reset se puede utilizar para deshacer cambios en el directorio de trabajo y el área de preparación.
Herramientas para cuando surgen conflictos de git durante una fusión
```terminal
git merge --abort
```
La ejecución de git merge con la opción --abort saldrá del proceso de fusión y devolverá la rama al estado anterior a que comenzara la fusión.

### Resumen

Los conflictos de fusión pueden ser una experiencia intimidante. Afortunadamente, Git ofrece herramientas poderosas para ayudar a navegar y resolver conflictos. Git puede manejar la mayoría de las fusiones por sí solo con funciones de fusión automática. Surge un conflicto cuando dos ramas separadas han realizado ediciones en la misma línea en un archivo, o cuando un archivo se ha eliminado en una rama pero editado en la otra. Lo más probable es que surjan conflictos cuando se trabaja en un entorno de equipo.

------------------------

Si estas aprendiendo a usar Git entonces te recomiendo ver mi serie de video Tutoriales de Git en mi Canal de Youtube.
