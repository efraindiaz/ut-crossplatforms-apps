# Estado en React, Memorización, Portales y Rendimiento  🚀 
## Objetivos  
1. Comprender cómo funciona el estado en React (props, estado local y global). 
2. Explorar librerías para el manejo del estado global (Redux, Zustand, Context API). 
3. Aprender sobre memorización con `React.memo`, `useMemo` y `useCallback`. 
4. Conocer React Portals para componentes fuera de la jerarquía del DOM. 
5. Entender conceptos avanzados de rendimiento en React.

# Estado, Memorización, Portales y Rendimiento 🚀

## 1. Comprendiendo el Estado en React

### ¿Qué es el Estado?
El estado en React es un mecanismo para manejar datos dinámicos que determinan cómo se renderiza y se comporta un componente.  
Tipos de estado:
1. **Props:** Datos pasados de un componente padre a uno hijo.
2. **Estado Local:** Administrado dentro de un componente con hooks como `useState`.
3. **Estado Global:** Compartido entre múltiples componentes, gestionado con Context API o librerías externas.

### Prop Drilling
El "prop drilling" ocurre cuando se pasan props a través de múltiples niveles de componentes para alcanzar uno específico.  
**Problema:** Dificulta la escalabilidad y mantenibilidad.  
**Solución:** Utilizar Context API o librerías como Redux/Zustand.

#### Ejemplo de Prop Drilling:
```javascript
function ChildComponent({ message }) {
  return <h2>{message}</h2>;
}

function IntermediateComponent({ message }) {
  return <ChildComponent message={message} />;
}

function ParentComponent() {
  const message = "Hello from the parent!";
  return <IntermediateComponent message={message} />;
}

export default ParentComponent;

```


![prop-drilling](https://github.com/efraindiaz/ut-crossplatforms-apps/blob/main/U01/react/prop-drilling.png?raw=true)

## 2. Librerías para Manejar Estado

### Redux

Redux es una librería que organiza el estado global en una única fuente llamada "store".

#### Ejemplo Básico de Redux:

```js
import { createStore } from 'redux';

// Initial state
const initialState = { count: 0 };

// Reducer
function counterReducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

// Create store
const store = createStore(counterReducer);

```

### Zustand

Zustand es una librería ligera y simple para manejar el estado global sin requerir mucho boilerplate.

#### Ejemplo Básico de Zustand:

```js
import create from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));

function Counter() {
  const { count, increment, decrement } = useStore();
  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
}

export default Counter;
```

## 3. Memorización en React

La memorización optimiza el rendimiento evitando renders innecesarios.

### `React.memo`

Evita que un componente hijo se vuelva a renderizar si sus props no han cambiado.

#### Ejemplo:

```js
import React from 'react';

const MemoizedComponent = React.memo(({ value }) => {
  console.log('Rendered');
  return <h2>Value: {value}</h2>;
});

function App() {
  const [count, setCount] = React.useState(0);
  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <MemoizedComponent value="Static Value" />
    </div>
  );
}

export default App;
```


### `useMemo`

Memoriza cálculos costosos.

#### Ejemplo:

```js
import React, { useMemo } from 'react';

function ExpensiveComponent({ number }) {
  const result = useMemo(() => {
    console.log('Calculating...');
    return number * 2;
  }, [number]);

  return <h2>Result: {result}</h2>;
}

export default function App() {
  const [count, setCount] = React.useState(0);
  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <ExpensiveComponent number={count} />
    </div>
  );
}
```


### `useCallback`

Memoriza funciones para evitar recrearlas.

#### Ejemplo:

```js
import React, { useState, useCallback } from 'react';

function Button({ onClick }) {
  console.log('Button rendered');
  return <button onClick={onClick}>Click Me</button>;
}

const MemoizedButton = React.memo(Button);

export default function App() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log('Button clicked');
  }, []);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <MemoizedButton onClick={handleClick} />
    </div>
  );
}
```


## 4. React Portals

Los Portals permiten renderizar componentes en nodos fuera de la jerarquía del DOM.

#### Ejemplo: Modal con Portals

```js
import React from 'react';
import ReactDOM from 'react-dom';

function Modal({ children, onClose }) {
  return ReactDOM.createPortal(
    <div className="modal">
      <div className="modal-content">
        {children}
        <button onClick={onClose}>Close</button>
      </div>
    </div>,
    document.getElementById('modal-root')
  );
}

function App() {
  const [isOpen, setIsOpen] = React.useState(false);

  return (
    <div>
      <button onClick={() => setIsOpen(true)}>Open Modal</button>
      {isOpen && <Modal onClose={() => setIsOpen(false)}>This is a modal!</Modal>}
    </div>
  );
}

export default App;
```


## 5. Conceptos Avanzados de Rendimiento

### Optimización con Lazy Loading y Code Splitting

Cargar dinámicamente componentes o dividir el código para reducir el tamaño inicial del bundle.

#### Ejemplo: Lazy Loading

```js
import React, { Suspense } from 'react';

const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
  return (
    <Suspense fallback={<h2>Loading...</h2>}>
      <LazyComponent />
    </Suspense>
  );
}

export default App;
```

