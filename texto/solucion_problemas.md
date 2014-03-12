##Solución de problemas con git
Solución de conflictos. Borrado de commits. Editado de la historia.

## Resolviendo conflictos en `git`
	
Normalmente los conflictos suceden cuando dos usuarios han modificado
    la misma línea, o bien cuando han modificado un fichero binario;
    por eso los ficheros binarios **no** deben estar en un
    repositorio. Te aparecerá un conflicto de esta forma cuando vayas
    a hacer `push`
	
	To git@github.com:oslugr/curso-git.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:oslugr/curso-git.git'
consejo: Updates were rejected because the tip of your current branch is behind
consejo: its remote counterpart. Merge the remote changes (e.g. 'git pull')
consejo: before pushing again.
consejo: See the 'Note about fast-forwards' in 'git push --help' for details.

El error indica que la *punta* de tu rama está detrás de la rama
remota. Rechaza por lo tanto el `push`, pero vamos a hacer `pull` para
ver qué es lo que ha fallado
	
	remote: Counting objects: 7, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4 (delta 3), reused 0 (delta 0)
Unpacking objects: 100% (4/4), done.
De github.com:oslugr/curso-git
   afee5ab..bf454ef  master     -> origin/master
Auto-merging texto/mas-usos.md
CONFLICTO(contenido): conflicto de fusión en texto/mas-usos.md
Automatic merge failed; fix conflicts and then commit the result.

El conflicto de fusión te indica que no hay forma de combinar los dos
ficheros porque hay cambios en la misma línea. Así que hay que
arreglar los conflictos. En general, si se trata de este tipo de
conflictos, no es complicado. Al mirar el fichero aparecerá algo así
	
    <<<<<<< HEAD
    ## Resolviendo conflictos en `git`
    =======
    ## Vamos a ver cómo se resuelven los problemas en git
    >>>>>>> bf454eff1b2ea242ea0570389bc75c1ade6b7fa0

Lo que uno tiene está entre la primera línea y los signos de igual; lo
que hay en la rama remota está a continuación y hasta la cadena que
indica el número del commit en el cual está el conflicto. Resolver el
conflicto es simplemente borrar las marcas de conflicto (los <<<<< y
los >>>>> y los ====) y elegir el código con el que nos quedamos; en
este caso, como se ve, es el que aparece efectivamente en este
capítulo.

Una vez hecho eso, se puede ya hacer `push` directamente sin ningún
problema. 
