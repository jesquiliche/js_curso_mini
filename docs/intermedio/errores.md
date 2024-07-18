---
sidebar_position: 3
---

# Capítulo 10: Manejo de Errores y Depuración en JavaScript

## Introducción
El manejo de errores y la depuración son habilidades esenciales para cualquier desarrollador. En este capítulo, aprenderás cómo manejar errores usando `try...catch`, cómo usar herramientas de depuración en el navegador y cómo utilizar mensajes de consola y logging para rastrear y solucionar problemas en tu código.

## Try...catch

### Introducción a Try...catch
El bloque `try...catch` te permite manejar errores en tu código sin detener la ejecución del programa. Es útil para situaciones donde un error puede ocurrir y quieres asegurarte de que tu programa puede manejarlo de manera adecuada.

### Sintaxis Básica

**JavaScript:**
```javascript
try {
    // Código que puede lanzar un error
    let resultado = 10 / 0;
    console.log(resultado);
} catch (error) {
    // Código que maneja el error
    console.error('Ocurrió un error:', error);
} finally {
    // Código que se ejecuta siempre, ocurra o no un error
    console.log('Ejecución finalizada.');
}
```

**Explicación:**
- `try { ... }`: Contiene el código que puede lanzar un error.
- `catch (error) { ... }`: Se ejecuta si ocurre un error en el bloque `try`. El parámetro `error` contiene información sobre el error.
- `finally { ... }`: Opcional. Se ejecuta siempre, sin importar si ocurrió un error o no.

### Ejemplo Práctico

**HTML:**
```html
<input type="text" id="miInput" placeholder="Escribe un número">
<button id="miBoton">Dividir por 2</button>
<p id="resultado"></p>
```

**JavaScript:**
```javascript
const input = document.getElementById('miInput');
const boton = document.getElementById('miBoton');
const resultado = document.getElementById('resultado');

boton.addEventListener('click', function() {
    try {
        let valor = parseInt(input.value);
        if (isNaN(valor)) {
            throw new Error('Por favor, introduce un número válido');
        }
        resultado.innerText = `El resultado es: ${valor / 2}`;
    } catch (error) {
        resultado.innerText = error.message;
    }
});
```

## Uso de Herramientas de Depuración en el Navegador

### Herramientas de Desarrollo

Los navegadores modernos vienen con herramientas de desarrollo que te permiten inspeccionar el DOM, ver mensajes de consola, establecer puntos de interrupción y mucho más. La más comúnmente utilizada es la de Google Chrome.

### Cómo Acceder a las Herramientas de Desarrollo

1. **Google Chrome:** Presiona `Ctrl + Shift + I` (o `Cmd + Option + I` en Mac) o haz clic derecho en la página y selecciona "Inspeccionar".
2. **Mozilla Firefox:** Presiona `Ctrl + Shift + I` (o `Cmd + Option + I` en Mac) o haz clic derecho en la página y selecciona "Inspeccionar".

### Uso de Puntos de Interrupción

Los puntos de interrupción te permiten pausar la ejecución del código en una línea específica para inspeccionar el estado de la aplicación.

**JavaScript:**
```javascript
function dividir(a, b) {
    debugger; // Pausa la ejecución aquí
    return a / b;
}

dividir(10, 2);
```

**Pasos para Usar Puntos de Interrupción:**
1. Abre las herramientas de desarrollo.
2. Ve a la pestaña "Sources" o "Debugger".
3. Encuentra tu archivo JavaScript y haz clic en el número de línea donde quieres establecer un punto de interrupción.
4. La ejecución se pausará en esa línea cuando se ejecute el código, permitiéndote inspeccionar variables y el flujo del programa.

## Mensajes de Consola y Logging

### Uso de `console.log`

`console.log` es una herramienta básica pero poderosa para imprimir mensajes y valores en la consola del navegador, ayudándote a entender lo que está sucediendo en tu código.

**JavaScript:**
```javascript
const nombre = 'Juan';
console.log('El nombre es:', nombre);
```

### Otros Métodos de Consola

- `console.error()`: Para imprimir mensajes de error.
- `console.warn()`: Para imprimir advertencias.
- `console.table()`: Para imprimir tablas.

**Ejemplo:**
```javascript
const usuario = { nombre: 'Juan', edad: 30 };
console.error('Esto es un mensaje de error');
console.warn('Esto es una advertencia');
console.table(usuario);
```

### Ejemplo Práctico de Logging

**HTML:**
```html
<input type="text" id="miInput" placeholder="Escribe algo">
<button id="miBoton">Enviar</button>
```

**JavaScript:**
```javascript
const input = document.getElementById('miInput');
const boton = document.getElementById('miBoton');

boton.addEventListener('click', function() {
    console.log('Botón clicado');
    console.log('Valor del input:', input.value);
    if (input.value === '') {
        console.warn('El input está vacío');
    }
});
```

## Conclusión

El manejo de errores y la depuración son cruciales para el desarrollo de aplicaciones robustas y libres de errores. Usar `try...catch` te permite manejar errores sin interrumpir la ejecución del programa, las herramientas de depuración del navegador te ofrecen un control detallado sobre tu código, y los mensajes de consola te ayudan a rastrear y entender el flujo de tu aplicación. Con estas habilidades, estarás mejor equipado para escribir código de alta calidad y solucionar problemas de manera eficiente.