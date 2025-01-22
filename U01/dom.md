#DOM

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
	1. Campo "Email"
	2. Campo "Password"
	3. Botón Enviar

2. Usa JavaScript para validar que todos los campos estén llenos al enviar.

3. Muestra un mensaje en el DOM indicando si el formulario es válido o no.


```javascript

<script>
	initForm()
	function initForm(){
		//
	}
</script>

```

