# GESTIÓN DE LAS RAMAS EN GIT

## **``git stash``** - Pasar cambios de una rama a otra sin hacer commit. 

- **Esta función de git es muy útil para mover los cambios entre ramas sin hacer commits y/o perder los cambios.**

Es una pila de ficheros que podemos usar para guardar ficheros con modificaciones que no queremos comitear.

		$ git stash --help
*es una ayuda con todas sus opciones.*

		$ git stash list 
*veremos una lista con los ficheros guardados en memoría.*

		$ git stash save <nombre_stash>
*guarda todos los ficheros sin comitear bajo el nombre que le hemos dado.*

		$ git stash show <nombre_stash>
*muestras los ficheros que posee el stash deseado.*

		$ git stash pop 
*coge el último stash y lo recupera quitandolo de la lista, esto lo recupera en la rama en la que nos encontremos. **(Esta opción es la más recomendable cuando se trata de un cambio)***

		$ git stash apply <nombre_stash> ó <número_index>
*recupera el documento o cambio especificado.*

		$ git stash clear
*borra todos los stash.*

		$ git stash drop -q <nombre_stash>
*borra el stash indicado.*

## Proceso para preparar la rama con la que trabajar a partir de la rama **```dev```**.

**1.** Lo primero es actualizarse la estructura de las ramas:

		$ git fetch

**2.** Comprobamos en que estado estamos y nos cambios de rama sino nos encontramos en la rama **``dev``**:
	
		$ git status
		$ git checkout dev

**3.** Reseteamos la rama al último estado remoto:

		$ git reset --hard origin/dev

**4.** Comprobamos cambios que se haya podido subir mientras este proceso:

		$ git pull origin dev

**5.** Y por último, creamos la rama con el nombre ``USXXXX`` o ``DEXXXX`` seguido de una breve descripción que la identifique correctamente sin espacios:

		$ git checkout -b <USXXXX_ejemplo_nombre_rama>

*con esto nos aseguramos que partimos de la última version de la rama dev.*

## **``git cherry-pick``** - Aplicar los cambios introducidos por algunos commits existentes.

**1.** Lo primero es ver el log de los commit:

		$ git log (--oneline)

**2.** Aplicar el cherry-pick del commit deseado:

		$ git cherry-pick <nº de commit>
*con esto se aplican los cambios de commits.*

## Tarea de mergeo de mi rama con la rama **``dev``**.

**1.** Realizamos los pasos hasta el nº **4** que vimos anteriormente para tener la última versión de ``dev``:
	
		$ git fetch
		$ git reset --hard origin/dev
		$ git pull origin dev

**2.** Y ahora mergeamos nuestra rama sobre ``dev`` (estando sobre la rama ``dev``):
		
		$ git merge <USXXXX_ejemplo_nombre_rama>

**3.** Si existieran conflictos los resolvemos:
		
		$ git mergetool -t meld
***meld** o el editor de texto deseado.*

**4.** Borramos los archivos temporas/.orig creados en la resolución del conflicto:
	
		$ git clean -f

**5.** Hacemos commit sin mensaje ya **git** genera los commits de mergeo:
	
		& git commit
* una vez hecho el commit, salimos del editor de texto en el que entramos.*

**6.** Hasta aqui tendriamos mergeada la rama ``dev`` con nuesra rama, asi que procedemos a la segunda parte la que hace posible las pruebas cruzadas. Volvemos a nuestra rama:

		$ git checkout <USXXXX_ejemplo_nombre_rama_mergeada_anteriormente>

**7.** Ahora como ya estamos en nuestra rama mergeamos con ``dev``:
		
		$ git merge dev

**8.** Ya está lista para subir nuestra rama con los cambios a una rama remota con el mismo nombre:
		
		$ git push origin <USXXXX_ejemplo_nombre_rama>


**9.** Por último, accedemos a **github** y pedimos el pullRequest desde nuestra rama recien subida a la rama ``dev``. Esto dejará nuestra rama en un tablón en el que el encargado QA en ese momento podrá probar los cambios y a partir de ahí aprobar o rechazar el pullRequest. Si es aprobado faltaría hacer el pullRequest con la rama ``master``. Si es rechazado y viene de una **Historia de usuario** se abre un defecto que se tiene que corregir, si ya es un defecto se vuelve al anterior asignado para que lo corrija.


