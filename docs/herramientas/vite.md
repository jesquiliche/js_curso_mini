---
sidebar_position: 1

---
# Configuración de un Entorno de Desarrollo Moderno

En este capítulo, aprenderás cómo configurar un entorno de desarrollo moderno para proyectos en TypeScript utilizando Vite. Exploraremos el uso de npm/yarn, la configuración de Vite, y la implementación de herramientas de linting y formateo con ESLint y Prettier.

---

## Uso de npm/yarn

**npm** y **yarn** son gestores de paquetes para JavaScript que te permiten instalar, compartir y gestionar dependencias en tus proyectos.

## Instalación de npm

npm viene preinstalado con Node.js. Para verificar que tienes npm instalado, ejecuta:

```bash
node -v
npm -v
```

## Instalación de Yarn

Yarn se puede instalar globalmente usando npm:

```bash
npm install -g yarn
```

## Inicialización del Proyecto

Inicia un nuevo proyecto y crea un archivo `package.json`:

```bash
npm init -y
# o
yarn init -y
```

---

## Configuración de Vite

**Vite** proporciona una configuración rápida y optimizada para proyectos frontend. Vamos a configurarlo para un proyecto TypeScript.

### Instalación de Vite

Para crear un nuevo proyecto con Vite, puedes usar el comando `create-vite`:

```bash
npm create vite@latest my-vite-project --template vanilla-ts
# o
yarn create vite@latest my-vite-project --template vanilla-ts
```

Esto creará un nuevo proyecto con Vite y TypeScript. Navega al directorio del proyecto:

```bash
cd my-vite-project
```

### Estructura del Proyecto

El comando anterior crea una estructura básica de proyecto. Echa un vistazo a los archivos clave:

- `index.html`: El punto de entrada HTML.
- `src/main.ts`: El punto de entrada de JavaScript/TypeScript.
- `vite.config.ts`: El archivo de configuración de Vite.

### Ejecutar el Servidor de Desarrollo

Para iniciar el servidor de desarrollo, usa:

```bash
npm run dev
# o
yarn dev
```

Esto iniciará el servidor de desarrollo y tu aplicación estará disponible en `http://localhost:3000`.

### Configuración Adicional

Puedes personalizar la configuración de Vite mediante el archivo `vite.config.ts`. Aquí hay un ejemplo básico de cómo se ve ese archivo:

```typescript
import { defineConfig } from 'vite';

export default defineConfig({
  // Configuración personalizada de Vite
});
```

---

## Linting y Formateo con ESLint y Prettier

**ESLint** es una herramienta de linting que te ayuda a encontrar y arreglar problemas en tu código TypeScript. **Prettier** es una herramienta de formateo de código que asegura un estilo consistente.

### Instalación de ESLint y Prettier

Instala ESLint y Prettier junto con las configuraciones necesarias para TypeScript:

```bash
npm install --save-dev eslint prettier eslint-plugin-prettier eslint-config-prettier @typescript-eslint/parser @typescript-eslint/eslint-plugin
# o
yarn add --dev eslint prettier eslint-plugin-prettier eslint-config-prettier @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

### Configuración de ESLint

Crea un archivo `.eslintrc.json` en la raíz del proyecto:

```json
{
  "parser": "@typescript-eslint/parser",
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended"
  ],
  "rules": {
    "prettier/prettier": "error"
  }
}
```

### Configuración de Prettier

Crea un archivo `.prettierrc` en la raíz del proyecto:

```json
{
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": true,
  "trailingComma": "all",
  "bracketSpacing": true,
  "arrowParens": "avoid"
}
```

### Scripts en `package.json`

Añade los siguientes scripts a tu archivo `package.json` para facilitar el uso de ESLint y Prettier:

```json
"scripts": {
  "dev": "vite",
  "build": "vite build",
  "lint": "eslint 'src/**/*.{ts,tsx}'",
  "format": "prettier --write 'src/**/*.{ts,tsx}'"
}
```

### Integración con VS Code

Para una mejor experiencia de desarrollo, instala las extensiones de ESLint y Prettier en VS Code y añade las siguientes configuraciones en tu archivo `settings.json`:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ]
}
```

---

## Conclusión

Configurando un entorno de desarrollo moderno con Vite, ESLint y Prettier, puedes asegurar que tu proyecto esté organizado, eficiente y siguiendo las mejores prácticas. Estas herramientas no solo ayudan a mantener tu código limpio y bien estructurado, sino que también mejoran tu productividad al proporcionar un flujo de trabajo más fluido y automatizado. Vite, en particular, ofrece tiempos de compilación rápidos y una configuración simple que facilita el desarrollo moderno de aplicaciones web.
Configurando un entorno de desarrollo moderno con Vite, ESLint y Prettier, puedes asegurar que tu proyecto esté organizado, eficiente y siguiendo las mejores prácticas. Estas herramientas no solo ayudan a mantener tu código limpio y bien estructurado, sino que también mejoran tu productividad al proporcionar un flujo de trabajo más fluido y automatizado. Vite, en particular, ofrece tiempos de compilación rápidos y una configuración simple que facilita el desarrollo moderno de aplicaciones web.