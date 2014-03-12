# Más usos de `git`

## Objetivos

* Aprender patrones habituales de flujo de trabajo con `git`
* Aprender a trabajar con las ramas.
* Solucionar los conflictos cuando dos desarrolladores trabajan sobre la misma línea.
* Interpretar la historia en sus diferentes formatos

## Flujos de desarrollo de software (y quizás de otras cosas)

Un sistema como `git` no es independiente de una organización del
trabajo. Aunque a priori puedes trabajar como te dé la gana, el que te
facilite el uso de ciertas herramientas hace que sea más fácil usar
una serie de prácticas que son habituales en el desarrollo de software
(y de otras cosas, como documentación o novelas) para hacer más
productivos a los equipos de trabajo y poder predecir con más
precisión el desarrollo de los mismos. Por eso, aunque se puede usar
cualquier metodología de desarrollo de softare con el mismo, `git`
funciona mejor con
[metodologías ágiles](http://es.wikipedia.org/wiki/Desarrollo_%C3%A1gil_de_software)
que tienen ciclos más rápidos de producción y de despliegue de nuevas
características o de arreglo de las mismas. Las metodologias ágiles
son iterativas y en todas las iteraciones están presentes la mayoría
de los actores del desarrollo: clientes, desarrolladores, arquitectos;
incluso en algunas puede que esté la peña de márketing, a ver si se
enteran de lo que está haciendo el resto de la empresa para venderlo
(y no al revés, vender cosas que luego obligan al resto de la empresa
a desarrollar).

El desarrollo se divide por tanto en estas fases

1. Trabajo con el código. Modificar ficheros, añadir nuevos.
2. Prueba del código. La mayor parte de las metodologías de desarrollo
hoy en día, o todas, incluyen una parte de prueba; en casi todos los
casos esta prueba está automatizada e incluye test unitarios (que
prueban características específicas), de integración y de cualquier
otro tipo (calidad de código, existencia y calidad de la
documentacion). 
3. Lanzamiento del producto. Cuando se han incorporado todas las
características que se desean, se lanza el producto. El lanzamiento
del producto, en el caso de web, incluye un *despliegue* (*deploy*)
del mismo, y en el caso de tratarse de otro tipo de aplicación, de un
*empaquetamiento*. Se suele hablar, en todo caso, de *despliegue*
(aunque sea porque las aplicaciones web son más comunes hoy en día que
las aplicaciones de escritorio).
4. Resolución de errores con el código en producción. Si surge algún
error, se trata de resolver sobre la marcha (*hotfix*), por supuesto,
incorporándolo al código que se va a usar para desarrollos posteriores.

En casi todas estas fases puede intervenir, y de hecho lo hace, un
sistema de control de fuentes como git; en muchos casos no se trata de
órdenes de `git`, sino de funciones a las que se puede acceder
directamente desde sitios de gestión como GitHub.

## Organización de un repositorio de git

No hay reglas universales para la organización de un repositorio,
aunque sí reglas sobre como *no* debe hacerse: todo en un sólo
directorio. El repositorio debe estar organizado de forma que cada
persona sólo tenga que *ver* los ficheros con los que tenga que
trabajar y no se *distraiga* con la modificación de ficheros con los
cuales, en principio, no tiene nada que ver; también de forma que no
se sienta tentado en modificar esos mismos ficheros. Vamos a exponer
aquí algunas prácticas comunes,pero en cada caso el sentido común y la
práctica habitual de la empresa deberá imponerse...

### Qué poner en el directorio principal

Cuando se crea un repositorio en GitHub te anima a crear un
`README.md`. Es importante que lo hagas, porque va a ser lo que se
muestre cuando entres a la página principal del proyecto en GitHub y,
además, porque te permite explicar, en pocas palabras, de qué va el
proyecto, cómo instalarlo, qué prerrequisitos tiene, la licencia, y
todo lo demás necesario para navegar por él. 

Otros ficheros que suelen ir en el directorio principal

* `INSTALL` por costumbre, suele contener las intrucciones para
  instalar. También por convención, hoy en día se suele escribir
  usando Markdown convirtiéndose, por tanto, en `INSTALL.md`
  
 * `.gitignore` posiblemente ya conocido, incluye los patrones y
   ficheros que no se deben considerar como parte del repositorio
   
 * `LICENSE` incluye la licencia. También se crea automáticamente en
   caso desde Github en caso de que se haya hecho así. No hay que
   olvidar que también hay que incluir una cabecera en cada fichero
   que indice a qué paquete pertenece y cuál es la licencia.
   
 * `TODO` es una ventana abierta a la colaboració, así como una lista
   para recordarnos a nosotros mismos qué tareas tenemos por delante.
   
 * Otros ficheros de configuración, como `. travis.yml`para el sistema
   de integración continua Travis, `Makefile.PL` o `configure` u otros
   ficheros necesarios para configurar la librería, y ficheros
   similares que haga falta ejecutar o ver al instalar la
   librería. Se aconseja siempre que tengan los nombres que suelan ser
   habituales en el lenguaje de programación, si no el usuario no
   sabrá como usarlos. 
   
 En general se debe tratar de evitar cargar demasiados ficheros, fuera
 de esos, en el directorio principal. Siempre que se pueda, se usará
 un subdirectorio.
 
### Una estructura habitual con directorio de test
 
 Los fuentes del proyecto deben ir en su propio directorio, que
 habitualmente se va a llamar `src`. Algunos lenguajes te van a pedir
 que tengan el nombre de la librería, en cuyo caso se usará el que más
 convenga. Si no se trata de una aplicación sino de una biblioteca, se
 usará `lib`en vez de `src`, como en esta [biblioteca llamada *NodEO*](https://github.com/JJ/nodeo)
 Los tests unitarios irán aparte, en un directorio
 habitualmente llamado `test`. Finalmente, un directorio llamado
 `examples` o `apps` o `scripts` o `bin` o `exe` incluirá ejemplos de uso de la
 biblioteca o diferentes programas que puedan servir para entender
 mejor la aplicación o para ejecutarla directamente.
 
 
### Estructura jerárquica con submódulos
 
 Un repositorio `git` tiene una estructura `plana`, en el sentido que
 se trata de un solo bloque de ficheros que se trata como tal, a
 diferencia de otros sistemas de gestión de fuentes centralizados como
 CVS o Subversion en los que se podía tratar cada subdirectorio como
 si fuera un proyecto independiente. Pero en
 algunos casos hace falta trabajar con proyectos en los cuales haya un
 repositorio que integre el resultado del desarrollo independiente de
 otros, por ejemplo, una aplicación que se desarrolle conjuntamente
 con una librería. En ese caso un repositorio `git` se puede dividir
 en
 [submódulos](http://git-scm.com/book/en/Git-Tools-Submodules),
 que son básicamente repositorios independientes pero que están
 incluidos en una misma estructura de directorios.
 
 Por ejemplo, vamos a incluir el texto de este curso en el repositorio
 de ejemplo, para poder servirlo como una web también:
 

    git submodule add git@github.com:oslugr/curso-git.git curso
Clonar en «curso»...
remote: Reusing existing pack: 14, done.
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 18 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (18/18), 17.26 KiB, done.
Resolving deltas: 100% (4/4), done.


Los submódulos no se clonan directamente al clonar el repositorio. Hay
que dar dos comandos: `git submodule init` y `git submodule update`
dentro del directorio correspondiente; esta última orden servirá para
actualizar submódulos también cada vez que haya un cambio en el repo
del que dependan (y queramos actualizar nuestra copia).

De esta forma, el repositorio queda (parcialmente) con esta estructura
de directorios:

    jmerelo@penny:~/txt/docencia/repo-tutoriales/repo-ejemplo$ tree
.
├── curso
│   ├── LICENSE
│   ├── README.md
│   └── texto
│       ├── ganchos.md
│       ├── GitHub.md
│       └── mas-usos.md


con el subdirectorio `curso` siendo, en realidad, otro repositorio.

Por ejemplo, podíamos tener una estructura que incluyera
subdirectorios para `cliente`(un submódulo) y `servidor` (otro
submódulo). Con ambos se puede trabajar de forma independiente y, de
hecho, *residen* en repositorios independientes, pero puede que, en
caso de empaquetarlos o desplegarlos de alguna forma determinada (por
ejemplo, a un PaaS), queramos hacerlo desde un solo repositorio, como
en este caso.

## Flujos de trabajo con git

Un *flujo de trabajo* es simplemente una forma de organizar las tareas
de programación de forma que se conozca, de antemano, qué tareas van
detrás de qué tareas y cuál es el destino, en cada momento, del código
que se está haciendo. El tener un flujo de trabajo consistente hace
que se eviten conflictos y también que el resultado del trabajo sea
más predecible; también a evitar problemas y a identificarlos
fácilmente. 

El flujo de trabajo básico cuando se trabaja con un sistema de control
de fuentes y lo hace un solo usuario es el siguiente:

1. `git pull`
2. Trabajo con el código; añadir nuevos ficheros fuentes con `git add`
3. `git commit -a -m "[implícito: este commit] [hace] [Tal cosa]" (o
`git -am`, que es lo mismo)
4. `git push`

Fijémonos en el tercer paso, el commit. Primero, conviene hacer siempre `-a`,
es decir, `-all`
por [varias razones](http://git-scm.com/docs/git-commit):

1. Porque examina todos los ficheros que están siendo seguidos, no
sólo los del directorio actual y los que hay por debajo.
2. Porque [hace automáticamente un `git rm` sobre los mismos](http://stackoverflow.com/questions/3541647/git-add-vs-git-commit-a), si es que
ha sido borrados. 

Lo segundo es decidir cuando se hace el *commit*; lo habitual es que se
haga cada vez que se lleve a cabo un cambio significativo, pero ¿qué
es un cambio significativo? Pues un cambio más o menos atómico, que
incluya todos los ficheros afectados por ese cambio y, lo más
importante, que deje, a priori, el código en un estado *sano*. No se
debe hacer commit de un código sintácticamente incorrecto, dejarse a
medias un cambio o, en general, antes de acabar lo que quiera que uno
se propusiera hacer al empezar la sesión de trabajo. No es
imprescindible hacer un `push` por cada commit, pero tampoco estorba
hacerlo, sobre todo por si, simultáneamente, alguien está modificando
el mismo código.  

También conviene escribir `-m` para insertar el mensaje directamente
sin que salga el editor de textos (que puede que no sea nuestro editor
favorito). En el mensaje podemos escribir cualquier cosa, pero hay que
tener en cuenta que lo que escribamos es un predicado cuyo sujeto son
los cambios que hemos hecho. Sobre qué hay que escribir hay
[muchas versiones](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html),
pero conviene que el mensaje sea informativo, hable de por qués y de
comos más que de qués (no se puede decir "inserta una función", eso ya
se ve en el código, sino por qué se inserta esa función) y se aconseja
también un formato similar al siguiente

    Hace tal cosa arreglando el error en el issue #666

    Siguiendo la sugerencia de @foodev hemos usado el algoritmo
    Vicentico para resolver ese error y ha quedado monísimo. 
	
Este formato se denomina `50+72` y consiste en usar una primera línea
con 50 caracteres (justos, en este caso) que incluya una explicación
extendida que esté formateada en líneas de 72 caracteres. Esto es
difícil de hacer desde la línea de órdenes, así que tienes dos
opciones: usar un *script* que formatee este mensaje, o bien
configurar tu editor de forma que use ese formato. 

El mensaje de *commit* también admite markdown y de hecho se
formateará de esa forma en GitHub (posiblemente también en otros
repos) y dentro del mismo admite ciertos atajos como referirse a una
tarea o *issue* por el número de la misma o a un desarrollador por el
handle. En todo caso, se formatee o no de esa forma, es informativo
saber por qué hace lo que hace.

En cuanto al `push` es un evento diferente que el `commit` y hace más
cosas, por lo que no debe verse como algo automático tras el
mismo. Un `commit` es una unidad mínima de cambio, un `push` envía los
contenidos al repo remoto y activa una serie de actividades, como la
integración continua, comprobación de código y otra serie de cosas
interesantes. Además, hasta que no hacemos `push` no comparamos
nuestro código con el que está en `HEAD`, que en ese momento puede
estar más adelante o más atrás. Si tienes miedo de provocar un
conflicto o de que te lo provoque, no hagas un pull hasta estar seguro
de que el código no rompe los tests automáticos y hasta que estés
seguro de poder resolver los conflictos que ocurran.  ¿Cómo se pueden
resolver estos conflictos? Lo veremos a continuación. 




## Ramas

## Los misterios del rebase

## Quién hizo qué

