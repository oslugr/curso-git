#Solución de problemas con git

##Objetivos

En todo desarrollo colaborativo aparecen problemas. No es difícil solucionarlos.

* Saber obtener información sobre git
* Conocer el estado e historial de nuestros proyectos
* Modificar y recuperar estados anteriores
* Solucionar conflictos entre repositorios

##Obtener Ayuda

Lo primero que necesitamos a la hora de enfrentarnos a las dificultades es conocer nuetras herramientas.

Git dispone de una ayuda detallada que nos resultará muy útil. Para invocarla sólo hay que hacer 

`git help`

también se puede obtener ayuda de un comado concreto con `git help COMANDO`, por ejemplo:

`git help commit`

##Viendo el historial

Has hecho una serie de modificaciones seguidas de commits con sus comentarios ¿Cómo puedes ver todo eso? Para ello tienes la instrucción

`git log`

La orden `git log` te mostrará un listado de todos los cambios efectuados, con sus respectivos comentarios, empezando desde el más reciente hasta el más antiguo.

El formato de cada commit en la respuesta es como este:

```
commit c2ac7c356156177a50df5b4870c72ce01a88ae63
Author: psicobyte <psicobyte@gmail.com>
Date:   Sun Mar 30 11:54:15 2014 +0200
   Cambios menores en las explicaciones de git add y git status
```

La primera línea es un *hash* único que identifica al commit (y que más adelante no será muy útil), seguida del autor, la fecha en que se hizo y el comentario que acompañó al commit. 

Por defecto, `git log` nos mostrará todas las entradas del log. para ver sólo un número determinado sólo tienes que añadirle el parámetro `-NUMERO`, donde NUMERO es el número de entradas que quieres ver, por ejemplo:

`git log -4`

mostrará las últimas cuatro entradas en el log.

Otra opción posible, si quieres ver una versión más resumida y compacta de los datos, es `--oneline`, que te muestra una versión compacta.

Si, por el contrario, quieres más detalles, la opción `-p` te mostrará, para cada commit, todos los cambios que se realizaron en los archivos (en formato diff).

Otra ayuda visual es `--graph`, que dibuja (con caracteres ASCII) un árbol indicando las ramas del proyecto (ya veremos eso un poco más adelante).

`git log` tiene un montón de opciones más (para filtrar por autor o fecha, mostrar estadísticas...) que, además, se pueden usar en combinación. Por ejemplo, la isntrucción

`git log --graph --oneline` 

Mostrará los commits en versión compacta y dibujando las ramas (cuando las haya), dando una salida parecida a esta:

```
* 6ad05c1 Sólo una cosilla
*   0678363 Resuelve conflicto como ejemplo
|\  
| * bf454ef Prueba para crear conflictos. Así mismo.
* | 8785174 Añade título nueva sección
|/  
* afee5ab Acaba un-solo-usuario y listo para conflictos
* fd04eff Corregido (más o menos) el markdown)
```

Para más detalles, recuerda que `git help log` es tu amigo.

##Borrado de archivos

En git se pueden borrar archivos con la orden `git rm`.

`git rm NOMBRE_DEL_FICHERO`

Funciona como la propia orden del sistema operativo, con la salvedad de que *tambien* borra el archivo del Index, si estuviera allí. Esto lo hace muy útil en ocasiones.

Si necesitas borrar el archivo del Index pero sin borrarlo de directorio de trabajo (porque, por ejemplo, te has arrepentido y no quieres incluirlo en el próximo commit), se puede hacer con la opción `--cached` del siguiente modo:

`git rm --cached NOMBRE_DEL_FICHERO`

Otra ocpión para hacer esto mismo es con `git reset HEAD` que se usa del siguiente modo:

`git reset HEAD NOMBRE_DEL_ARCHIVO`

##Rehacer un commit

Puedes rehacer el último commit usando la opción `--amend` de este modo:

`git commit --amend`

Si no has modificado nada en tus archivos, esto simplemente te permitirá reescribir el comentario del commit pero, si por ejemplo habiás olvidado añadir algo al Index, puedes hacerlo antes del `git commit --amend` y se aplicará en el commit.

##Deshacer cambios en un archivo

Has cambiado un archivo en tu directorio de trabajo, pero te arrepientes y quieres recuperar la versión del HEAD (la del último commit). Nada más fácil que:

`git checkout -- NOMBRE_DEL_ARCHIVO`

##Resolviendo conflictos
	
Normalmente los conflictos suceden cuando dos usuarios han modificado
    la misma línea, o bien cuando han modificado un fichero binario;
    por eso los ficheros binarios **no** deben estar en un
    repositorio. Te aparecerá un conflicto de esta forma cuando vayas
    a hacer `push`

```	
To git@github.com:oslugr/curso-git.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:oslugr/curso-git.git'
consejo: Updates were rejected because the tip of your current branch is behind
consejo: its remote counterpart. Merge the remote changes (e.g. 'git pull')
consejo: before pushing again.
consejo: See the 'Note about fast-forwards' in 'git push --help' for details.
```

El error indica que la *punta* de tu rama está detrás de la rama remota (es decir, que hay modificaciones posteriores a tu última sincronización). Rechaza por lo tanto el `push`, pero vamos a hacer `pull` para ver qué es lo que ha fallado

```
remote: Counting objects: 7, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4 (delta 3), reused 0 (delta 0)
Unpacking objects: 100% (4/4), done.
De github.com:oslugr/curso-git
   afee5ab..bf454ef  master     -> origin/master
Auto-merging texto/mas-usos.md
CONFLICTO(contenido): conflicto de fusión en texto/mas-usos.md
Automatic merge failed; fix conflicts and then commit the result.
```

El conflicto de fusión te indica que no hay forma de combinar los dos
ficheros porque hay cambios en la misma línea. Así que hay que
arreglar los conflictos. En general, si se trata de este tipo de
conflictos, no es complicado. Al mirar el fichero aparecerá algo así

```
    <<<<<<< HEAD
    ## Resolviendo conflictos en `git`
    =======
    ## Vamos a ver cómo se resuelven los problemas en git
    >>>>>>> bf454eff1b2ea242ea0570389bc75c1ade6b7fa0
```

Lo que uno tiene está entre la primera línea y los signos de igual; lo
que hay en la rama remota está a continuación y hasta la cadena que
indica el número del commit en el cual está el conflicto. Resolver el
conflicto es simplemente borrar las marcas de conflicto (los <<<<< y
los >>>>> y los ====) y elegir el código con el que nos quedamos; en
este caso, como se ve, es el que aparece efectivamente en este
capítulo.

Una vez hecho eso, se puede ya hacer `push` directamente sin ningún
problema.

##Retrocediendo al pasado

Para recuperar el estado de tu directorio de trabajo tal como estaba en algún momento del pasado, primero necesitas saber qué momento es ese. Eso se consigue con `git log` que, como vimos, nos devuelve (entre otras cosas) un hash que identifica al commit.

Con ese hash ya podemos hacer un `git reset` del siguiente modo:

`git reset --hard HASH_DEL_COMMIT_A_RECUPERAR`

Eso, en cierto modo, volverá atrás en el tiempo, deshará los commits posteriores al indicado y traerá a tu directorio de trabajo los archivos tal y como estaban entonces. Todos los cambios posteriores desaparecerán, así que mucho cuidado.

Como consejo, recuerda hacer `push` antes de jugar con `git reset --hard`. De este modo, si quieres recuperar todo el trabajo posterior, no tienes más que hacer `pull` y los recuperarás de nuevo.

También te puedes salvaguardar usando otra rama para hacer el `git reset --hard` sobre ella, pero el uso de ramas es algo que veremos un poco más adelante.

##Viendo (y recuperando) archivos antiguos

Puedes ver los cambios que hiciste en un commit si haces 

`git show HASH_DE_UN_COMMIT`

Esto puede ser muy útil, pero aun hay más. Si haces `git show HASH_DE_UN_COMMIT:ruta/a/un/archivo` te mostrará el estado de ese archivo en aquel commit.

Esto nos va a servir para hacer un pequeño truco:

`git show HASH_DE_UN_COMMIT:ruta/a/un/archivo > archivo_copia`

La orden anterior nos permite redireccionar la salida de `git show` a un archivo llamado `archivo_copia`, con lo que obtendremos una copia del archivo tal y como estaba en el commit indicado.
