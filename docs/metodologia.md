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
La herramienta de gestión del código a utilizar será GitHub.

### Ramas
La gestión de las ramas se realizará de la siguiente forma. Primero, se dispondrá de 'master', que almacenará un código que se considera como listo para despliegue, por lo que pasará pruebas funcionales, de sistema y de casos de uso. Después, se tendrá la rama de 'dev', que puede contener código con nuevas funcionalidades, pero pueden no estar probadas completamente y pueden dar errores. 

El progreso de una versión a otra se realizará de la siguiente manera. Se dispondrán de ramas de defectos y de casos de uso. Estas ramas se trabajarán realizando un 'branch' desde 'dev'. Una vez se considere el código como terminado, se realizará inicialmente un 'pull' de 'dev' y 'rebase' desde 'dev' a la nueva funcionalidad de forma local (es decir, sin subir el código). Se realizará el proceso contrario, realizando un 'rebase' desde la rama trabajada a 'dev', de esta forma los conflictos quedarán eliminados con el primer 'rebase' y se podrá seguir trabajando en la funcionalidad. Una vez se hayan solucionado los conflictos, se subirá la rama de funcionalidad/defecto al repositorio remoto.

Una vez el código quede de la forma correcta, se realizará un pull request a 'dev' o a la funcionalidad padre. Se realizarán pruebas cruzadas del código implementado por lo que se espera que el código se haya probado de la forma que se considere adecuada.

### Commits
El formato de los commits se encuentra en la siguiente [sección](https://github.com/alexgs922/adrenalive-api/wiki/Otros#commits-v1).

La frecuencia de commits será de un commit por día trabajado como mínimo, pudiendo realizarse más si se considera necesario (por ejemplo, corrección de errores o mejoras de código).

### Pruebas cruzadas
Con el objetivo de asegurarse que el código que se realice no contenga errores, se realizarán pruebas cruzadas, que consisten en la realización de pruebas por parte de una persona que no ha realizado el código. De esta forma se podrá detectar errores que se le pueden haber pasado a los desarrolladores de la funcionalidad.

Las pruebas cruzadas se aplicarán a ramas subidas al repositorio remoto que contengan un pull request. Las personas que no realicen tareas o hayan terminado la suya podrán realizar estas pruebas. Si se detecta un error, se debe informar al desarrollador correspondiente del error, detallando cuanto más mejor sobre la generación del error. 