#REACT

## ¿Qué es React?

React es una biblioteca de JavaScript para construir interfaces de usuario, creada por Facebook. Se utiliza principalmente para desarrollar aplicaciones web con una experiencia de usuario interactiva.

### Características principales:

- **Componentes**: React divide la interfaz en piezas reutilizables llamadas componentes.
- **JSX**: Una extensión de JavaScript que permite escribir código similar a HTML dentro de JavaScript.
- **Virtual DOM**: React utiliza un DOM virtual para mejorar el rendimiento.

![[Pasted image 20250121233805.png]]

---

## Instalación de React

Para iniciar con React, necesitas tener Node.js instalado. Luego, puedes crear un proyecto usando `create-react-app`:

```bash
npx create-react-app my-app
cd my-app
npm start
```

Esto generará un proyecto básico de React listo para ejecutarse.

## ¿Qué es Create React App?

**Create React App** es una herramienta de línea de comandos oficial proporcionada por Facebook que te permite configurar rápidamente un entorno de desarrollo para crear aplicaciones React de una manera sencilla y sin la necesidad de configurar manualmente herramientas como webpack, Babel o ESLint.

### Estructura Básica de un Proyecto React

```
my-app/
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── App.css
│   ├── App.js
│   ├── index.css
│   ├── index.js
│   └── logo.svg
├── package.json
├── README.md
└── node_modules/
```

- **public:** Contiene archivos estáticos que serán copiados directamente al directorio de salida de la aplicación.
    - `index.html`: El punto de entrada de la aplicación, donde se carga el script de React.
    - `favicon.ico`: El icono que se muestra en la pestaña del navegador.
- **src:** Contiene el código fuente de tu aplicación React.
    - `App.js`: El componente principal de tu aplicación.
    - `index.js`: El punto de entrada de tu aplicación desde el punto de vista de JavaScript.
    - `index.css`: El archivo CSS principal para estilizar tu aplicación.
    - `App.css`: El archivo CSS específico para el componente App.
    - `logo.svg`: Un ejemplo de un archivo de imagen.
- **package.json:** Contiene metadatos sobre tu proyecto, como las dependencias, scripts y configuración de npm.
- **README.md:** Un archivo donde puedes escribir una descripción de tu proyecto.
- **node_modules:** Contiene todas las dependencias instaladas de tu proyecto.

### ¿Cómo funciona esta estructura?

1. **index.html:** Sirve como un contenedor para tu aplicación React. Carga el script de `index.js` y proporciona un elemento con el id `root` donde se renderizará la aplicación.
2. **index.js:** Importa el componente principal `App` y lo renderiza dentro del elemento con el id `root` utilizando ReactDOM.
3. **App.js:** Es el componente raíz de tu aplicación. Aquí es donde defines la estructura y la lógica de tu aplicación.
4. **Componentes:** Puedes crear componentes adicionales para organizar tu código y reutilizar elementos de la interfaz de usuario. Estos componentes se importan y anidan dentro del componente principal.

---

## JSX: Sintaxis de Extensión de JavaScript

JSX permite escribir HTML directamente dentro de JavaScript. Ejemplo:

```jsx
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

### Reglas básicas de JSX:

1. Todo debe estar contenido en un solo elemento padre.
2. Usa `className` en lugar de `class` para las clases CSS.
3. Las etiquetas deben cerrarse correctamente.

---

## Componentes en React

Los componentes son bloques de construcción reutilizables. Pueden ser de tipo **funcional** o **de clase**.

### Componente funcional:

```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

### Componente de clase:

```jsx
class Greeting extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
```

### Uso de componentes:

```jsx
function App() {
  return (
    <div>
      <Greeting name="John" />
      <Greeting name="Maria" />
    </div>
  );
}
```

---

## Estado y Props

### Props:

Son datos que se pasan de un componente padre a un componente hijo.

```jsx
function User(props) {
  return <h2>User: {props.name}</h2>;
}
```

### Estado:

El estado es un objeto que pertenece al componente y puede cambiar con el tiempo.

#### Uso del estado en un componente de clase:

```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}
```

#### Uso del estado con hooks (en componentes funcionales):

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

---

## useEffect: Efectos Secundarios

El hook `useEffect` permite realizar efectos secundarios en componentes funcionales, como consumir una API, suscribirse a eventos, o actualizar el DOM.

### Sintaxis básica:

```jsx
import React, { useState, useEffect } from 'react';

function FetchData() {
  const [data, setData] = useState([]);

  useEffect(() => {
    // Fetch data from an API
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then((response) => response.json())
      .then((json) => setData(json));
  }, []); // Empty array means this effect runs only once

  return (
    <div>
      <h1>Posts</h1>
      <ul>
        {data.map((post) => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </div>
  );
}

```
---

## Manejo de Eventos

Los eventos en React son similares a los eventos en JavaScript.

```jsx
function Button() {
  function handleClick() {
    alert('Button clicked!');
  }

  return <button onClick={handleClick}>Click me</button>;
}
```

---

## Ciclo de Vida de los Componentes

Solo aplica a componentes de clase. Los métodos más comunes son:

1. **componentDidMount**: Se ejecuta después de que el componente se monta.
2. **componentDidUpdate**: Se ejecuta después de que el componente se actualiza.
3. **componentWillUnmount**: Se ejecuta antes de desmontar el componente.

Ejemplo:

```jsx
class Example extends React.Component {
  componentDidMount() {
    console.log('Component mounted');
  }

  componentWillUnmount() {
    console.log('Component unmounted');
  }

  render() {
    return <h1>Hello, React!</h1>;
  }
}
```

---
### Custom Hooks

Un custom hook es una función de JavaScript que utiliza los hooks de React (`useState`, `useEffect`, etc.) para encapsular lógica reutilizable. Permiten compartir la lógica entre componentes sin necesidad de duplicarla.

#### **Ventajas de los custom hooks:**

1. **Reutilización de lógica:** Evitan la duplicación de código.
2. **Legibilidad:** Simplifican los componentes al mover lógica compleja fuera de ellos.

### **Cómo crear un custom hook**

Un custom hook es simplemente una función que comienza con el prefijo `use` y puede llamar a otros hooks de React.

#### Hook para realizar solicitudes a una API

```jsx
import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    setLoading(true);
    fetch(url)
      .then((response) => {
        if (!response.ok) {
          throw new Error('Failed to fetch');
        }
        return response.json();
      })
      .then((data) => setData(data))
      .catch((error) => setError(error))
      .finally(() => setLoading(false));
  }, [url]);

  return { data, loading, error };
}

export default useFetch;
```

### ¿Como lo usamos?

```jsx
import React from 'react';
import useFetch from './useFetch';

function Posts() {
  const { data, loading, error } = useFetch('https://jsonplaceholder.typicode.com/posts');

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <ul>
      {data.map((post) => (
        <li key={post.id}>{post.title}</li>
      ))}
    </ul>
  );
}
```
