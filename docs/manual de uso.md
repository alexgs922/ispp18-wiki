# API
En esta sección se explicará el sistema de la API.

## Inicio
La API se despliega en el puerto 3000 (en su defecto en el puerto definido por la variable del sistema PORT), tal y como viene configurado en el archivo 'config.js'.
```javascript
    port: process.env.PORT || 3000
```
La razón de este sistema es porque el despliegue en Heroku requiere desplegarlo en puertos especificos para su correcto funcionamiento.

Antes de poder iniciar la API y servidor Web, se necesita tener una conexión en local con la base de datos MongoDB, en el puerto 27017.

Si quiere iniciar la API, debe realizar el siguiente comando:
```bash
npm start
```
Podrá acceder al servidor con Postman o accediendo a 'localhost:\<PORT>/api/...'.

## Router
Express, la librería que permite gestionar el servidor, utiliza un archivo donde se indican las rutas disponibles, que es 'routes/index.js'. En esa carpeta se encuentran lineas como la siguiente:
```javascript
api.get('/users', auths.isAuth, usersCtrl.getAllUsers);  //Get all users
```
Se describirá cada elemento de esta linea:
 - `api`: Se trata de un objeto de enrutado que proviene de `express.Router()`. Contiene todas las rutas del sistema.
 - `get`: Es uno de los verbos HTML. Podrán ser válidos elementos como `post`, `delete`, `put`...
 - `'/users'`: La ruta de la entrada, en el servidor se podrá acceder a esta ruta con 'localhost:3000/api/users'.
 - `:id`: Se trata de un atributo dentro de la ruta. Será accesible con `req.params.id` (se verá más adelante qué significa `req`). No confundir con un atributo GET, esos son accesibles sin necesidad de indicarlos con los dos puntos.
 - `auths.isAuth`: Método que comprueba los credenciales del usuario, generalmente se deberá poner para evitar el acceso de usuarios no registrados, pero puede obviarse (por ejemplo, en el registro). Debe ponerse antes del controlador.
 - `userCtrl.getAllUsers`: Se trata del método que recogerá esta petición. Deberá ser de la forma `function(req, res)`. En la [sección de controladores](#Controllers) se describirá más a fondo qué significan.
 - Finalmente, es recomendado comentar qué realiza esta petición, ya que permitirá conocer más a la hora de realizar las pruebas.

## Auths
En 'middleware/auths.js' se encuentra el método que comprueba los credenciales del usuario. Generalmente este método no se modificará.

El proceso de identificación de usuarios se basa en la librería `jwt-basic` y consiste en comprobación de token, que es generado en la creación del usuario y guardado en la colección 'auths'.

Una vez se haya identificado al usuario, se debe llamar a `next()` ya que en caso contrario, la petición no llegará al controlador o subsecuente método especificado en el Router.

## Schema
En la carpeta 'models/', se encuentran los objetos gestionados en la base de datos. Los objetos creados se usan a partir de un objeto de la librería `mongoose` llamado `Schema`. A partir de éste se pueden realizar las consultas, sin necesidad de realizar una llamada a la BD como tal, por lo que es recomendado.

Para más información con respecto a Schema, se puede acceder a la [documentación oficial](http://mongoosejs.com/docs/guide.html)

## Controllers
Los controladores se encuentran en la carpeta `controllers`. Los controladores son funciones que deben tener como argumentos `req`, que es un objeto que contiene datos de la petición, y `res`, que contiene información y métodos para el envío. En este método debe incluirse una petición a la base de datos, generalmente, y comprobar que en efecto los atributos tipo GET y a través de URL son correctos.

Los atributos de `req` más usados son:
 - `req.params.<elem>`: Obtendrá un atributo GET o URL de la forma `?<elem>=<val>` o `/<val>` (especificado en Route el nombre del parámetro). En este caso retornaría `<val>`.
 - `req.body.<elem>`: Obtiene un elemento del JSON enviado. Esto es sólo aplicable en peticiones tipo POST.

Los atributos más usados de `res` son: 
 - `res.status`: Determina el código de estado HTTP de la respuesta al cliente. Generalmente será 200, OK. En caso de error, es mejor enviar un código tipo 4XX cuando el objeto o petición no exista y 5XX cuando haya pasado algo raro en la petición (ejemplo, que se interrumpa la conexión con la base de datos).
 - `res.send`: Envía los datos introducidos. Generalmente se usarán métodos especializados para el envío de información JSON o HTML.
 - `res.json`: Envía los datos introducidos en formato JSON. Realizará las transformaciones requeridas así como incluir en el header los elementos necesarios.
 - `res.render`: Envía los datos introducidos en formato HTML. Es preferible que el contenido sea un HTML válido.

Debe tenerse especial cuidado al usar `res.send`, `res.json` y `res.render` ya que éstos realizarán el envío directamente, por lo que si necesita realizar un tratamiento posterior, el envío ya se habrá realizado.

# Web
En esta sección se describirá el uso de la parte Web de la aplicación

## Instalación
Primero, debemos instalar una serie de dependencias globales, aparte de `npm install`.
Se va a necesitar 'yo' y 'generator-angular' que pueden instalarse de esta forma:
```
npm install -g yo generator-angular
```
Con esto se podrá introducir nuevas vistas y controladores.

Después, para ejecutar la parte Web, se deberá acceder a la carpeta 'api/' y ejecutar:
```
npm start
```

Con esto, se ejecutará la parte Web y API.

## Añadir nuevas vistas y controladores
Para añadir nuevas vistas o controladores, debe ejecutarse el siguiente comando dentro de la carpeta 'cliente':
```
yo angular:route <ruta>
```
Con esto, se crearán archivos en la carpeta 'views', 'scripts/controllers' y se añadirá la ruta en la carpeta correspondiente. 

En la carpeta de 'views', se encuentran las vistas HTML de la página. Se podrá usar todos los comandos de AngularJS como ng-repeat y otros.

En la carpeta de 'scripts/controllers' están la definición de controladores. Se debe tener en cuenta que el '$scope' de AngularJS se encuentra en el objeto 'this' y para acceder a éste debe llamarse con el nombre del controlador.

Finalmente, los estilos en CSS se encuentran en la carpeta 'styles' y las imágenes y otros datos en 'images'.

## Añadir nuevos servicios
Para añadir servicios, accesible por controladores definidos anteriormente, se debe ejecutar el siguiente comando:
```
yo angular:service <nombreServicio>
```
El servicio (que se introducirá de forma correcta dentro del 'index.html') se podrá acceder a través de la carpeta 'cliente/app/scripts/services/'. Recordar que se define una función que debe retornar un diccionario con cada función que ofrezca el servicio y el importado de servicio funciona de igual forma que con los controladores.

## Internacionalización
Para internacionalizar la aplicación, sólo es necesario incluir el texto de la siguiente forma en el caso de tratarse de un texto constante:
```javascript
{{ 'KEY' | translate }}
```

Éste sistema funcionará también con variables del $scope.
```javascript
{{ error | translate }}
```
