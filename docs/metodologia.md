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
* Heroku: Despliegue del producto.

## Gestión del código
La herramienta de gestión del código a utilizar será GitHub.

### Ramas
La gestión de las ramas se realizará de la siguiente [forma](gestion_ramas.md).

### Commits
El formato de los commits se encuentra en la siguiente [sección](plantillas.md#commits-v1).

La frecuencia de commits será de un commit por día trabajado como mínimo, pudiendo realizarse más si se considera necesario (por ejemplo, corrección de errores o mejoras de código).

### Pruebas cruzadas
Con el objetivo de asegurarse que el código que se realice no contenga errores, se realizarán pruebas cruzadas, que consisten en la realización de pruebas por parte de una persona que no ha realizado el código. De esta forma se podrá detectar errores que se le pueden haber pasado a los desarrolladores de la funcionalidad.

Las pruebas cruzadas se aplicarán a ramas subidas al repositorio remoto que contengan un pull request. Las personas que no realicen tareas o hayan terminado la suya podrán realizar estas pruebas. Si se detecta un error, se debe informar al desarrollador correspondiente del error, detallando cuanto más mejor sobre la generación del error. 