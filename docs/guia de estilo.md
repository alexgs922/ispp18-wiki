# Parte Web y API
## Archivos Web
Los archivos que no sean imágenes o hojas de estilo CSS deberán crearse a partir de Yeoman y su nombre deberá seguir el sistema de [CamelCase](https://en.wikipedia.org/wiki/Camel_case) sin mayúscula inicial. Por ejemplo, si se desea crear un servicio de actividades, se realizará de la siguiente forma:
```bash
yo angular:service activityService
```
No se recomienda cambiar el nombre de los archivos de AngularJS, ya que pueden causar fallos inesperados. En el caso de que un archivo creado por Yeoman no siga este patrón, pero se haya creado siguiendo el formato anterior, se debe de ignorar.

Si en esta sección se menciona la nomenclatura del archivo, se asume siempre que eso será lo que se introduzca dentro del comando de Yeoman.

### Servicios
Los servicios, al ser puntos de acceso que usarán los controladores para interactuar con la API, tendrán el sistema de nombres `<objeto>Service`. Puede verse el ejemplo anterior como referencia.

### Controladores
Si la vista asociada se trata de una operación CRUD, debería usarse la notación `<acción><objeto>`. Por ejemplo, si se está creando una vista de creación de actividades, el nombre del controlador que gestione la creación será `createActivity`, si se está creando la vista de eliminación de actividad, `deleteActivity`...

En el caso de que no siga el patrón anterior, como por ejemplo un controlador del 'header'. Se usará directamente el propósito del controlador.

### Vistas
Deberán seguir el formato más cercano a los [controladores](#Controladores).

### Traducciones
Las traducciones se encuentran en la carpeta 'translations'. Son varios archivos que identifican el lenguaje y dentro de éstos un JSON.

El sistema a seguir es el siguiente. Los objetos (como Activity) tendrán una variable dentro del JSON, de la siguiente forma:
```javascript
{
    ...
    ACTIVITY: {
        ...
    }
    ...
}
```

Dentro de cada uno de éstos objetos, se pondrán cada clave con su valor correspondiente:

```javascript
{
    ACTIVITY: {
        TITLE: "Title/Título",
        ...
    }
}
```

### Estilos
Generalmente, se introducirá dentro del archivo principal de estilos, `main.css`. En el caso de necesitarse crear un archivo nuevo, se debe ponerle el mismo nombre que la vista.

### Imágenes
Deberán tener algún nombre que identifique el contenido de la imágen.

## Archivos API
Estos archivos seguirán un formato similar a la parte Web. Generalmente, se debe incluir el objeto en la base de datos a implementar y un identificativo de objeto, como puede ser `Controller`, `Route` ...

## Código
### Sangría
La sangría a usar en la parte de la API será de 4 espacios. En la parte Web será de 2 espacios. 

### Indentación
Se debe tener el símbolo `{` dentro de la definición del bloque, por ejemplo:
```javascript
function asdf() {
    console.log("Javascript no funciona");
}
```
NO se permitirá, salvo en claras excepciones, el siguiente estilo:
```javascript
function asdf()
{
    console.log("Javascript no funciona");
}
```

Esto afecta a ambas partes de la aplicación.

### Nombres de las variables
Los nombres de las variables deberán ser fáciles de reconocer y usar el mismo sistema de nomenclatura que el sistema de archivos, esto es usando CamelCase con la primera en minúscula.

También se recomienda que las variables tengan nombres en inglés.

### Uso de tipos de variables
Se debe tener en cuenta la diferencia entre `let` y `var`. Se deberá de usar `let` en circunstancias donde esa variable no interactuará con el resto del bloque, por ejemplo:
```javascript
{
    var result = "Javascript no funciona";
    let result2 = "Javascript sí funciona!";
}

console.log(result); // Esto retornará "Javascript no funciona" 
console.log(result2); // Esto dará error, ya que la variable no está definida
```

También se debe considerar el uso de `const`, que sólo debería ser usado en variables constantes y en el uso en la API de importado de librerías y archivos.