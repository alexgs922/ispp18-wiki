# PROCEDIMIENTO PARA SUBIR A LA WIKI

## Modificaciones locales

**1.** Lo primero para empezar a realizar los cambios es actualizarse con lo que ya hay en el servidor (**rama master**):


			$ git pull origin master

**2.** Hacer las modificaciones oportunas y ver cambios locales con:

			$ mkdocs serve

y en la dirección [ *http://127.0.0.1:8000* ](http://127.0.0.1:8000)

**3.** Una vez modificado añadimos los cambios que tengamos con:

			$ git add .
			$ git commit -m "<Comentario>"

**4.** Subimos al repositorio remoto:

			$ git push origin master


## Desplegar en el servidor

**1.** Hay dos posiblidades vamos a explicar primero una, bajarse lo último y resetear la rama *gh-pages*:

			$ git fetch
			$ git checkout gh-pages
			$ git reset --hard origin/gh-pages
			$ git pull origin gh-pages

**2.** Volvemos a la rama *master* y desplegamos:

			$ git checkout master
			$ mkdocs gh-deploy

**1.1** Segunda forma es la siguiente, borramos la rama *gh-pages* y luego desplegamos:

			$ git branch -D gh-pages
			$ mkdocs gh-deploy
