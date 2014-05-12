# Usando `git` como los profesionales: GitHub

## Objetivos

* Conocer las características generales de los repositorios públicos de GitHub
* Conocer las características específicas de GitHub
* Aprovechar esas características específicas en el trabajo de desarrollo.

## Por qué GitHub

GitHub se ha convertido en el sitio más popular, a pesar de encontrarse entre una cantidad de sitios que alojan también proyectos y permiten usar Git como Gitorious, BitBucket o incluso el venerable [SourceForge](http://sourceforge.net); [Gitorious](https://gitorious.org/) tiene la ventaja de que está a su vez basado en software libre, por lo que te puedes instalar tu propia copia del repositorio bajo tu control. Sea con este sotware o con [GitLab](https://www.gitlab.com/) te puedes hacer tu propia instalación de git si tienes disponible un servidor para ello. Evidentemente, para trabajar con grandes proyectos privados son una buena opción y lo más aceptable.

Sin embargo, hay buenas razones para usar GitHub. Aparte del uso de git, GitHub en realidad funciona como una comunidad de programadores que te permite interaccionar muy fácilmente con otros programadores que usen las mismas herramientas que uno. Ninguno de los otros repositorios tiene esas características; aunque todos tienen ciertas capacidades *sociales*, lo cierto es que la mayoría de los programadores de software libre usan hoy GitHub. De hecho, GitHub con sus métricas, características de *gamificación* (poner estrellas a proyectos, por ejemplo), continuo desarrollo, enganche a plataformas de programación diversas y cliente móvil es hoy en día la mejor opción para desarrollar software libre (y novelas y [cursos de Git](http://github.com/JJ/curso-git)).

Adicionalmente, GitHub se usa como repositorio por defecto para
módulos de diferentes lenguajes de programación; por ejemplo, `npm`,
el gestor de módulos de Node, lo usa para alojar y descargar las
fuentes; otros marcos como Joomla lo usan también para definir sus
plugins. Incluso GitHub se incluye ya en flujos de trabajo de ciertos
entornos, como
[la (futura o pasada) revista científica Push](http://push.cwcon.org).  

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

GitHub es una red social de gente que hace cosas y
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
*Follow* con lo que, al entrar en la
[página principal de GitHub](http://github.com) se te mostrará, junto
con la actividad propia, la de esta persona. Una persona puede ser
también añadida a un repositorio, lo que le dará privilegios para
realizar todo tipo de acciones sobre él. Conviene usar esto con
moderación y sólo cuando se trate de una persona ya involucrada en el
proyecto. 

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
modificaciones *sin que el autor original tenga que aprobarlas*. Los
*pull requests* permiten colaboración esporádica, ya que las
modificaciones que se soliciten pueden aprobarse o no por parte del
autor principal del repositorio; la persona que las haga, sin embargo,
no tiene por qué estar añadida como colaborador permanente al mismo. 

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
*issues* resueltos. Los *issues* se agrupan en *milestones* o hitos,
que son simplemente grupos de temas que deben ser resueltos antes de
pasar a otra fase del desarrollo. Agrupar los *issues* en hitos
permite ver el progreso del mismo, ya que te va mostrando cuál es el
grado de terminación de dicho hito. Los hitos, además, pueden fecharse
con lo que se puede ver si se ha pasado uno de fecha o no. 

Finalmente, los usuarios se pueden agrupar en [organizaciones](https://help.github.com/articles/creating-a-new-organization-account--2). Una
organización es en muchos aspectos similar a un usuario; tiene las
mismas limitaciones y las mismas ventajas, pero en una organización se
definen *equipos* y los permisos para trabajar por repositorios se
hacen usando estos *equipos*; cada repositorio puede tener uno o más
equipos con diferentes niveles de privilegios y el repositorio en sí
tendrá también un equipo que será el que pueda realizar ciertas
acciones sobre el mismo. Generalmente se crea un equipo por
repositorio, pero puede organizarse de cualquier otra forma.

Cuando uno es añadido a un equipo de una organización, se convierte en
otra "personalidad" que te permite, por ejemplo, hacer *fork* como
miembro de tal organización. Para adoptar esa personalidad se
selecciona el nombre de la organización de un menú que está en el
panel de control de [GitHub (página principal)](https://github.com) justo debajo del
logotipo del octocat. 

En resumen, la facilidad que tiene GitHub para manejar todo tipo de
situaciones de desarrollo y la *gamificación* y *socialización* de la
experiencia de desarrollo es lo que ha hecho que hoy en día tenga
tanto éxito hasta el punto de que el perfil de uno en GitHub es su
mejor carta de presentación a la hora de conseguir un trabajo en
desarrollo y programación. 

## Creando páginas para GitHub pages

Una de las partes interesantes de GitHub y en lo que coincide con
otros más clásicos como SourceForge es en la posibilidad de publicar
páginas relacionadas con el proyecto o, para el caso, sobre lo que uno
quiera. A diferencia de otros sitios, son páginas estáticas (lo que
permite, imagino, ser más rápido y eficiente a la hora de servirlas).

También se pueden crear muy fácilmente: *Settings*-> se baja a la
página donde pone "GitHub Pages", y se pulsa en *Automatic Page
Generator* que te permitirá elegir entre unos pocos (la verdad, no hay
muchos) *temas* el que más te guste.

Lo que hace este generador automático es lo siguiente:

- Generar una rama `gh-pages` de tu repositorio principal
- A partir del fichero `README.md` del directorio principal de tu
   proyecto, genera un fichero `index.html` usando la plantilla
   seleccionada
- Genera un dominio `usuario.github.io/proyecto` desde el cual se
   puede acceder a  las páginas publicadas
   
El generador automático sólo funciona una vez. A partir de ese
momento, sólo se reflejarán en el sitio general los cambios que se
hagan desde la rama `gh-pages`. Se puede trabajar directamente con
ella o bien usar algún tipo de `hook` para generar contenido a partir
de la rama `master` y copiarlo a esa rama. 

Tampoco es obligatorio usar el generador, que está basado en
[Jekyll](http://jekyllrb.com/), un motor de plantillas y generador
estático de páginas basado en Markdown u otros lenguajes
simplificados. Jekyll es muy potente y te permite hasta
[montar un blog](http://jekyllrb.com/docs/migrations/), pero no nos
vamos a meter en el funcionamiento del mismo. Tampoco es necesario;
para crear una página de proyecto sólo hay que hacer dos pasos:

``` 
    git checkout -b gh-pages
    touch index.html
	git add index.html
```

(Aquí tendría que editarse el fichero HTML y meter algo, y a
continuación)

```
    git commit -am "Creada página del sitio"
	git push origin gh-pages
```

Con esto se transmite la rama al repositorio y automáticamente se
publica.

Adicionalmente a las páginas de proyecto, cada organización y cada
usuario puede crear también su página. Un usuario `nombredeusuario`
tendrá una página `nombredeusuario.github.io` de la que "colgarán" el
resto de las páginas (aunque el realidad se tratará de repositorios
diferentes, y sólo estarán las que se hayan generado, claro). Para
crear tanto una página de usuario como de organización simplemente se
crea el repositorio y se pone el contenido en la rama principal, la
`master`. Al hacer push se publica automáticamente, como la de la
[organización que se ha creado para este curso](http://curso-git-2014.github.io/)


## Cómo usar los hooks

Los *hooks* o *ganchos* son eventos que se activan cuando se produce algún tipo de acción por parte de git. En general, se usan para integrar el sistema de gestión de fuentes de git con otra serie de sistemas, principalmente de [integración continua](http://es.wikipedia.org/wiki/Integraci%C3%B3n_continua) o [entrega continua](http://en.wikipedia.org/wiki/Continuous_delivery) o, en general, cualquier tipo de sistema de notificaciones o de trabajo en grupo.

GitHub puede integrar cualquier tipo de servicio que acepte una petición REST con una serie de características (esencialmente, datos sobre el repositorio y sobre el último commit), pero tiene ya una serie de servicios, casi un centenar, configurables directamente desde el panel de control yendo a *Settings* -> *Webhooks & Services* -> *Configure services*. Todos los servicios se activan cuando se hace un push a GitHub. Evidentemente, en local no se enteran, salvo que los configuremos explícitamente como vamos a ver en el tema siguiente. 

Vamos a dividir los servicios que hay en varios grupos:

- Integración continua. Servicios como TravisCI, CircleCI, Jenkins o
  Shippable. Los tres primeros se pueden configurar directamente desde
  GH, para el último hay que entrar en [su web](http://shippable.com)
  y activar el repositorio que haga falta. Estos servicios realizan
  una serie de tests o generación de código sobre el proyecto y dan un
  resultado indicando qué tests se han pasado o no. Para indicar qué
  tests se hacen y los parámetros del repositorio, cada uno usa un
  formato diferente, aunque son habituales los ficheros de formato
  YAML o XML. En
  [el repo de ejemplo](http://github.com/oslugr/repo-ejemplo) se han
  activado Travis y Shippable, y en el directorio principal se pueden
  ver los ficheros de configuración (del mismo nombre que el sitio). 
- Servicios de mensajería diversos, que envían mensajes cuando sucede
  algo. Entre estos últimos está [Twitter](http://twitter.com), que se
  puede configurar para que se cree un tweet con el mensaje del commit
  cada vez que se haga uno. Puede ser bastante útil, si se usa este
  sitio, para mantenerte al día de la actividad de un grupo de
  trabajo. También hay otros servicios como Jabber o Yammer o
  comerciales como Amazon SNS.  
- Entrega continua: a veces integrados con los de, valga la
  redundancia, integración continua, pero que permiten directamente,
  cuando se hace un push sobre una rama dterminada, se despliegue en
  el sitio definitivo. Servicios como Azure lo permiten, pero también
  [CodeShip](http://codeship.io) o
  [Jenkins](http://lkrnac.net/blog/2014/03/16/continuous-delivery/). Generalmente
  en este caso hay que configurar algún tipo de *secret* o *clave* que
  permita a GitHub acceder al sitio y depositar la *carga* que,
  inmediatamente, estará disponible. De hecho, es muy fácil trabajar
  con esto
  [directamente desde el editor como Eclipse](http://java.dzone.com/articles/trigger-continuous-delivery) 
- Sistemas de trabajo en grupo, que integran GitHub con los sistemas
  que tengan de asignación de tareas, de resolución de incidencias
  incluidas por parte de clientes. Por ejemplo, Basecamp, Bugzilla o
  Zendesk. De hecho, el propio GitHub integra un sistema de
  incidencias que se puede usar fácilmente.  
- Análisis del código como CodeClimate (que analiza una serie de
  parámetros del código), Depending (que analiza dependencias en PHP)
  o David-DM (que analiza dependencias para nodejs). 

Lo interesante es que se puede trabajar con la mayoría de estos sistemas de forma gratuita, aunque algunos tienen un modelo *freemium* que te cobra a partir de un nivel determinado de uso (lo que es natural, si no no podrían ofrecértelo de forma grauita). Además, integra la mayor parte de los sistemas que se usan habitualmente en la industria del software. 

## Algunos *hooks* interesantes: sistemas de integración continua

GitHub resulta ideal para trabajar con cualquier sistema de
integración continua, sea alojado o propio. Los sistemas de
integración continua funcionan de la forma siguiente: 

- Provisionan una máquina virtual con unas características
  determinadas para ejecutar pruebas o compilar código.  
- Instalan el software necesario para llevar a cabo dichas pruebas.
- Ejecutan las pruebas, creando finalmente un informe que indique
  cuantas han fallado o acertado. 
- Crear un *artefacto*, que puede ir desde un fichero con el informe
  en un formato estándar (suele ser XUnit o JUnit) hasta el ejecutable
  que se podrá descargar directamente del sitio; esto último puede
  incluir también su despliegue en la *nube*, un IaaS (Infraestructure
  as a Service) o PaaS (Platform as a Service) en caso de que haya
  pasado todos los tests satisfactoriamente. 

La integración continua forma parte de una metodología de [desarrollo basado en test o guiado por pruebas](http://es.wikipedia.org/wiki/Desarrollo_guiado_por_pruebas) que consiste en crear primero las pruebas que tiene que pasar un código antes de, efectivamente, escribir tal código. Las pruebas son tests unitarios y también de integración, que prueban las capas de la aplicación a diferentes niveles (por ejemplo, acceso a datos, procesamiento de los datos, UI). Todos los lenguajes de programación moderno incluyen una aplicación que crea un protocolo para llevar a cabo los test e informar del resultado y estos sistemas van desde el humilde Makefile que se usa en diferentes lenguajes compilados hasta el complejo Maven, pasando por sistemas como los tests de Perl o los Rakefiles de Ruby. En cualquier caso, cada lenguaje suele tener una forma estándar de pasar los tests (`make test`, `npm test` o `mocha`) y los sistemas de integración continua hacen muy simple trabajar con estos tests estándar, pero también son flexibles en el sentido que se puede adaptar a todo tipo de programa.

Veamos como trabajar con [Travis](http://travis-ci.com). Se hace siguiendo estos pasos

1. [Darse de alta en Travis CI](http://docs.travis-ci.com/user/getting-started/) usando la propia cuenta de GitHub
2. Activar el *hook* en [tu perfil de Travis](https://travis-ci.org/profile). 
3. Se añade el fichero `.travis.yml` a tu repositorio. Este dependerá del lenguaje que se esté usando, aunque si lo único que quieres es comprobar la ortografía de tus documentos, lo puedes hacer [como en el repositorio ejemplo](https://github.com/oslugr/repo-ejemplo/blob/master/.travis.yml)
4. Hacer push.

La mayoría de estos repositorios suelen usar un fichero en formato estándar, YAML, XML o JSON. Veamos qué hace el fichero que hemos usado para el repo ejemplo:

```
branches:
  except:
    - gh-pages
language: C
compiler:
  - gcc
before_install:
  - sudo apt-get install aspell-es 
script: OUTPUT=`cat README.md | aspell list -d es -p ./.aspell.es.pws`; if [ -n "$OUTPUT" ]; then echo $OUTPUT; exit 1; fi
```

La estructura de YAML permite expresar vectores y matrices asociativas fácilmente. En general, nos vamos a encontrar con algo del tipo `variable: valor` que será una clave y el valor correspondiente; el valor, a su vez, puede incluir otras estructuras similares. Por ejemplo, la primera

```
branches:
  except:
    - gh-pages
```

es una clave, `branches`, que incluye otra clave, `except`, que a su vez apunta a un vector (diferentes valores precedidos por -) con las ramas que vamos a excluir. En este caso, `gh-pages`, la de las páginas. Si hubiera otra rama a excluir, iría de esta forma

```
branches:
  except:
    - gh-pages
	- a-excluir
```

es decir, como un array de dos componentes. Esto hará que, sobre nuestro repositorio, se prueben todas las ramas, inclusive por supuesto la máster. A continuación expresamos el lenguaje que se va a usar; Travis no admite cualquier lenguaje, pero algunos como C, Perl o nodejs los acepta sin problemas. Como hay varios compiladores posibles, a continuación le decimos qué compilador se va a usar (en realidad, no se usa ninguno). En otros lenguajes habría que decir qué intérprete o qué versión; estas claves son específicas del lenguaje.

```
before_install:
  - sudo apt-get install aspell-es 
script: OUTPUT=`cat README.md | aspell list -d es -p ./.aspell.es.pws`; if [ -n "$OUTPUT" ]; then echo $OUTPUT; exit 1; fi
```

Como lo único que vamos a hacer en este caso es comprobar la ortografía del texto del fichero `README.md`, instalamos con `apt-get` (herramienta estándar para Linux) un diccionario en español; este instalará todas las dependencias a su vez.  Finalmente, la orden marcada `script` es la que lleva a cabo la comprobación. Para un programa normal sería suficiente hacer `make test` (y definir las dependencias para este objetivo, claro). No nos preocupemos mucho por lo que es, sino por lo que hace: si hay alguna palabra que no pase el test ortográfico, [fallará y enviará un mensaje de correo electrónico a la persona que haya hecho un commit indicándolo](https://travis-ci.org/oslugr/repo-ejemplo/builds/22375300). Si lo pasa sin problemas, [también enviará el mensaje indicando que todo está correcto]( https://travis-ci.org/oslugr/repo-ejemplo/builds/22377799). Este tipo de cosas resulta útil sólo por el hecho de que se ejecuten automáticamente, pero pueden servir también para hacer despliegues continuos.

Travis también proporciona un *badge* que puedes incluir en tu repositorio para indicar si pasa los tests o no, que puedes incluir en tu fichero `README.md`(o donde quieras) con este código

```
[![Build Status](https://travis-ci.org/oslugr/repo-ejemplo.svg?branch=master)](https://travis-ci.org/oslugr/repo-ejemplo)
```

sustituyendo el nombre de usuario y el nombre del repo por el correspondiente, claro. Este código está escrito en MarkDown, y GitHub lo interpretará directamente sin problemas, aunque lo mejor es que pinches en la imagen que aparece arriba a la derecha que te dará el código correspondiente.

## Cliente de GitHub

GitHub también mantiene un [cliente de GitHub](https://github.com/github/hub), escrito en Ruby y llamado `hub`, que se puede usar para sustituir a `git` o por sí mismo. En realidad, es como `git` salvo que tiene ya definidos por omisión una serie de características específicas de GitHub, como los nombres de los repositorios o los usuarios de los mismos. Tras [instalarlo](http://hub.github.com/) puedes usarlo, por ejemplo, para clonar el repo de ejemplo usado aquí con `hub clone oslugr/repo-ejemplo` en vez de usar el camino completo a git; el formato sería siempre `usuario/nombre-del-repo`. Más órdenes que añade a git (y que se pueden usar directamente desde git si se usa, como se indica en las instrucciones, git como un alias de `hub`):

* `hub browse`: abre un navegador en la página del repositorio
  correspondiente. Por ejemplo `hub browse -- issues` lo abriría en la
  página correspondiente a las solicitudes de ese proyecto. 
* `hub fork`: una vez clonado un repositorio de otro usuario, no hace falta hacer *fork* desde la web, se puede hacer directamente desde el repo. Se crea un origen remoto con el nombre de tu usuario, al que se puede hacer *push* de la forma normal. Desde la misma línea de órdenes se puede hacer un *pull request* al repositorio original también. 
* Como usuario puedes aplicar también los *pull requests* desde línea de órdenes.
* `hub compare` permite comparar entre diferentes tags o versiones o ramas.

En general, ya que se tiene GitHub, conviene usar este cliente, sea o
no con un alias a `git`. Por lo menos su uso es conveniente. 

## Listo para el lanzamiento: publicación en GitHub

GitHub, como cualquier otro repositorio git, permite usar una rama
específica para depositar las versiones descargables; una forma de
hacerlo, por ejemplo, es usar la rama `gh-pages` para no mezclarlo con
el resto de los ficheros que están en el repositorio y, por tanto,
versionados. Sin embargo, no es una buena idea poner ficheros binarios
bajo control de git, porque es muy fácil provocar conflictos con ellos
y no tan fácil resolverlos (o es un fichero o es otro, los algoritmos
de diferencias de texto no trabajan sobre ficheros que no sean
binarios); además, en general, estos ficheros se generan a partir del
fuente de una forma más o menos automática: usando `Makefiles`, por
ejemplo, en C, o en general compilando; si se trata de paquetes, cada
lenguaje tiene mecanismos específicos para crearlos a partir de los
fuentes, por lo tanto no es necesario colocar tales ficheros en el
repositorio. Por eso es mejor colocarlos *fuera* del repositorio, y es
lo que hace GitHub, en un apartado llamado *archivos*. 

Hacer un lanzamiento de un producto es fácil en GitHub: simplemente se crea una
etiqueta como se ha visto anteriormente, con `git tag`. Por ejemplo,
[este es el fichero correspondiente a la etiqueta `v0.0.1` que se definió en el repositorio de ejemplo](https://github.com/oslugr/repo-ejemplo/releases/tag/v0.0.1). Al
pinchar en
[*Releases*](https://github.com/oslugr/repo-ejemplo/releases) te
aparecen las versiones que ya has creado o un botón con *Draft a new
release* para crear una nueva. 

Desde este interfaz web se puede añadir alguna información más que
desde la línea de comandos: se puede crear la etiqueta si no existe y
se pueden añadir imágenes, ficheros binarios generados de cualquier
otra forma (o automáticamente) y, en general, lo que uno
desee. También se puede marcar como *pre-release* y
[darle un título como a las versiones de Ubuntu, con animalitos o nombres de días de la semana o lo que sea](https://github.com/oslugr/repo-ejemplo/releases/tag/v0.0.3).   

En general, si no se usa ningún repositorio de módulos o aplicaciones
para publicar la aplicación, o simplemente se quiere publicar junto
con los fuentes, manuales y lo que se desee, es conveniente usar esta
característica de GitHub para mantener un archivo de versiones
descargables de la misma y también para que puedan acceder a ella
fácilmente quienes no quieran usar simplemente `git` para
descargársela. 

>Vais a decir que ya podían instalarse `git` y demás herramientas
> necesarias para compilar o ejecutar la aplicación, pero en muchos
> casos no tiene por qué ser fácil o factible; no se va a instalar uno
> un compilador de fortran simplemente para compilar una aplicación
> nuestra, por ejemplo.  


