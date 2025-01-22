#Desarrollo WEB

## **1. Manipulación del DOM**

### **Explicación:**

El DOM (Document Object Model) representa la estructura de un documento HTML como un árbol de nodos. Manipular el DOM significa interactuar con estos nodos para modificar la estructura, el contenido o el estilo del documento.

### **Ejemplo: Selección de elementos**

```javascript

const header = document.querySelector("header"); // Selecciona el primer elemento <header> del documento.

const items = document.getElementsByClassName("item"); // Selecciona todos los elementos con la clase "item".

```


### **Ejemplo: Creación y eliminación de nodos**

```javascript

const newDiv = document.createElement("div"); // Crea un nuevo elemento <div>.

newDiv.textContent = "Hola, mundo"; // Agrega texto al nuevo <div>.

header.appendChild(newDiv); // Agrega el <div> como hijo del elemento <header>.

header.removeChild(newDiv); // Elimina el <div> que se agregó.

```

  
### **Ejemplo: Modificación de atributos y estilos**

```javascript

newDiv.setAttribute("id", "saludo"); // Asigna un atributo id al <div>.

newDiv.style.color = "blue"; // Cambia el color del texto a azul.

```

  
### **Ejemplo: Eventos y suscriptores**

```javascript

newDiv.addEventListener("click", () => {

alert("Div clickeado!"); // Muestra una alerta al hacer clic en el <div>.

});

```


### **Ejercicio Práctico:**

Crear un formulario dinámico:

1. Crea un formulario con campos de texto y un botón de enviar.

2. Usa JavaScript para validar que todos los campos estén llenos al enviar.

3. Muestra un mensaje en el DOM indicando si el formulario es válido o no.

  

```javascript

const form = document.createElement("form");

const input = document.createElement("input");

input.setAttribute("type", "text");

input.setAttribute("placeholder", "Nombre");

const button = document.createElement("button");

button.textContent = "Enviar";

form.appendChild(input);

form.appendChild(button);

document.body.appendChild(form);

  

form.addEventListener("submit", (event) => {

event.preventDefault();

if (input.value.trim() === "") {

alert("Por favor, completa el campo");

} else {

alert(`Gracias, ${input.value}`);

}

});

```

  

---

  

## **2. Programación Orientada a Objetos**

  
### **Explicación:**

La POO (Programación Orientada a Objetos) organiza el código en objetos, que contienen propiedades y comportamientos (métodos). Esto facilita la reutilización y el mantenimiento del código.

### **Ejemplo: Declaración de clases y herencia**

```javascript

class Animal {

constructor(nombre) {

this.nombre = nombre;

}

  

hacerSonido() {

console.log(`${this.nombre} hace un sonido.`);

}

}

  

class Perro extends Animal {

hacerSonido() {

console.log(`${this.nombre} dice: guau!`);

}

}

  

const miPerro = new Perro("Firulais");

miPerro.hacerSonido(); // Firulais dice: guau!

```

  

### **Ejercicio Práctico:**

Crea una clase `Vehiculo` con propiedades como marca y modelo, y un método `detalles` que imprima esas propiedades. Crea una subclase `Coche` que extienda `Vehiculo` y añada una propiedad `puertas`. Implementa un método en `Coche` que imprima el número de puertas junto con los detalles del vehículo.

  

```javascript

class Vehiculo {

constructor(marca, modelo) {

this.marca = marca;

this.modelo = modelo;

}

  

detalles() {

console.log(`Marca: ${this.marca}, Modelo: ${this.modelo}`);

}

}

  

class Coche extends Vehiculo {

constructor(marca, modelo, puertas) {

super(marca, modelo);

this.puertas = puertas;

}

  

detallesCoche() {

console.log(`Marca: ${this.marca}, Modelo: ${this.modelo}, Puertas: ${this.puertas}`);

}

}

  

const miCoche = new Coche("Toyota", "Corolla", 4);

miCoche.detallesCoche();

```

  

---

  

## **3. Asincronía**

  

### **Explicación:**

La asincronía permite realizar tareas que toman tiempo (como peticiones a un servidor) sin bloquear la ejecución del programa.

  

### **Ejemplo: Promesas y async/await**

```javascript

const promesa = new Promise((resolve, reject) => {

setTimeout(() => {

const exito = true;

if (exito) resolve("Operación exitosa");

else reject("Error en la operación");

}, 2000);

});

  

promesa

.then((resultado) => console.log(resultado))

.catch((error) => console.error(error));

  

async function realizarOperacion() {

try {

const resultado = await promesa;

console.log(resultado);

} catch (error) {

console.error(error);

}

}

  

realizarOperacion();

```

  

### **Ejercicio Práctico:**

Crea una función que consulte una API (como `https://jsonplaceholder.typicode.com/posts`) y muestre los títulos de los primeros 5 elementos en el DOM.

  

```javascript

async function obtenerPosts() {

try {

const respuesta = await fetch("https://jsonplaceholder.typicode.com/posts");

const posts = await respuesta.json();

const lista = document.createElement("ul");

posts.slice(0, 5).forEach((post) => {

const item = document.createElement("li");

item.textContent = post.title;

lista.appendChild(item);

});

document.body.appendChild(lista);

} catch (error) {

console.error("Error al obtener los posts:", error);

}

}

  

obtenerPosts();

```

