---
sidebar_position: 4
---

# Funciones

## Introducción
Las funciones son bloques de código reutilizables que realizan una tarea específica. En JavaScript, las funciones son ciudadanos de primera clase, lo que significa que pueden ser asignadas a variables, pasadas como argumentos a otras funciones y devueltas desde otras funciones. Este capítulo explorará cómo declarar y usar funciones, trabajar con parámetros y valores de retorno, y entender el scope y el contexto (`this`) en JavaScript.

## Declaración y Expresión de Funciones

### Declaración de Funciones
Una declaración de función define una función con el nombre proporcionado y un cuerpo de código que se ejecuta cuando se llama a la función.

**Sintaxis:**

```javascript
function nombreDeFuncion(parámetros) {
    // cuerpo de la función
}
```

**Ejemplo:**

```javascript
function saludar(nombre) {
    console.log("Hola, " + nombre + "!");
}

saludar("Juan"); // Salida: "Hola, Juan!"
```

### Expresión de Funciones
Una expresión de función define una función dentro de una expresión y puede ser anónima (sin nombre). Las expresiones de funciones no se elevan (hoisted), lo que significa que no se pueden llamar antes de ser definidas.

**Sintaxis:**

```javascript
const nombreDeFuncion = function(parámetros) {
    // cuerpo de la función
};
```

**Ejemplo:**

```javascript
const saludar = function(nombre) {
    console.log("Hola, " + nombre + "!");
};

saludar("María"); // Salida: "Hola, María!"
```

### Funciones Flecha
Las funciones flecha proporcionan una sintaxis más concisa para escribir funciones. No tienen su propio `this`, `arguments`, `super` o `new.target`.

**Sintaxis:**

```javascript
const nombreDeFuncion = (parámetros) => {
    // cuerpo de la función
};
```

**Ejemplo:**

```javascript
const saludar = (nombre) => {
    console.log("Hola, " + nombre + "!");
};

saludar("Carlos"); // Salida: "Hola, Carlos!"
```

## Parámetros y Valores de Retorno

### Parámetros
Las funciones pueden aceptar parámetros, que son valores pasados a la función cuando se llama.

**Ejemplo:**

```javascript
function sumar(a, b) {
    return a + b;
}

console.log(sumar(2, 3)); // Salida: 5
```

### Valores por Defecto
Puedes asignar valores por defecto a los parámetros para que se utilicen si no se proporciona ningún valor al llamar a la función.

**Ejemplo:**

```javascript
function saludar(nombre = "Desconocido") {
    console.log("Hola, " + nombre + "!");
}

saludar(); // Salida: "Hola, Desconocido!"
```

### Valores de Retorno
Las funciones pueden devolver valores usando la palabra clave `return`. Si no se especifica un valor de retorno, la función devuelve `undefined` por defecto.

**Ejemplo:**

```javascript
function multiplicar(a, b) {
    return a * b;
}

let resultado = multiplicar(4, 5);
console.log(resultado); // Salida: 20
```

### Scope y Contexto (`this`)

### Scope
El scope define el contexto en el cual las variables están disponibles para su uso. JavaScript tiene dos tipos principales de scope: global y local.

- **Scope Global**: Variables declaradas fuera de cualquier función tienen un scope global y están disponibles en cualquier parte del código.

- **Scope Local**: Variables declaradas dentro de una función tienen un scope local y solo están disponibles dentro de esa función.

**Ejemplo:**

```javascript
let globalVar = "Soy global";

function miFuncion() {
    let localVar = "Soy local";
    console.log(globalVar); // Salida: "Soy global"
    console.log(localVar);  // Salida: "Soy local"
}

miFuncion();
console.log(localVar); // Error: localVar is not defined
```

### Contexto (`this`)
El contexto, o `this`, se refiere al objeto desde el cual se invocó la función. El valor de `this` depende de cómo se llama a la función.

**En el contexto global:**

```javascript
console.log(this); // En el navegador, `this` se refiere al objeto `window`.
```

**Dentro de un objeto:**

```javascript
const persona = {
    nombre: "Juan",
    saludar: function() {
        console.log("Hola, " + this.nombre + "!");
    }
};

persona.saludar(); // Salida: "Hola, Juan!" (this se refiere a persona)
```

**En una función:**

```javascript
function mostrarThis() {
    console.log(this);
}

mostrarThis(); // En el navegador, `this` se refiere al objeto `window`.
```

**En una función flecha:**

Las funciones flecha no tienen su propio `this`. Heredan el `this` del contexto en el cual fueron definidas.

```javascript
const persona = {
    nombre: "Ana",
    saludar: () => {
        console.log("Hola, " + this.nombre + "!"); // `this` se refiere al contexto global
    }
};

persona.saludar(); // Salida: "Hola, undefined!"
```

## Conclusión
Las funciones son una parte fundamental de JavaScript, permitiendo encapsular lógica y reutilizar código. Entender cómo declarar y usar funciones, trabajar con parámetros y valores de retorno, y manejar el scope y el contexto (`this`) te permitirá escribir código más modular y eficiente. Con la práctica, te familiarizarás con las distintas formas de definir y utilizar funciones en tus programas JavaScript.
