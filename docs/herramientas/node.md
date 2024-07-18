---
sidebar_position: 3

---
# Desarrollo con Node.js

Node.js es un entorno de ejecución para JavaScript que permite a los desarrolladores crear aplicaciones del lado del servidor. Es rápido, escalable y está basado en el motor V8 de Google. En este capítulo, aprenderás cómo crear un servidor básico con Node.js, utilizar el framework Express y conectar tu aplicación a una base de datos.

---

## Creación de un Servidor Básico

Para empezar, vamos a crear un servidor básico con Node.js. Necesitarás tener Node.js instalado en tu máquina.

### Instalación de Node.js

Descarga e instala Node.js desde su [sitio oficial](https://nodejs.org/). Para verificar la instalación, ejecuta:

```bash
node -v
npm -v
```

### Creación del Proyecto

Crea un nuevo directorio para tu proyecto y navega a él en tu terminal. Luego, inicializa un proyecto de Node.js:

```bash
mkdir my-node-project
cd my-node-project
npm init -y
```

### Creación del Servidor Básico

Crea un archivo llamado `server.js` y añade el siguiente código:

```javascript
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello, World!\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

Para ejecutar el servidor, usa el comando:

```bash
node server.js
```

Abre tu navegador y navega a `http://127.0.0.1:3000/`. Deberías ver el mensaje "Hello, World!".

---

## Uso de Express

Express es un framework minimalista y flexible para Node.js que proporciona un robusto conjunto de características para aplicaciones web y móviles.

### Instalación de Express

Instala Express mediante npm:

```bash
npm install express
```

### Creación de un Servidor con Express

Modifica el archivo `server.js` para utilizar Express:

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}/`);
});
```

Ejecuta el servidor de nuevo:

```bash
node server.js
```

Navega a `http://localhost:3000/` y deberías ver el mensaje "Hello, World!".

### Rutas y Middlewares en Express

Express permite definir múltiples rutas y utilizar middlewares para manejar las solicitudes. Añade algunas rutas adicionales y un middleware:

```javascript
const express = require('express');
const app = express();
const port = 3000;

// Middleware para todas las rutas
app.use((req, res, next) => {
  console.log(`${req.method} request for '${req.url}'`);
  next();
});

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.get('/about', (req, res) => {
  res.send('About Page');
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}/`);
});
```

Con esto, cada solicitud a cualquier ruta será registrada en la consola.

---

## Conexión a Bases de Datos

Node.js puede conectarse a varias bases de datos como MongoDB, MySQL, PostgreSQL, entre otras. Vamos a ver cómo conectar una aplicación Node.js a MongoDB utilizando Mongoose.

### Instalación de MongoDB y Mongoose

Primero, asegúrate de tener MongoDB instalado y en funcionamiento. Luego, instala Mongoose, que es una biblioteca de modelado de datos para MongoDB y Node.js.

```bash
npm install mongoose
```

##### Conexión a MongoDB con Mongoose

Crea un archivo llamado `database.js` y añade el siguiente código para conectarte a MongoDB:

```javascript
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/mydatabase', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

const db = mongoose.connection;
db.on('error', console.error.bind(console, 'connection error:'));
db.once('open', () => {
  console.log('Connected to MongoDB');
});
```

Luego, modifica `server.js` para incluir esta conexión:

```javascript
const express = require('express');
const mongoose = require('mongoose');
const app = express();
const port = 3000;

mongoose.connect('mongodb://localhost:27017/mydatabase', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

const db = mongoose.connection;
db.on('error', console.error.bind(console, 'connection error:'));
db.once('open', () => {
  console.log('Connected to MongoDB');
});

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}/`);
});
```

### Definición de un Modelo con Mongoose

Define un modelo para tu base de datos MongoDB. Crea un archivo llamado `models/User.js`:

```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  name: String,
  email: String,
  password: String,
});

const User = mongoose.model('User', userSchema);

module.exports = User;
```

### Uso del Modelo en el Servidor

Modifica `server.js` para utilizar el modelo `User`:

```javascript
const express = require('express');
const mongoose = require('mongoose');
const User = require('./models/User');
const app = express();
const port = 3000;

mongoose.connect('mongodb://localhost:27017/mydatabase', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

const db = mongoose.connection;
db.on('error', console.error.bind(console, 'connection error:'));
db.once('open', () => {
  console.log('Connected to MongoDB');
});

// Middleware para parsear JSON
app.use(express.json());

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

// Ruta para crear un nuevo usuario
app.post('/users', async (req, res) => {
  const user = new User(req.body);
  try {
    await user.save();
    res.status(201).send(user);
  } catch (error) {
    res.status(400).send(error);
  }
});

// Ruta para obtener todos los usuarios
app.get('/users', async (req, res) => {
  try {
    const users = await User.find();
    res.send(users);
  } catch (error) {
    res.status(500).send(error);
  }
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}/`);
});
```

### Actualización y Eliminación de Usuarios

Añadimos rutas adicionales para actualizar y eliminar usuarios:

```javascript
// Ruta para actualizar un usuario
app.put('/users/:id', async (req, res) => {
  try {
    const user = await User.findByIdAndUpdate(req.params.id, req.body, { new: true, runValidators: true });
    if (!user) {
      return res.status(404).send();
    }
    res.send(user);
  } catch (error) {
    res.status(400).send(error);
  }
});

// Ruta para eliminar un usuario
app.delete('/users/:id', async (req, res) => {
  try {
    const user = await User.findByIdAndDelete(req.params.id);
    if (!user) {
      return res.status(404).send();
    }
    res.send(user);
  } catch (error) {
    res.status(500).send(error);
  }
});
```

Con estas nuevas rutas, puedes realizar operaciones CRUD (Crear, Leer, Actualizar y Eliminar) completas sobre el modelo `User`.

---

## Conclusión

En este capítulo, has aprendido a configurar un servidor básico con Node.js y Express, a manejar rutas y middlewares, y a conectar tu aplicación a una base de datos MongoDB utilizando Mongoose. Con estas habilidades, puedes construir aplicaciones web del lado del servidor que son escalables y eficientes. Node.js, junto con Express y Mongoose, ofrece una plataforma poderosa para el desarrollo backend moderno, permitiéndote gestionar tanto el servidor como la base de datos de manera efectiva.