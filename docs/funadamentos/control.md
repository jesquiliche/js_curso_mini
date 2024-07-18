---
sidebar_position: 4
---
# Estructuras de Control

## Introducción
Las estructuras de control son fundamentales en la programación, ya que permiten dirigir el flujo de ejecución del código basándose en condiciones y repeticiones. En JavaScript, existen varias estructuras de control que te permitirán manejar el flujo de tu programa de manera efectiva. Este capítulo cubrirá las estructuras de control condicionales y las estructuras de control de bucle.

## Estructuras de Control Condicionales

Las estructuras condicionales te permiten ejecutar diferentes bloques de código basados en ciertas condiciones. Las principales estructuras condicionales en JavaScript son `if`, `else if`, `else` y `switch`.

## `if`, `else if` y `else`
La estructura `if` se usa para ejecutar un bloque de código si una condición especificada es verdadera. Puedes usar `else if` para especificar nuevas condiciones si la primera no se cumple, y `else` para ejecutar un bloque de código si ninguna de las condiciones previas es verdadera.

**Sintaxis:**

```javascript
if (condición) {
    // Código a ejecutar si la condición es verdadera
} else if (otraCondición) {
    // Código a ejecutar si la otra condición es verdadera
} else {
    // Código a ejecutar si ninguna de las condiciones anteriores es verdadera
}
```

**Ejemplo:**

```javascript
let edad = 18;

if (edad < 13) {
    console.log("Eres un niño.");
} else if (edad >= 13 && edad < 20) {
    console.log("Eres un adolescente.");
} else {
    console.log("Eres un adulto.");
}
```

## `switch`
La estructura `switch` se usa para ejecutar uno de varios bloques de código basados en el valor de una expresión. Es una alternativa a múltiples `if...else if...else`.

**Sintaxis:**

```javascript
switch (expresión) {
    case valor1:
        // Código a ejecutar si la expresión es igual a valor1
        break;
    case valor2:
        // Código a ejecutar si la expresión es igual a valor2
        break;
    // Puedes tener tantos casos como necesites
    default:
        // Código a ejecutar si la expresión no coincide con ningún caso
}
```

**Ejemplo:**

```javascript
let dia = 3;

switch (dia) {
    case 1:
        console.log("Lunes");
        break;
    case 2:
        console.log("Martes");
        break;
    case 3:
        console.log("Miércoles");
        break;
    default:
        console.log("Día no válido");
}
```

## Estructuras de Control de Bucle

Las estructuras de bucle permiten repetir un bloque de código varias veces. Las principales estructuras de bucle en JavaScript son `for`, `while` y `do...while`.

## `for`
El bucle `for` se usa para repetir un bloque de código un número específico de veces. Es ideal cuando conoces de antemano cuántas veces necesitas iterar.

**Sintaxis:**

```javascript
for (inicialización; condición; incremento) {
    // Código a ejecutar en cada iteración
}
```

**Ejemplo:**

```javascript
for (let i = 0; i < 5; i++) {
    console.log("Iteración número " + i);
}
```

## `while`
El bucle `while` repite un bloque de código mientras una condición especificada sea verdadera. Es útil cuando no conoces de antemano cuántas veces necesitas iterar.

**Sintaxis:**

```javascript
while (condición) {
    // Código a ejecutar mientras la condición sea verdadera
}
```

**Ejemplo:**

```javascript
let i = 0;

while (i < 5) {
    console.log("Iteración número " + i);
    i++;
}
```

##### `do...while`
El bucle `do...while` es similar a `while`, pero garantiza que el bloque de código se ejecute al menos una vez, ya que la condición se evalúa después de cada iteración.

**Sintaxis:**

```javascript
do {
    // Código a ejecutar
} while (condición);
```

**Ejemplo:**

```javascript
let i = 0;

do {
    console.log("Iteración número " + i);
    i++;
} while (i < 5);
```

## Bucles y Control de Flujo Adicional

## `break`
La instrucción `break` se usa para salir de un bucle o una estructura `switch` antes de que terminen normalmente.

**Ejemplo:**

```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        break; // Salir del bucle cuando i es igual a 5
    }
    console.log(i);
}
```

### `continue`
La instrucción `continue` se usa para saltar a la siguiente iteración de un bucle y omitir el código restante en la iteración actual.

**Ejemplo:**

```javascript
for (let i = 0; i < 10; i++) {
    if (i % 2 === 0) {
        continue; // Saltar la iteración cuando i es un número par
    }
    console.log(i);
}
```

## Ejemplos Prácticos y Buenas Prácticas

### Ejemplo Práctico: Iterar sobre Arrays

```javascript
let frutas = ["manzana", "banana", "cereza"];

for (let i = 0; i < frutas.length; i++) {
    console.log(frutas[i]);
}

// Usando for...of
for (let fruta of frutas) {
    console.log(fruta);
}
```

### Ejemplo Práctico: Usar Condicionales y Bucles Juntos

```javascript
let numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

for (let numero of numeros) {
    if (numero % 2 === 0) {
        console.log(numero + " es par");
    } else {
        console.log(numero + " es impar");
    }
}
```

## Conclusión
Las estructuras de control son herramientas poderosas que te permiten manejar el flujo de ejecución de tu programa de manera eficiente. Entender cómo y cuándo usarlas es fundamental para escribir código claro, eficiente y mantenible. Practica con diferentes escenarios y combina estas estructuras para resolver problemas complejos de manera efectiva.
