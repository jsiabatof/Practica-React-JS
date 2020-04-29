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

-----------------

¿Qué es Redux? Profundizando en la herramienta

¿Que es Redux?

Redux nos permite tener un contenedor predecible del estado en aplicaciones creadas con JavaScript, Nos ayuda a escribir aplicaciones que se comportan de una manera consistente, Esto significa que podemos utilizar esta lógica en aplicaciones del lado del cliente, trabajar del lado del servidor o crear aplicaciones para dispositivos móviles.

Uno de los principales uso que tiene Redux es con React pero puede ser implementado en cualquier librería o proyecto que este construido con JavaScript, lo cual incluye a Angular, Vue o algún otro framework o librería.

Redux nace de la arquitectura Flux, tomando inspiración del lenguaje funcional Elm y es creado por Dan Abramov y Andrew Clark en el 2015, Hoy en día es una de las librerías más utilizadas para el manejo del flujo de la información en aplicaciones.

Una de las principales motivaciones para crear Redux nace en resolver un problema y era el manejo del estado y el flujo de nuestras aplicaciones creadas en JavaScript. Redux propone una forma de manejar el estado donde podamos controlar cómo vamos a interactuar con otros elementos (llamadas a un API) o interacciones dentro de nuestra aplicación, teniendo en cuenta esto, Redux intenta de predecir las mutaciones que pueda sufrir el estado, creando restricciones de cuando y como pueden ser ejecutadas las actualizaciones en nuestras aplicaciones.

Redux es una librería muy pequeña que se puede incorporar en cualquier proyecto construido en JavaScript y se basa en tres principios:

Única fuente de la verdad:
Nuestra aplicación solo debe de tener un único Store y es la única fuente de información.

El estado es de solo lectura
La única forma de modificar el estado es emitiendo un acción, este objeto describe lo que va a ocurrir.

Los cambios se realizan con funciones puras
Para realizar cambios al estado es necesario utilizar Reducers los cuales son funciones puras que toman el estado anterior, una acción y devuelve un nuevo estado con las modificaciones necesarias.

Teniendo en cuenta esta información continuaremos en el curso explicando cada uno de estos elementos que incorpora Redux en nuestra aplicación Platzi Video.

------------------

Instalación de Redux

Vamos a instalar las dependencias para poder trabajar con Redux:

npm install redux react-redux --save
Dentro de nuestro proyecto vamos a crear una carpeta para nuestros actions y otra para los reducers que utilizaremos en Redux.

El paquete react-redux nos proporciona un Provider para poder encapsular nuestros componentes por medio de un connect para poder transmitir la información que necesitemos del store a cada componente.

-------------------

Creando el Store de Redux

Para crear un Store necesitamos llamar a la función createStore del paquete de redux pasándole los parámetros del reducer y initialState.

Para conectar un componente a Redux vamos a necesitar importar connect de react-redux, connect va a aceptar dos parámetros:

->mapStateToProps: es una función que le va a indicar al provider qué información necesitamos del store.

->mapDispatchToProps: es un objeto con las distintas funciones para ejecutar una action en Redux.

-------------------

Creando los reducers

Un action de Redux va a contener dos elementos:

->type: para indicar la acción que se va a ejecutar.

->payload: es la información que estamos mandando al reducer.

Dentro de los reducers usaremos un switch para separar la lógica por cada tipo de acción que tendremos en Redux.

------------------

Creando un Servicio para Gravatar

Muchas veces la mejor opción no es descargar un paquete de npm ya que podemos ver la documentación, entender cómo funciona y nosotros implementar el código necesario para nuestro caso, ya que instalar todo el paquete puede volver más pesado nuestro proyecto.

Para nuestro servicio que llamará a Gravatar vamos a crear la carpeta utils y dentro añadir el archivo gravatar.js.

-----------------

Debug con Redux Devtools

Redux Dev Tools nos va a servir mucho para entender mejor el flujo de nuestra información en nuestra aplicación y poder realizar debugging de manera sencilla.

Solamente necesitas instalar la extensión según el navegador que tengas:

Chrome
Firefox
Una vez instalado dentro de nuestro index.js vamos a añadir el siguiente código:

// importamos compose
import { createStore, compose } from ‘redux’;
...

const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose

const store = createStore(reducer, initialState, composeEnhancers