# *Hooks*: ejecutando código tras una orden git

## Objetivos

* Entender el concepto de *fontanería* y *loza*
* Entender el concepto de *hooks* o *puntos de enganche*
* Entender las órdenes menos usuales de git usadas desde los *hooks*
* Saber adaptar *hooks* para una labor determinada
 
## Viendo las cañerías: estructura de un repositorio `git`

Cuando se crea por primera vez un repositorio veremos que aparecen misteriosamente una serie de ficheros con esta estructura dentro del directorio `.git`.

![Estructura básica de un repositorio git](img/tree-git.png)

`branches` lo dejamos de lado porque ya no se usa (aunque por alguna razón se sigue creando). `config`, `HEAD`, `refs` y `objects` son ficheros o directorios que almacenan información dinámica. 


## Comandos de alto y bajo nivel: *fontanería* y *loza*

Para entendernos, todas las órdenes que hemos usado hasta ahora son *loza*. Es decir, es el *interfaz* del usuario de toda la instalación de fontanería que lleva a cabo realmente la labor de quitar de enmedio lo que uno depositao en las instalaciones sanitarias. Pero por debajo de la loza y pegado a ella, están las cañerías y toda la instalación de fontanería. 

Los comandos de `git` se dividen en [dos tipos](http://git-scm.com/book/ch9-1.html): *fontanería* o *cañería*, que son comandos que *generalmente* no ve el usuario y *loza*, que son los que ve y los que usa. Sin embargo, este capítulo trata realmente de esa fontanería, porque van a ser una serie de órdenes que se van a llevar a cabo *después* de que se ejecuten las órdenes de *loza*, o, quizás *dentro* de esas órdenes de loza.

Pero antes de usar esas órdenes de fontanería tenemos que entender cómo son las cañerías. Una parte se ha visto anteriormente: el *index* o índice que contiene todos los objetos a los que `git` debe prestarles atención a la hora de hacer un commit. Pero existen además [los objetos y las referencias](http://teohm.com/blog/2011/05/30/learning-git-internals-by-example/).

Los *objetos* son, en general, información que está almacenada en el repositorio. Incluyen, por supuesto, los ficheros que almacenamos en el mismo, pero también los mensajes de commit, las etiquetas y los *árboles*. Los ficheros almacenados están *divididos*: el *contenido* del fichero se almacena en un *blob* y el nombre del fichero se almacena en el árbol. Hay, pues, cuatro tipos de objetos: *blob*, *tree*, *commit* y *tag*. 

La orden `ls-tree` nos permite ver qué tipos de objetos tenemos almacenados y sus códigos SHA1, que son los nombres de ficheros calculados a partir del contenido del mismo. Aunque todos están almacenados en el directorio `.git/objects`, esta orden nos permite ver también de qué tipo son:

```
~/txt/docencia/repo-tutoriales/repo-ejemplo<master>$ git ls-tree HEAD
100644 blob a6f69e4284566cd84272c6a4e4996f64643afbea	.aspell.es.pws
100644 blob a72b52ebe897796e4a289cf95ff6270e04637aad	.gitignore
100644 blob cc5411b5557f43c7ba2f37ad31f8dc34cccda075	.gitmodules
100644 blob 4e7b6c1b5a6cb3a962ea05874d10c943c1923f39	.travis.yml
100644 blob d5445e7ac8422305d107420de4ab8e1ee6227cca	LICENSE
100644 blob d1913ebe4d9e457be617ee0e786fc8c30a237902	Procfile
100644 blob c5badda0c484c989e958ea4e27dfe11d69f3c8ef	README.md
160000 commit fa8b7521968bddf235285347775b21dd121b5c11	curso
100644 blob f8c35adaf57066d4329737c8f6ec7ce6179cc221	package.json
100644 blob 08827778af94ea4c0ddbc28194ded3081e7b0f87	shippable.yml
040000 tree 39da6b155c821af1e6a304daca9b66efb1ac651f	test
100644 blob 94f151d9ef9340c81989b0c3fa8c517c068e1864	web.js
```
En este caso tenemos objetos de tres tipos: blob, commit y tree. a `ls-tree` se le pasa un *tree-ish*, es decir, algo que apunte a dónde esté almacenado un árbol pero, para no preocuparnos de qué se trata esto, usaremos simplemente HEAD, que apunta como sabéis a la punta de la rama en la que nos encontramos ahora mismo. También  nos da el SHA1 de 40 caracteres que representa cada uno de los ficheros. Si editamos un fichero como el README.md, tras hacer el commit tendrá esta apariencia:

```
~/txt/docencia/repo-tutoriales/repo-ejemplo<master>$ git ls-tree HEAD100644 blob a6f69e4284566cd84272c6a4e4996f64643afbea	.aspell.es.pws
[...]
100644 blob da5b5121adb42e990b9e990c3edb962ef99cb76a	README.md
```

Como vemos, ha cambiado el SHA1. Pero ls-tree va más allá y te puede mostrar también cuál es el estado del repositorio hace varios commits. Por ejemplo, podemos usar `HEAD^` para referirnos al commit anterior y `git ls-tree HEAD^` nos devolvería exactamente el mismo estado en el que estaba antes de hacer la modificación a README.md. De hecho, podemos usar también la abreviatura del commit de esta forma `git ls-tree 5be23bb`, siendo este último una parte del SHA1 (o hash) del último commit; nos devolvería el último resultado. 

Pero podemos ir todavía más profundamente dentro de las tuberías. `ls-tree` sólo lista los objetos que ya forman parte del árbol, del principal o de alguno de los secundarios. Puede que necesitemos acceder a aquellos objetos que se han añadido al índice, pero todavía no han pasado a ningún árbol. Para eso usamos `ls-files`. Tras añadir un fichero que está en un subdirectorio `views` con `add`, podemos hacer:

```
git ls-files --stage
100644 a6f69e4284566cd84272c6a4e4996f64643afbea 0	.aspell.es.pws
100644 a72b52ebe897796e4a289cf95ff6270e04637aad 0	.gitignore
100644 cc5411b5557f43c7ba2f37ad31f8dc34cccda075 0	.gitmodules
100644 4e7b6c1b5a6cb3a962ea05874d10c943c1923f39 0	.travis.yml
100644 d5445e7ac8422305d107420de4ab8e1ee6227cca 0	LICENSE
100644 d1913ebe4d9e457be617ee0e786fc8c30a237902 0	Procfile
100644 da5b5121adb42e990b9e990c3edb962ef99cb76a 0	README.md
160000 fa8b7521968bddf235285347775b21dd121b5c11 0	curso
100644 f8c35adaf57066d4329737c8f6ec7ce6179cc221 0	package.json
100644 08827778af94ea4c0ddbc28194ded3081e7b0f87 0	shippable.yml
100644 9920d80438d42e3b0a6924a0fcace2d53a6af602 0	test/route.js
100644 36cc059186e7cb247eaf7bfd6a318be6cffb9ea3 0	views/layout.jade
100644 94f151d9ef9340c81989b0c3fa8c517c068e1864 0	web.js
```
Que nos devuelve, en penúltimo lugar, un fichero que todavía no ha pasado al árbol. Evidentemente, tras el commit:

```
~/txt/docencia/repo-tutoriales/repo-ejemplo<master>$ git ls-tree HEAD
[...]
040000 tree fd3846c0d6089437598004131184c61aea2b6514	views
```

Este listado nos muestra el nuevo objeto de tipo `tree` que se ha creado y nos da su SHA1, que podemos usar para examinarlo con `ls-tree`


```
~/txt/docencia/repo-tutoriales/repo-ejemplo<master>$ git ls-tree fd3846c
100644 blob 36cc059186e7cb247eaf7bfd6a318be6cffb9ea3	layout.jade
```

que, si queremos ver en una vista más normal, hacemos lo mismo con `ls-file`

```
~/txt/docencia/repo-tutoriales/repo-ejemplo<master>$ git ls-files views
views/layout.jade
```

Hay un tercer comando, `cat-file`, que muestra el contenido de un objeto, en general. Por ejemplo, en este caso, para listar el contenido de un objeto de tipo `tree`

```
~/txt/docencia/repo-tutoriales/repo-ejemplo<master>$ git cat-file -p fd3846c
100644 blob 36cc059186e7cb247eaf7bfd6a318be6cffb9ea3	layout.jade
```

Hay 
## Concepto de *hooks*

## Programando un *hook* básico

## Algunos *hooks* útiles explicados
