---
sidebar_position: 1

---
# Capítulo 12: Módulos en JavaScript

## Introducción

Los módulos son una forma de organizar y reutilizar código en JavaScript. Permiten dividir el código en piezas más pequeñas y manejables, cada una con su propio contexto. En este capítulo, exploraremos cómo importar y exportar módulos en JavaScript y cómo usar módulos tanto en Node.js como en el navegador.

## Importación y Exportación de Módulos

### Exportación de Módulos

Para exportar código desde un archivo JavaScript, se utilizan las palabras clave `export` y `export default`.

#### Exportación Nombrada

Con la exportación nombrada, puedes exportar múltiples elementos desde un archivo.

**math.js:**
```javascript
export const PI = 3.14159;

export function sumar(a, b) {
    return a + b;
}

export function restar(a, b) {
    return a - b;
}
```

#### Exportación por Defecto

Con la exportación por defecto, se puede exportar un solo valor desde un archivo. Es útil cuando quieres que el módulo exporte solo una cosa.

**mensajes.js:**
```javascript
export default function saludar(nombre) {
    return `Hola, ${nombre}!`;
}
```

### Importación de Módulos

Para importar código desde otro archivo, se utiliza la palabra clave `import`.

#### Importación Nombrada

Se puede importar uno o varios elementos específicos de un módulo.

**app.js:**
```javascript
import { PI, sumar, restar } from './math.js';

console.log(`El valor de PI es: ${PI}`);
console.log(`La suma de 3 y 4 es: ${sumar(3, 4)}`);
console.log(`La resta de 5 y 2 es: ${restar(5, 2)}`);
```

#### Importación por Defecto

Se puede importar el valor exportado por defecto de un módulo.

**app.js:**
```javascript
import saludar from './mensajes.js';

console.log(saludar('Mundo'));
```

#### Importación Combinada

También se pueden combinar importaciones nombradas y por defecto.

**app.js:**
```javascript
import saludar, { PI, sumar, restar } from './math.js';

console.log(saludar('Mundo'));
console.log(`El valor de PI es: ${PI}`);
console.log(`La suma de 3 y 4 es: ${sumar(3, 4)}`);
console.log(`La resta de 5 y 2 es: ${restar(5, 2)}`);
```

## Uso de Módulos en Node.js

Node.js utiliza un sistema de módulos basado en CommonJS. Cada archivo en Node.js es un módulo que puede exportar y requerir otros módulos.

### Exportación de Módulos en Node.js

En Node.js, se utiliza `module.exports` para exportar código desde un archivo.

**math.js:**
```javascript
const PI = 3.14159;

function sumar(a, b) {
    return a + b;
}

function restar(a, b) {
    return a - b;
}

module.exports = {
    PI,
    sumar,
    restar
};
```

### Importación de Módulos en Node.js

Para importar módulos en Node.js, se utiliza `require`.

**app.js:**
```javascript
const math = require('./math.js');

console.log(`El valor de PI es: ${math.PI}`);
console.log(`La suma de 3 y 4 es: ${math.sumar(3, 4)}`);
console.log(`La resta de 5 y 2 es: ${math.restar(5, 2)}`);
```

## Uso de Módulos en el Navegador

Los navegadores modernos soportan la sintaxis de módulos ES6 de manera nativa, permitiendo la importación y exportación de módulos directamente en el navegador.

### Configuración del HTML

Para usar módulos en el navegador, se debe incluir el atributo `type="module"` en la etiqueta `<script>`.

**index.html:**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Uso de Módulos en el Navegador</title>
</head>
<body>
    <script type="module" src="app.js"></script>
</body>
</html>
```

### Ejemplo Práctico en el Navegador

**math.js:**
```javascript
export const PI = 3.14159;

export function sumar(a, b) {
    return a + b;
}

export function restar(a, b) {
    return a - b;
}
```

**app.js:**
```javascript
import { PI, sumar, restar } from './math.js';

console.log(`El valor de PI es: ${PI}`);
console.log(`La suma de 3 y 4 es: ${sumar(3, 4)}`);
console.log(`La resta de 5 y 2 es: ${restar(5, 2)}`);
```

## Conclusión

El uso de módulos en JavaScript es una práctica esencial para organizar y reutilizar código de manera eficiente. Tanto en Node.js como en el navegador, la capacidad de dividir el código en módulos más pequeños y manejables facilita el mantenimiento y la escalabilidad de las aplicaciones. Con la comprensión de cómo exportar e importar módulos, estarás bien preparado para escribir código modular y limpio en tus proyectos.
