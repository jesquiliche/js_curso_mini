---
sidebar_position: 2

---
# Capítulo 13: APIs Web y Fetch

## Introducción

Las APIs Web permiten la interacción entre tu aplicación y otros servicios a través de peticiones HTTP. En JavaScript, la Fetch API es una herramienta moderna y flexible para realizar estas peticiones. En este capítulo, exploraremos cómo usar la Fetch API para hacer peticiones HTTP, cómo manejar datos JSON, y los conceptos de CORS y seguridad en peticiones.

## Uso de Fetch API para hacer peticiones HTTP

### ¿Qué es la Fetch API?

La Fetch API proporciona una interfaz JavaScript para acceder y manipular partes del canal HTTP, tales como peticiones y respuestas. También provee un método global `fetch()` que permite hacer peticiones HTTP de manera sencilla.

### Haciendo una Petición GET

Para hacer una petición GET y obtener datos de un servidor, se utiliza el método `fetch()`. Este método devuelve una promesa que se resuelve con la respuesta de la petición.

**Ejemplo Básico de Fetch:**
```javascript
fetch('https://api.example.com/data')
    .then(response => response.json()) // Convierte la respuesta en JSON
    .then(data => {
        console.log(data); // Maneja los datos recibidos
    })
    .catch(error => {
        console.error('Error:', error); // Maneja errores
    });
```

### Haciendo una Petición POST

Para enviar datos a un servidor, se utiliza una petición POST. Se debe especificar el método, los headers y el cuerpo de la petición.

**Ejemplo Básico de Fetch con POST:**
```javascript
fetch('https://api.example.com/data', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({
        nombre: 'Juan',
        edad: 30
    })
})
.then(response => response.json())
.then(data => {
    console.log('Success:', data);
})
.catch(error => {
    console.error('Error:', error);
});
```

## Manejo de Datos JSON

### ¿Qué es JSON?

JSON (JavaScript Object Notation) es un formato ligero de intercambio de datos que es fácil de leer y escribir para los humanos, y fácil de parsear y generar para las máquinas. Es el formato más común para enviar y recibir datos en aplicaciones web.

### Parseando JSON

Cuando se recibe una respuesta en formato JSON, se debe parsear para convertirla en un objeto JavaScript utilizable.

**Ejemplo de Parseo de JSON:**
```javascript
fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => {
        console.log(data); // Ahora data es un objeto JavaScript
    });
```

### Enviando JSON

Para enviar datos en formato JSON, se debe convertir el objeto JavaScript en una cadena JSON utilizando `JSON.stringify()`.

**Ejemplo de Envío de JSON:**
```javascript
const data = {
    nombre: 'Juan',
    edad: 30
};

fetch('https://api.example.com/data', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify(data)
})
.then(response => response.json())
.then(data => {
    console.log('Success:', data);
})
.catch(error => {
    console.error('Error:', error);
});
```

## CORS y Seguridad en Peticiones

### ¿Qué es CORS?

CORS (Cross-Origin Resource Sharing) es un mecanismo que permite que los recursos de una página web sean solicitados desde otro dominio distinto al dominio desde el que se sirvió el recurso. CORS es un componente de la política de seguridad de los navegadores y está diseñado para prevenir ataques Cross-Site Scripting (XSS) y otras vulnerabilidades.

### Cómo Funciona CORS

Cuando se hace una petición a un dominio diferente, el navegador envía una petición preflight (de pre-verificación) utilizando el método OPTIONS para determinar si el servidor permite la solicitud. Si el servidor permite la solicitud, responde con los encabezados CORS adecuados, y el navegador permite la petición original.

### Configuración de CORS en el Servidor

Para permitir CORS, el servidor debe incluir los encabezados CORS en sus respuestas.

**Ejemplo de Configuración de CORS en Node.js:**
```javascript
const express = require('express');
const app = express();

app.use((req, res, next) => {
    res.header('Access-Control-Allow-Origin', '*'); // Permitir todos los orígenes
    res.header('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE'); // Permitir métodos específicos
    res.header('Access-Control-Allow-Headers', 'Content-Type, Authorization'); // Permitir headers específicos
    next();
});

app.get('/data', (req, res) => {
    res.json({ message: 'Datos recibidos correctamente' });
});

app.listen(3000, () => {
    console.log('Servidor corriendo en puerto 3000');
});
```

### Seguridad en Peticiones

La seguridad en peticiones es crucial para proteger tanto a los usuarios como a los servidores de posibles ataques. Aquí hay algunas prácticas recomendadas:

1. **Validar y Sanitizar Entradas:** Siempre valida y sanitiza los datos que recibes para prevenir inyecciones de código y otros ataques.
2. **Usar HTTPS:** Asegúrate de que las peticiones se realicen sobre HTTPS para proteger la integridad y confidencialidad de los datos.
3. **Autenticación y Autorización:** Implementa mecanismos de autenticación y autorización para asegurar que solo los usuarios legítimos puedan acceder y modificar los recursos.

## Conclusión

La Fetch API es una herramienta poderosa y flexible para realizar peticiones HTTP en JavaScript. Entender cómo manejar datos JSON, así como los conceptos de CORS y seguridad en peticiones, es esencial para crear aplicaciones web robustas y seguras. Con este conocimiento, estarás mejor preparado para interactuar con APIs y manejar datos de manera eficiente en tus proyectos.
