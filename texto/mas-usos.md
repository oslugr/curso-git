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



## Organización de un repositorio de git

No hay reglas universales para la organización de un repositorio,
aunque sí reglas sobre como *no* debe hacerse: todo en un sólo
directorio. El repositorio debe estar organizado de forma que cada
persona sólo tenga que *ver* los ficheros con los que tenga que
trabajar y no se *distraiga* con la modificación de ficheros con los
cuales, en principio, no tiene nada que ver; también de forma que no
se sienta tentado en modificar esos mismos ficheros. 

## Flujos de trabajo con git

Un *flujo de trabajo* es simplemente una forma de organizar las tareas
de programación de forma que se conozca, de antemano, qué tareas van
detrás de qué tareas y cuál es el destino, en cada momento, del código
que se está haciendo. El tener un flujo de trabajo consistente hace
que se eviten conflictos y también que el resultado del trabajo sea
más predecible; también a evitar problemas y a identificarlos
fácilmente. 

El flujo de trabajo básico cuando se trabaja con un sistema de control
de fuentes es el siguiente:
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

Lo segundo es decidir cuando se hace el commit; lo habitual es que se
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
los cambios que hemos hecho. 

## Ramas

## Los misterios del rebase

## Quién hizo qué

