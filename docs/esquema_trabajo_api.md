## Esquema de trabajo del desarrollo de la API (back-end)
En esta sección se describirá el proceso a seguir para desarrollar en la parte de API.

### Selección de tareas
Siendo el grupo auto-gestionado, no se asignarán tareas de forma directa (existiendo sugerencias por parte del PM a los miembros del grupo). 

Las tareas se deben escoger basándose en la disponibilidad de los miembros del grupo. No se debe escoger una tarea con el objetivo de realizarla en la semana, sino cuanto antes sea posible (1-3 días). Como medida de la cantidad de trabajo a poner en la tarea, la medida de PHs (decidida por todo el grupo) es un indicativo de ésto. 

### Inicio de desarrollo
Se debe asignar la tarea en *Trello*, desplazar la tarea de "Unassigned" a "To do" y empezar su desarrollo, sin olvidar la creación de una nueva rama en el repositorio. Con ésto indicará al resto del grupo que la tarea se desarrolará en el tiempo antes delimitado. En el caso de no disponer del suficiente tiempo como para realizar la tarea debido a dificultades con otras asignaturas, es posible (y recomendado) desplazar la tarea hacia "Unassigned" y quitarse la asignación de la tarea.

### Progreso de la tarea
Una vez se comience a desarrollar la tarea, se desplazará la tarea a "In progress". Con esto, se podrá indicar que la tarea está en progreso y se puede asistir en su desarrollo. Una vez se termine la tarea, se creará un pull request y se desplazará la tarea a "In testing".

Para contabilizar el tiempo que tarda en realizar la tarea, debe activar el temporizador de Toggl y usar el tag más representativo (generalmente el nombre de la tarea padre) que identificará su tarea. 

La rama debería tener un nombre de la forma "US-{Número de tarea}". 

### Pruebas de la tarea
Antes de cerrar la tarea, se debería crear un pull request con título "US-{número de tarea} {descripción de tarea}" y descripción (opcional) sobre la funcionalidad implementada.

Cuando se desplace la tarea a "In testing", queda a discreción de los miembros del grupo de realizar las pertinentes pruebas de la implementación. Se dará más prioridad a la realización de pruebas que a la realización de la implementación. No olvidar activar el tiempo de Toggl durante el proceso de pruebas con el tag "Testing". La estimación de testing es la mitad de la realización de la tarea (donde si una tarea es estimado 2 PH, tardará 1 PH en realizar el testing).

### Finalización de la tarea
Una vez sea probado por otro miembro del grupo, se podrá dar por terminada la tarea que haya realizado. El miembro del grupo que haya realizado la prueba debe preocuparse de desplazar la tarea a la correspondiente lista, sea "In 'dev'" o "In 'master'" dependiendo de la rama que sea destinataria.