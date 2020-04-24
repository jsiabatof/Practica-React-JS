Crear nuestro archivo de Rutas

Dentro de nuestro proyecto vamos a crear una carpeta llamada routes donde vamos a ir añadiendo las rutas que necesitemos en la aplicación.

Las rutas que añadamos debemos definirlas con el componente Route y estas deben estar encapsuladas dentro del componente BrowserRouter del paquete de react-router-dom. Para definir una ruta con el componente Route debemos pasarle las props de:

path para indicar la url.
exact si queremos que funcione única y exactamente con la url que le digamos.
component para indicarle el componente que va a renderizar.

----------------

Container: Login

Vamos a descargar el proyecto del curso de Frontend de escuela de JavaScript para crear los componentes que necesitaremos, en caso de que vengas del curso de React no debes descargar nada.

Debemos modificar nuestra configuración del entorno de desarrollo local para que pueda funcionar con el uso de rutas, debemos ir al archivo webpack.config.js y añadir este fragmento de código antes de plugins:

module.exports = {
  {/*...*/}
  devServer: {
    historyApiFallback: true,
  },
  {/*...*/}
}

------------------

Container: Register

Para asegurar que nuestras rutas solamente se rendericen con la que haga match con la url debemos encapsular las rutas dentro del componente .

-----------------

Container: 404 Not Found

Es importante siempre tener una ruta que renderice un componente para las urls que no existan, debemos añadir esta ruta al final del Switch para que sea el caso por default.

Fragment nos permite no añadir elementos extra al DOM, podemos utilizar Fragment de 2 maneras:

Añadiendo el componente o .
O implemente encapsulando nuestros elementos dentro de <>.

------------------

Qué es Redux

Redux es una librería escrita en JavaScript, basada en la arquitectura Flux y creada por Dan Abramov, se basa en 3 principios fundamentales:

Solamente hay una fuente de la verdad.
El estado es de solo lectura.
Solamente podemos utilizar funciones puras.
Nuestra UI va a activar una action, esta action va a ejecutar un reducer para modificar la información del store, y al actualizarse el store la UI se va a modificar.