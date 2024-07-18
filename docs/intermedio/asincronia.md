---
sidebar_position: 4

---
# Capítulo 11: Asincronía en JavaScript

## Introducción

La asincronía es una característica fundamental en JavaScript que permite realizar operaciones sin bloquear el hilo principal de ejecución. Esto es crucial para aplicaciones web que necesitan ser rápidas y responsivas. En este capítulo, exploraremos tres formas principales de manejar la asincronía en JavaScript: callbacks, promesas y `async/await`.

## Callbacks

### ¿Qué es un Callback?

Un callback es una función que se pasa como argumento a otra función y se ejecuta después de que la primera función haya completado su tarea. Los callbacks son una de las formas más antiguas y básicas de manejar la asincronía en JavaScript.

### Ejemplo Básico de Callback

**HTML:**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Callbacks en JavaScript</title>
</head>
<body>
    <button id="miBoton">Hacer algo</button>
    <script src="app.js"></script>
</body>
</html>
```

**JavaScript (app.js):**
```javascript
const boton = document.getElementById('miBoton');

function hacerAlgoDespues(callback) {
    console.log('Haciendo algo...');
    setTimeout(callback, 2000); // Simula una tarea asincrónica con un retraso de 2 segundos
}

boton.addEventListener('click', function() {
    hacerAlgoDespues(function() {
        console.log('Hecho después de 2 segundos');
    });
});
```

### Callbacks Anidados y el "Callback Hell"

Los callbacks pueden volverse difíciles de manejar cuando se anidan varios uno dentro de otro, lo que se conoce como "callback hell".

**Ejemplo de Callback Hell:**
```javascript
hacerAlgoDespues(function() {
    console.log('Primera tarea completa');
    hacerAlgoDespues(function() {
        console.log('Segunda tarea completa');
        hacerAlgoDespues(function() {
            console.log('Tercera tarea completa');
        });
    });
});
```

## Promesas

### ¿Qué es una Promesa?

Una promesa es un objeto que representa un valor que puede estar disponible ahora, en el futuro o nunca. Las promesas proporcionan una forma más limpia y manejable de trabajar con asincronía comparado con los callbacks anidados.

### Creación y Uso de Promesas

**Ejemplo Básico de Promesa:**
```javascript
const miPromesa = new Promise((resolve, reject) => {
    setTimeout(() => {
        const exito = true; // Simula una condición de éxito o fracaso
        if (exito) {
            resolve('Operación exitosa');
        } else {
            reject('Operación fallida');
        }
    }, 2000);
});

miPromesa
    .then((mensaje) => {
        console.log(mensaje); // 'Operación exitosa'
    })
    .catch((error) => {
        console.error(error); // 'Operación fallida'
    });
```

### Encadenamiento de Promesas

Las promesas permiten el encadenamiento, lo que facilita manejar múltiples tareas asincrónicas de manera secuencial.

**Ejemplo de Encadenamiento:**
```javascript
miPromesa
    .then((mensaje) => {
        console.log(mensaje); // 'Operación exitosa'
        return 'Siguiente operación';
    })
    .then((mensaje) => {
        console.log(mensaje); // 'Siguiente operación'
    })
    .catch((error) => {
        console.error(error); // 'Operación fallida'
    });
```

## Async/Await

### ¿Qué es Async/Await?

`async/await` es una sintaxis más moderna y legible para trabajar con promesas. `async` se utiliza para declarar una función asíncrona, y `await` se utiliza dentro de funciones asíncronas para esperar una promesa.

### Funciones Asíncronas

**Ejemplo Básico de Async/Await:**
```javascript
async function miFuncionAsincrona() {
    try {
        const mensaje = await miPromesa;
        console.log(mensaje); // 'Operación exitosa'
    } catch (error) {
        console.error(error); // 'Operación fallida'
    }
}

miFuncionAsincrona();
```

### Ventajas de Async/Await

`async/await` hace que el código asincrónico se parezca más al código sincrónico, lo que lo hace más fácil de entender y mantener.

### Ejemplo Práctico Completo

**HTML:**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Async/Await en JavaScript</title>
</head>
<body>
    <button id="miBoton">Cargar datos</button>
    <div id="resultado"></div>
    <script src="app.js"></script>
</body>
</html>
```

**JavaScript (app.js):**
```javascript
const boton = document.getElementById('miBoton');
const resultado = document.getElementById('resultado');

boton.addEventListener('click', async function() {
    try {
        const datos = await cargarDatos();
        resultado.innerText = datos;
    } catch (error) {
        resultado.innerText = 'Error al cargar datos';
        console.error(error);
    }
});

function cargarDatos() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const exito = true; // Simula una condición de éxito o fracaso
            if (exito) {
                resolve('Datos cargados correctamente');
            } else {
                reject('Error al cargar datos');
            }
        }, 2000);
    });
}
```

## Conclusión

La asincronía es una parte esencial de JavaScript que permite crear aplicaciones web rápidas y eficientes. Desde los callbacks básicos hasta las promesas y la sintaxis moderna de `async/await`, cada método ofrece diferentes formas de manejar la asincronía. Entender y utilizar estas técnicas te permitirá escribir código más claro, manejable y eficiente.
