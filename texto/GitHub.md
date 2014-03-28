# Usando `git` como los profesionales: GitHub

## Por qué GitHub

GitHub se ha convertido en el sitio más popular, a pesar de encontrarse entre una cantidad de sitios que alojan también proyectos y permiten usar Git como Gitorious, BitBucket o incluso el venerable [SourceForge](http://sourceforge.net); [Gitorious](https://gitorious.org/) tiene la ventaja de que está a su vez basado en software libre, por lo que te puedes instalar tu propia copia del repositorio bajo tu control. Sea con este sotware o con [GitLab](https://www.gitlab.com/) te puedes hacer tu propia instalación de git si tienes disponible un servidor para ello. Evidentemente, para trabajar con grandes proyectos privados son una buena opción y lo más aceptable.

Sin embargo, hay buenas razones para usar GitHub. Aparte del uso de git, GitHub en realidad funciona como una comunidad de programadores que te permite interaccionar muy fácilmente con otros programadores que usen las mismas herramientas que uno. Ninguno de los otros repositorios tiene esas características; aunque todos tienen ciertas capacidades *sociales*, lo cierto es que la mayoría de los programadores de software libre usan hoy GitHub. De hecho, GitHub con sus métricas, características de *gamificación* (poner estrellas a proyectos, por ejemplo), continuo desarrollo, enganche a plataformas de programación diversas y cliente móvil es hoy en día la mejor opción para desarrollar software libre (y novelas y [cursos de Git](http://github.com/JJ/curso-git)).

Adicionalmente, GitHub se usa como repositorio por defecto para módulos de diferentes lenguajes de programación; por ejemplo, `npm`, el gestor de módulos de Node, lo usa para alojar y descargar las fuentes; otros marcos como Joomla lo usan también para definir sus plugins. Incluso GitHub se incluye ya en flujos de trabajo de ciertos entornos, como [la (futura o pasada) revista científica Push](http://push.cwcon.org). 

En resumen, GitHub es la primera, segunda y tercera mejor opción de un
programador de software libre a la hora de alojar sus proyectos. La
cuarta sería gitorious, por el hecho de que efectivamente todo el
software que usa está liberado y la quinta Bitbucket. Más atrás
estarían el resto. En este curso veremos principalmente, por esa
razón, GitHub y sus características específicas, algunas de las cuales
se han venido usando ya el resto del curso.  

## Repositorios públicos y privados

Por omisión, los repositorios de GitHub son públicos. Para conseguir
un repositorio privado hay que hacer una de dos cosas

* Pagar. Por 7 dólares al mes puedes tener
  [cinco repositorios privados](https://github.com/pricing). 
  
* Conseguir [una cuenta para educación](https://education.github.com/)
  que permite, generalmente de forma limitada, tener un número
  determinado de cuentas gratuitas.
  
En realidad, las cuentas privadas son útiles para empresas que quieran
desarrollar sus propias aplicaciones en privado; para software libre,
aplicaciones que se creen para un proyecto las cuentas tienen espacio
de almacenamiento ilimitado y un número ilimitado de colaboradores,
por lo que no hace falta adquirir una cuenta ni tener un repositorio
privado. 

## El GitHub *social*

En realidad, GitHub es una red social de gente que hace cosas y
escribe texto como este o aplicaciones en diferentes lenguajes de
programación. Cada usuario tiene
[un perfil](https://github.com/oslugr) y en él puede contar cosas como
dónde se encuentra, su web y poco más. Lo que importa es lo que se
hace, que aparece justo al lado del logo. GitHub usa
[Gravatar](http://gravatar.com) para las fotos de perfil, por lo que
tendrás que darte de alta en ese servicio *con la misma dirección de
email que uses en GH* para que aparezca tu avatar junto a tus
contribuciones. Se puede seguir la
[actividad](https://github.com/oslugr?tab=activity) de un usuario,
pero también se puede ir un paso más allá y pulsar el botón de
*Follow* con lo que, a entrar en la
[página principal de GitHub](http://github.com) se te mostrará, junto
con la actividad propia, la de esta persona.

El componente *social* también se ve en repositorios específicos: los
repositorios, como
[este de ejemplo del curso](https://github.com/oslugr/repo-ejemplo),
se pueden *vigilar* (*Watch*) y también poner una especie de "Me
gusta", *Star*, uno al lado del otro. Finalmente, se puede hacer un
*Fork* del repositorio, lo que copia el contenido completo del
repositorio al propio y permite trabajar con él; equivale a una *rama*
tal como la que hemos visto anteriormente. Este *fork* respeta la
autoría original que sigue apareciendo en todos los *commits* que se
hayan hecho originalmente, pero permite añadir uno sus propias
modificaciones *sin que el autor original tenga que aprobarlas*. 

GitHub también permite comentar a diferentes niveles: se puede
comentar un *commit*, se pueden comentar líneas de código y finalmente
se pueden hacer solicitudes y comentarios a un repo completo usando
[*issues* o solicitudes](https://github.com/oslugr/repo-ejemplo/issues)
(*to have an issue* significa literalmente tener un *asunto* o
*problema*). Todas estas formas de interacción permiten tener una vida
*social* más o menos rica y que haya muchas formas posibles de
interaccionar con los autores de un proyecto y por supuesto también de
que esos autores aumenten su *karma* a base de las conexiones,
estrellas que reciban sus repositorios y comentarios, así como los
asuntos resueltos.



## Cómo usar los hooks

## Algunos *hooks* interesantes: sistemas de integración continua

## Creando páginas para GitHub pages
