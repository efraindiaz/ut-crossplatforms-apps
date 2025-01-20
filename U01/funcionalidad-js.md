
![Pasted image 20250119181602.png](https://pbs.twimg.com/media/GhIyLvhWoAAnLeR.png)

- Variables
- Tipos de datos
- Operadores
- Estructuras de control
- Funciones
- Scope
- DOM


## Ciclos e Iteración Avanzada
Permiten ejecutar bloques de código varias veces. Incluyen `for...of` y `for...in` para iterar sobre arrays y objetos.

### Ejemplo:
```javascript
let fruits = ["apple", "pear", "grape"];
for (let fruit of fruits) {
  console.log(fruit);
}

let person = { name: "Anna", age: 30 };
for (let key in person) {
  console.log(key, person[key]);
}
```

---

## Arrays y Métodos Comunes
Los arrays almacenan múltiples valores en una sola variable. Métodos como `push`, `pop`, `map`, y `filter` son esenciales.

### Ejemplo:
```javascript
let numbers = [1, 2, 3, 4];
numbers.push(5); // Adds 5 to the end
console.log(numbers); // [1, 2, 3, 4, 5]

let evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4]
```

---

## Objetos
Los objetos almacenan datos en pares clave-valor. Son fundamentales para modelar entidades del mundo real.

### Ejemplo:
```javascript
let person = {
  name: "Carlos",
  age: 28,
  greet: function() {
    return `Hello, I am ${this.name}`;
  }
};
console.log(person.greet()); // Hello, I am Carlos
```

---
## Programación Orientada a Objetos (POO)
La POO permite crear estructuras más organizadas mediante clases y objetos.

### Ejemplo:
```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    return `Hello, I am ${this.name}`;
  }
}

let john = new Person("John", 30);
console.log(john.greet()); // Hello, I am John
```

---

## ES6: Novedades Clave

### Funciones Flecha (Arrow Functions)
Son una forma más concisa de escribir funciones.
```javascript
const add = (a, b) => a + b;
console.log(add(3, 4)); // Result: 7
```

### Destructuración
La destructuración permite extraer valores de arrays u objetos de forma más sencilla y legible. Se utiliza ampliamente para evitar acceder manualmente a las propiedades o índices.

#### Ejemplo con Arrays:
```javascript
let numbers = [10, 20, 30];
let [first, second] = numbers;
console.log(first); // 10
console.log(second); // 20
```

#### Ejemplo con Objetos:
```javascript
let person = { name: "Alice", age: 25 };
let { name, age } = person;
console.log(name); // Alice
console.log(age); // 25
```

La destructuración es especialmente útil en funciones:
```javascript
function greet({ name, age }) {
  return `Hello, ${name}. You are ${age} years old.`;
}

console.log(greet({ name: "Mark", age: 40 }));
```

---

### Operadores Rest y Spread

#### Operador Rest (`...`)
El operador Rest permite agrupar múltiples elementos en una sola variable. Es útil en funciones con un número variable de argumentos.

##### Ejemplo:
```javascript
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}
console.log(sum(1, 2, 3, 4)); // 10
```

#### Operador Spread (`...`)
El operador Spread permite expandir elementos de un array u objeto en lugares donde se esperan múltiples valores.

##### Ejemplo:
```javascript
let array1 = [1, 2, 3];
let array2 = [...array1, 4, 5];
console.log(array2); // [1, 2, 3, 4, 5]

let obj1 = { a: 1, b: 2 };
let obj2 = { ...obj1, c: 3 };
console.log(obj2); // { a: 1, b: 2, c: 3 }
```

---

### Template Literals
Las plantillas literales permiten crear cadenas de texto dinámicas usando backticks (`` ` ``) y la interpolación con `${}`.

#### Ejemplo:
```javascript
let name = "John";
let age = 30;
console.log(`My name is ${name} and I am ${age} years old.`);
// My name is John and I am 30 years old.
```

---

### Almacenamiento Local y de Sesión
`localStorage` y `sessionStorage` son APIs del navegador para almacenar datos clave-valor. La diferencia principal es que `localStorage` persiste los datos incluso si se cierra el navegador, mientras que `sessionStorage` los elimina al cerrar la pestaña.

#### Ejemplo:
```javascript
// Almacenar datos
localStorage.setItem("username", "Alice");
console.log(localStorage.getItem("username")); // Alice

// Eliminar datos
localStorage.removeItem("username");

// Almacenamiento de sesión
sessionStorage.setItem("token", "abc123");
console.log(sessionStorage.getItem("token")); // abc123
```

---

### Conversión de Tipos
Permite convertir datos entre tipos como string, number, y boolean.

#### Ejemplo:
```javascript
let numString = "123";
let number = parseInt(numString); // Convierte a número
console.log(number); // 123

let floatString = "123.45";
let floatNumber = parseFloat(floatString);
console.log(floatNumber); // 123.45

let num = 456;
let stringNum = String(num); // Convierte a string
console.log(stringNum); // "456"
```

---

## JSON
JSON es un formato ligero para estructurar y transmitir datos entre sistemas. Se utiliza comúnmente en APIs para enviar y recibir información.

### Ejemplo:
```javascript
let user = { name: "Luis", age: 25 };
let json = JSON.stringify(user);
console.log(json); // {"name":"Luis","age":25}

let parsed = JSON.parse(json);
console.log(parsed.name); // Luis
```

---
## Event Loop
El Event Loop es el mecanismo que permite a JavaScript manejar tareas asíncronas. Se asegura de que las operaciones no bloqueen el hilo principal al moverlas a una cola de eventos.

### Conceptos Clave:
- **Call Stack**: Donde se apilan las funciones en ejecución.
- **Task Queue**: Cola donde se almacenan las tareas asíncronas.

### Flujo Básico:
1. El código síncrono se ejecuta en el Call Stack.
2. Las operaciones asíncronas se envían a la Task Queue.
3. El Event Loop verifica si el Call Stack está vacío y luego procesa las tareas en la Task Queue.

### Ejemplo:
```javascript
console.log("Start");

setTimeout(() => {
  console.log("Task completed");
}, 2000);

console.log("End");
// Output: Start, End, Task completed (after 2 seconds)
```

El Event Loop permite manejar tareas concurrentes sin bloquear el hilo principal.

---
## Promesas y async/await

### ¿Qué son las Promesas?
Las promesas son un objeto que representa el resultado eventual (resuelto o rechazado) de una operación asíncrona. Su propósito es manejar el flujo asíncrono sin necesidad de callbacks anidados.

### Estados de una Promesa:
1. **Pendiente (Pending)**: La operación no ha terminado.
2. **Resuelta (Fulfilled)**: La operación se completó exitosamente.
3. **Rechazada (Rejected)**: La operación falló.

### Ejemplo básico con Promesas:
```javascript
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = true;
      if (success) {
        resolve("Data loaded successfully");
      } else {
        reject("Error loading data");
      }
    }, 2000);
  });
};

fetchData()
  .then(data => console.log(data)) // Data loaded successfully
  .catch(error => console.error(error));
```

---

### ¿Qué es `async/await`?
`async/await` es una sintaxis introducida en ES8 que simplifica el manejo de promesas. Permite escribir código asíncrono de forma que parezca síncrono.

### Diferencias:
- **Promesas**: Usan `then` y `catch` para manejar resultados.
- **async/await**: Utilizan palabras clave que hacen el código más legible y fácil de depurar.

### Ejemplo básico con `async/await`:
```javascript
const fetchData = async () => {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Error fetching data:", error);
  }
};

fetchData();
```

**Nota**: La palabra clave `await` sólo puede ser utilizada dentro de funciones declaradas como `async`.

