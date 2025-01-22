#Fundamentos de Javascript

### **1.1 Variables**

Las variables son contenedores para almacenar datos. En JavaScript, se pueden declarar usando `var`, `let` o `const`.

- `var`: Ámbito global o de función (se recomienda evitarlo).

- `let`: Ámbito de bloque, útil para variables que cambian.

- `const`: Ámbito de bloque, útil para valores constantes.

  

#### **Ejemplo: Declaración de variables**

```javascript

var name = "Juan"; // Variable global o de función

let age = 25; // Variable de bloque que puede cambiar

const country = "México"; // Variable de bloque que no cambia

console.log(`Hola, soy ${name}, tengo ${age} años y vivo en ${conuntry}.`);

```

  

### **1.2 Tipos de Datos**

Los principales tipos de datos en JavaScript incluyen:

- Primitivos: `string`, `number`, `boolean`, `null`, `undefined`.

- Complejos: `object` (incluyendo arrays y funciones).

  

#### **Ejemplo: Tipos de datos**

```javascript

const stringType = "Hola, mundo"; // string

const numberType = 42; // number

const isTrue = true; // boolean

const nullType = null; // null

const undefinedType = undefined; // undefined

const objectType = { name: "Ana", age: 30 }; // object

```

  

### **1.3 Operadores**

Los operadores son símbolos o palabras clave que realizan operaciones sobre datos.

- **Aritméticos:** `+`, `-`, `*`, `/`, `%`.

- **Relacionales:** `>`, `<`, `>=`, `<=`, `==`, `===`, `!=`, `!==`.

- **Lógicos:** `&&`, `||`, `!`.

  

#### **Ejemplo: Operadores**

```javascript

const a = 10;

const b = 5;

console.log(a + b); // 15

console.log(a > b); // true

console.log(a > 0 && b > 0); // true

```

  

### **1.4 Estructuras de Control**

Las estructuras de control determinan el flujo del programa, como condicionales y bucles.

- **Condicionales:** `if`, `else if`, `else`, `switch`.

- **Bucles:** `for`, `while`, `do...while`.

  

#### **Ejemplo: Condicionales**

```javascript

const age = 18;

if (age >= 18) {

console.log("Eres mayor de edad.");

} else {

console.log("Eres menor de edad.");

}

```

  

#### **Ejemplo: Bucles**

```javascript

for (let i = 0; i < 5; i++) {

console.log(`Iteración ${i}`);

}

```

  

---

  

## **2. Funciones en JavaScript**

Las funciones son bloques de código que realizan una tarea específica. Pueden aceptar argumentos y devolver valores.


### **2.1 Tipos de Funciones**

1. **Declaradas:** Definidas con la palabra clave `function`.

2. **Expresadas:** Asignadas a una variable.

3. **Flecha:** Introducidas en ES6, son más concisas y no tienen su propio `this`.

  

#### **Ejemplo: Declaración de Función**

```javascript

function hello(name) {

return `Hola, ${name}!`;

}

console.log(hello("Efrain")); // Hola, Efrain!

```

  

#### **Ejemplo: Función Expresada**

```javascript

const add = function (a, b) {

return a + b;

};

console.log(add(3, 7)); // 10

```

  

#### **Ejemplo: Función Flecha**

```javascript

const multiply = (a, b) => a * b;

console.log(multiply(4, 5)); // 20

```

  

### **2.2 Ámbito (Scope)**

El ámbito define dónde se puede acceder a una variable.

- **Ámbito Global:** Disponible en todo el programa.

- **Ámbito de Bloque:** Limitado al bloque donde se define.

  

#### **Ejemplo: Ámbito**

```javascript

let global = "Estoy en el ámbito global";

  

function scopeExcample() {

let local = "Estoy en el ámbito local";

console.log(global); // Funciona

console.log(local); // Funciona

}

scopeExcample();

// console.log(local); // Error: local no está definido

```
