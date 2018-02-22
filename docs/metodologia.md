En esta página se detallará las herramientas usadas, procesos de construcción del software ...

## Herramientas

### Planificación
* Trello: Creación, asignación y comprobación del estado de las tareas.
* Toggl: Control del tiempo aplicado a las tareas de Trello.
* Slack: Comunicación informal escrita.
* Skype: Comunicación informal y formal oral.

### Integración
* Sonar: Comprobación de pruebas en el código.
* Icinga: Monitorización de la red.
* Travis: Integración continua.

### Desarrollo
* Github: Gestión del control de versiones.
* MongoDB: Base de datos.
* React Native: Framework basado en JS donde se desarrollará la aplicación.
* Heroku: Despliegue del producto.

## Gestión del código
Para empezar, se realizará a través de GitHub. Se utilizarán el siguiente esquema de ramas:
* 'master': Contendrá una base de la aplicación fiable, deben pasar todas las pruebas y garantiza el software sin errores graves y con funcionalidades que pasan las pruebas funcionales.
* 'dev': Contiene código que se introducirá en master, podrá contener funcionalidades pero es posible que contengan errores. Se realizarán pruebas cruzadas en esta rama con el objetivo de detectar errores, por lo que pueden no pasar las pruebas.
* '\<func\>': Corresponderá a una funcionalidad a añadir del código. Puede modificarse por varias personas y pueden contener errores.

Se debe tener en cuenta que la modificación de 'master' podrá implicar que el código deje de funcionar en una versión que puede proveerse al cliente en cualquier momento, por lo que la rama 'master' estará bloqueada de modificaciones y sólo se podrá modificar a través de pull requests.

### Commits
El formato de los commits se encuentra en la siguiente [sección](https://github.com/alexgs922/adrenalive-api/wiki/Otros#commits-v1).

### Pruebas cruzadas
Con el objetivo de asegurarse que el código que se realice no contenga errores, se realizarán pruebas cruzadas, que consisten en la realización de pruebas por parte de una persona que no ha realizado el código. De esta forma se podrá detectar errores que se le pueden haber pasado a los desarrolladores de la funcionalidad.


