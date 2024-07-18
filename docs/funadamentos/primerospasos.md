---
sidebar_position: 1
---

# Primeros Pasos con JavaScript

JavaScript es uno de los lenguajes de programación más populares y versátiles, especialmente en el desarrollo web. Para comenzar con JavaScript, es fundamental tener un entorno de desarrollo configurado adecuadamente y entender cómo escribir y ejecutar tus primeros scripts. En este capítulo, exploraremos estos aspectos esenciales.

---

## Instalación y Configuración del Entorno de Desarrollo

Para escribir y ejecutar código JavaScript, necesitas un entorno de desarrollo adecuado. A continuación, se describen los pasos para instalar y configurar tu entorno:

## 1. Instalación de un Editor de Código

Un editor de código es una herramienta esencial para escribir código de manera eficiente. Hay varios editores de código disponibles, pero algunos de los más populares son:

- **Visual Studio Code (VS Code)**: Es gratuito, altamente configurable y tiene una gran cantidad de extensiones disponibles para mejorar tu experiencia de desarrollo. [Descargar VS Code](https://code.visualstudio.com/).

- **Sublime Text**: Un editor rápido y ligero con soporte para muchos lenguajes de programación. [Descargar Sublime Text](https://www.sublimetext.com/).

- **Atom**: Un editor de código gratuito y de código abierto, desarrollado por GitHub. [Descargar Atom](https://atom.io/).

Nosotros para nuestras instalaremos **Visual Studio Code**. Para descargar Vs Code, puede dirigirse al siguiente enlace https://code.visualstudio.com/download. 

![vsCode](/images/vscode.png)

**Visual Studio Code** cuenta con versiones para **Mac**,**Linux**. Escoja la versión que se adapte a su sistema operativo e installela. La instalación por lo menos en **Windows** es an simple como pulsar siguiente, siguiente.

## 2. Instalación de Node.js

Node.js es un entorno de ejecución para JavaScript fuera del navegador. Aunque no es estrictamente necesario para escribir JavaScript, es útil para ejecutar scripts localmente y para utilizar herramientas de desarrollo como npm (Node Package Manager).

- **Descargar Node.js**: Visita [nodejs.org](https://nodejs.org/) y descarga la versión LTS (Long Term Support).

- **Instalación**: Sigue las instrucciones del instalador. Una vez instalado, puedes verificar la instalación abriendo una terminal y ejecutando los comandos:
  ```sh
  node -v
  npm -v
  ```

### 3. Configuración de Extensiones en el Editor de Código

Si estás utilizando VS Code, puedes mejorar tu entorno de desarrollo instalando algunas extensiones útiles:

- **ESLint**: Para mantener un código limpio y consistente.
- **Prettier**: Para formatear el código automáticamente.
- **Live Server**: Para ejecutar un servidor local y ver los cambios en tiempo real.

Para instalar estas extensiones, abre VS Code, ve a la sección de extensiones (ícono de cuadrado en la barra lateral) y busca las extensiones mencionadas para instalarlas.

---

## Primer Script y Ejecución en el Navegador

Ahora que tienes tu entorno configurado, es hora de escribir y ejecutar tu primer script en JavaScript.

### 1. Crear un Archivo HTML

Primero, crea un archivo HTML básico que incluya tu script de JavaScript. Abre tu editor de código y crea un nuevo archivo llamado `index.html` con el siguiente contenido:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Primer Script</title>
</head>
<body>
    <h1>Hola, Mundo!</h1>
    <script src="script.js"></script>
</body>
</html>
```

### 2. Escribir el Script de JavaScript

Crea un archivo llamado `script.js` en el mismo directorio que `index.html`. Este archivo contendrá tu primer script de JavaScript. Abre `script.js` y escribe el siguiente código:

```javascript
// script.js
console.log('Hola, Mundo!');
```

Este script simplemente imprimirá "Hola, Mundo!" en la consola del navegador.

### 3. Ejecutar el Script en el Navegador

Para ver tu script en acción, abre el archivo `index.html` en tu navegador web. Puedes hacer esto arrastrando el archivo a una ventana del navegador o haciendo clic derecho sobre el archivo y seleccionando "Abrir con" y eligiendo tu navegador preferido.

Una vez abierto, deberías ver "Hola, Mundo!" en la página. Para ver el mensaje en la consola, abre las herramientas de desarrollador del navegador:

- **Google Chrome**: Haz clic derecho en la página y selecciona "Inspeccionar" o presiona `Ctrl+Shift+I` (Windows/Linux) o `Cmd+Option+I` (Mac).
- **Mozilla Firefox**: Haz clic derecho en la página y selecciona "Inspeccionar" o presiona `Ctrl+Shift+I` (Windows/Linux) o `Cmd+Option+I` (Mac).

En la pestaña "Consola", deberías ver el mensaje "Hola, Mundo!".
