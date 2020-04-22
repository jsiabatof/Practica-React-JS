¿Qué es React JS?

React es una librería desarrollada por Facebook que nos ayuda a construir interfaces de usuario interactivas para todo tipo de aplicaciones: web, móviles o de escritorio.

Cada pequeña parte de nuestra página web la conoceremos como “Componente”. Cada componente se encargará de una función en específico. Además, podremos reutilizar nuestros componentes siempre que lo necesitemos.

Al unir todos nuestros componentes tendremos una página web que nos permite cambiar, actualizar o eliminar elementos de forma muy sencilla.

Nuestro profesor será Oscar Barajas: Frontend Developer en Platzi y uno de los líderes en la comunidad de Facebook Developer Circles.

---------------

DOM, Virtual DOM y React DOM

El DOM es el código HTML que se transforma en páginas web.

Cada vez que cambiamos alguna parte del DOM, también estamos actualizando el HTML con el que interactúan nuestros usuarios. El problema es que todas las operaciones, comparaciones y actualizaciones en el DOM son muy costosas.

El Virtual DOM es una herramienta que usan tecnologías como React y Vue para mejorar el rendimiento (performance) y velocidad de nuestras aplicaciones.

Es una copia exacta del DOM, pero mucho más ligera, ya que los cambios no actualizan el verdadero HTML de nuestras páginas web. Gracias al Virtual DOM podemos hacer operaciones y comparaciones de forma sumamente rápida.

Recuerda que los cambios en el Virtual DOM no afectan el HTML que ven los usuarios, así que debemos estar sincronizando constantemente las copias con el DOM. Pero no te preocupes, React DOM lo hace por nosotros.

--------------

Create React App y Tipos de Componentes

Inicialización de un proyecto en React
Creación de nuestro sitio web usando la plantilla por defecto de ->create-react-app:

npx create-react-app nombre-de-tu-proyecto

->Iniciar el servidor de desarrollo:

npm start

No olvides que puedes aprender a manejar de forma las diferentes herramientas de desarrollo en el Curso de Prework: Buenas Prácticas y Entorno de Desarrollo.

Creación y Tipos de Componentes
Los nombres de nuestros componentes deben empezar con una letra mayúscula, al igual que cada nueva palabra del componente. Esto lo conocemos como Pascal Case o Upper Camel Case.

Los componentes Stateful son los más robustos de React. Los usamos creando clases que extiendan de React.Component. Nos permiten manejar estado y ciclo de vida (más adelante los estudiaremos a profundidad).

import React, { Component } from 'react';

class Stateful extends Component {
  constructor(props) {
    super(props);

    this.state = { hello: 'hello world' };
  }

  render() {
    return (
      <h1>{this.state.hello}</h1>
    );
  }
}

export default Stateful;
También tenemos componentes Stateless o Presentacionales. Los usamos creando funciones que devuelvan código en formato JSX (del cual hablaremos en la próxima clase).

import React from 'react';

const Stateless = () => {
  return (
    <h1>¡Hola!</h1>
  );
}

// Otra forma de crearlos:
const Stateless = () => <h1>¡Hola!</h1>;

export default Stateless;

---------------

JSX: JavaScript + HTML

Estamos acostumbrados a escribir código HTML en archivos .html y la lógica de JavaScript en archivos .js.

React usa JSX: una sintaxis que nos permite escribir la estructura HTML y la lógica en JavaScript desde un mismo lugar: nuestros componentes.

import React from 'react';

const HolaMundo = () => {
  // Esto es JavaScript:
  const claseCSSHolaMundo = 'container-red';
  const mensajeTextoHTML = '¡Hola, Mundo!';

  // Esto es JSX (HTML + JavaScript):
  return (
    <div className={claseCSSHolaMundo}>
      <h1>{mensajeTextoHTML}</h1>

      {isTrue ? '¡Es verdad! :D' : '¡No es verdad! :('}
    div>
  );
}

export default HolaMundo;

------------------

Props: Comunicación entre Componentes

Las Props son la forma de enviar y recibir información en nuestros componentes. Son la forma de comunicar cada componente con el resto de la aplicación. Son muy parecidas a los parámetros y argumentos de las funciones en cualquier lenguaje de programación.

// Button.jsx
import React from 'react';

const Button = props => {
  return (
    <div>
      <button type="button">{props.text}button>
    </div>
  );
};

export default Button;
// index.jsx
import React from 'react';
import Button from './components/Button';

ReactDOM.render(
  <Button text="¡Hola!" />,
  document.getElementByid('root'),
);

-----------------

¿Qué son los métodos del ciclo vida?

Todos los componentes en React pasan por una serie de fases que generalmente se denominan “Ciclo de Vida del componente” es un proceso que React hace en cada componente, en algunos casos no podemos verlos como un bloque de código y en otros podemos llamarlos en nuestro componente para asignar una actividad según sea el caso necesario.

Los componentes en react pasan por un Montaje, Actualización, Desmontaje y Manejo de errores.

Montaje:
En esta fase nuestro componente se crea junto a la lógica y los componentes internos y luego es insertado en el DOM.

Actualización:
En esta fase nuestro componente está al pendiente de cambios que pueden venir a través de un cambio en “state” o “props” esto en consecuencia realizan una acción dentro de un componente.

Desmontaje:
En esta etapa nuestro componente “Muere” cuando nosotros no necesitamos un elemento de nuestra aplicación, podemos pasar por este ciclo de vida y de esta forma eliminar el componente de la representación que tiene en el DOM.

Manejo de Errores:
Cuando nuestro código se ejecuta y tiene un error, podemos entrar en una fase donde se puede entender mejor qué está sucediendo con la aplicación.

Algo que debemos tener en cuenta es que un componente NO debe pasar por toda las fases, un componente puede ser montado y desmontado sin pasar por la fase de actualización o manejo de errores.

Ahora que entendemos las fases que cumple el ciclo de vida en React vamos a entrar a detalle en cada uno de ellos para ver qué piezas de código se ejecutan y nos ayudarán a crear aplicaciones en React pasando por un ciclo de vida bien estructurado.

Montado:
Constructor()

Este es el primer método al que se hace un llamado, aquí es donde se inicializan los métodos controladores, eventos del estado.

getDerivedStateFromProps()

Este método se llama antes de presentarse en el DOM y nos permite actualizar el estado interno en respuesta a un cambio en las propiedades, es considerado un método de cuidado, ya que su implementación puede causar errores sutiles.

render()

Si queremos representar elementos en el DOM en este método es donde se escribe esta lógica, usualmente utilizamos JSX para trabajar y presentar nuestra aplicación.

ComponentDidMount()

Este método se llama inmediatamente que ha sido montado en el DOM, aquí es donde trabajamos con eventos que permitan interactuar con nuestro componente.

Actualización:
getDerivedStateFromProps()

Este método es el primero en ejecutarse en la fase de actualización y funciona de la misma forma que en el montaje.

shouldComponentUpdate()

Dentro de este método se puede controlar la fase de actualización, podemos devolver un valor entre verdadero o falso si queremos actualizar o no el componente y es utilizado principalmente para optimización.

render()

Se llama el método render que representa los cambios en el DOM.

componentDidUpdate()

Este método es invocado inmediatamente después de que el componente se actualiza y recibe como argumentos las propiedades y el estado y es donde podemos manejar nuestro componente.

Desmontado
componentWillUnmount()

Este método se llama justo antes de que el componente sea destruido o eliminado del DOM.

Manejo de Errores:
getDerivedStateFromError()

Una vez que se lanza un error este es el primer método que se llama, el cual recibe el error como argumento y cualquier valor devuelto en este método es utilizado para actualizar el estado del componente.

componentDidCatch()

Este método es llamado después de lanzarse un error y pasa como argumento el error y la información representada sobre el error.

Ahora que entendemos cada una de las fases que tiene el ciclo de vida de react, podemos utilizarlas según sea necesario en nuestra aplicación y de esta forma crear las interacciones que necesitemos.

---------------

State - Events

"React nos permite responder a las interacciones de los usuarios con propiedades como onClick, onChange, onKeyPress, onFocus, onScroll, entre otras.

Estas propiedades reciben el nombre de la función que ejecuta el código que responde a las interacciones de los usuarios. Seguramente, esta función usará la función this.setState para actualizar el estado de nuestro componente.

class Button extends React.Component {
  state = { count: 0 }

  handleClick = () => (
     this.setState({ count: this.state.count + 1 })
  );

  render() {
    const { count } = this.state;

    return (
      <div>
        <h1>Manzanas: {count}</h1>
        <button onClick{this.handleClick}>Sumar</button>
      </div>
    );
  }
}

Recuerda que los nombres de estos eventos deben seguir la nomenclatura camelCase: primera palabra en minúsculas, iniciales de las siguientes palabras en mayúsculas y el resto también en minúsculas."

-----------------

Instalación y configuración de entorno

Iniciar un repositorio en GIT:

git init
Iniciar un proyecto de Node.js:

npm init -y
```

Instalar React:

```bash
npm install --save react react-dom

------------------

Agregando compatibilidad con todos los navegadores usando Babel

Babel es una herramienta muy popular para escribir JavaScript moderno y transformarlo en código que pueda entender cualquier navegador.

Instalación de Babel y otras herramientas para que funcione con React:

npm install --save-dev @babel/core @babel/preset-env @babel/preset-react babel-loader
Configuración de Babel (.babelrc):

{
  ""presets"": [
    ""@babel/preset-env"",
    ""@babel/preset-react""
  ],
}

---------------

Webpack: Empaquetando nuestros módulos

"Webpack es una herramienta que nos ayuda a compilar multiples archivos (JavaScript, HTML, CSS, imágenes) en uno solo (o a veces un poco más) que tendrá todo nuestro código listo para producción.

Instalación de Webpack y algunos plugins:

npm install webpack webpack-cli html-webpack-plugin html-loader  --save-dev
Configuración de Webpack (webpack.config.js):

const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  resolve: {
    extensions: ['.js', '.jsx'],
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
        },
      },
      {
        test: /\.html$/,
        use: {
          loader: 'html-loader',
        },
      },
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './public/index.html',
      filename: './index.html',
    }),
  ],
};
Script para ejecutar las tareas de Webpack (package.json):

{
  ""scripts"": {
    ""build"": ""webpack --mode production""
  },
}

----------------

Webpack Dev Server: Reporte de errores y Cambios en tiempo real

Instalación de Webpack Dev Server:

npm install --save-dev webpack-dev-server
Script para ejecutar el servidor de Webpack y visualizar los cambios en tiempo real (package.json):

{
  ""scripts"": {
    ""build"": ""webpack --mode production"",
    ""start"": ""webpack-dev-server --open --mode development""
  },
}

--------------

Estilos con SASS

Los preprocesadores como Sass son herramientas que nos permiten escribir CSS con una sintaxis un poco diferente y más amigable que luego se transformará en CSS normal. Gracias a Sass podemos escribir CSS con variables, mixins, bucles, entre otras características.

Instalación de Sass:

npm install --save-dev mini-css-extract-plugin css-loader node-sass sass-loader
Configuración de Sass en Webpack (webpack.config.js):

const MiniCssExtractPlugin = require('mini-css-extract-plugin');

// ...

module: {
  rules: [
    {
      test: /\.(s*)css$/,
      use: [
        { loader: MiniCssExtractPlugin.loader },
        'css-loader',
        'sass-loader',
      ],
    },
  ],
},

// ...

plugins: [
  new MiniCssExtractPlugin({
    filename: 'assets/[name].css',
  }),
],`
```

---------------

Configuración final: ESLint y Git Ignore

El Git Ignore es un archivo que nos permite definir qué archivos NO queremos publicar en nuestros repositorios. Solo debemos crear el archivo .gitignore y escribir los nombres de los archivos y/o carpetas que no queremos publicar.
Los linters como ESLint son herramientas que nos ayudan a seguir buenas prácticas o guías de estilo de nuestro código.
Se encargan de revisar el código que escribimos para indicarnos dónde tenemos errores o posibles errores. En algunos casos también pueden solucionar los errores automáticamente. De esta manera podemos solucionar los errores incluso antes de que sucedan.
Instalación de ESLint:

npm install --save-dev eslint babel-eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-react eslint-plugin-jsx-a11y
Podemos configurar las reglas de ESLint en el archivo .eslintrc.

---------------

