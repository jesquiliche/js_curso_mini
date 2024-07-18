---
sidebar_position: 2

---

# Capítulo 14: Programación Funcional

La programación funcional es un paradigma de programación que trata las computaciones como evaluaciones de funciones matemáticas y evita el cambio de estado y la mutación de datos. En JavaScript, este enfoque se basa en el uso de funciones de orden superior, la inmutabilidad de datos y el uso de funciones puras, así como en el uso de métodos como `map`, `filter` y `reduce` para manipular colecciones de datos de manera eficiente.

## Funciones de Orden Superior

Las funciones de orden superior son aquellas que pueden recibir funciones como argumentos o devolver otras funciones como resultado. En JavaScript, esto se puede lograr gracias al hecho de que las funciones son tratadas como ciudadanos de primera clase, lo que permite una gran flexibilidad en el manejo y composición de funciones.

### Ejemplo de Función de Orden Superior

```javascript
// Función de orden superior que recibe otra función como argumento
function operacionMatematica(numero, operacion) {
    return operacion(numero);
}

// Funciones que se pueden pasar como argumento
function cuadrado(x) {
    return x * x;
}

function cubo(x) {
    return x * x * x;
}

console.log(operacionMatematica(3, cuadrado)); // Devuelve 9 (3 al cuadrado)
console.log(operacionMatematica(3, cubo)); // Devuelve 27 (3 al cubo)
```

## Inmutabilidad y Pureza de Funciones

### Inmutabilidad

La inmutabilidad se refiere a la incapacidad de cambiar un objeto una vez que ha sido creado. En JavaScript, los objetos primitivos como cadenas y números son inmutables, pero los objetos complejos como arrays y objetos pueden ser mutables. La inmutabilidad se promueve creando nuevos objetos en lugar de modificar los existentes, lo cual facilita la gestión de estados y reduce los errores inesperados.

### Pureza de Funciones

Una función pura es aquella que, dada la misma entrada, siempre produce el mismo resultado y no tiene efectos secundarios observables fuera de la función. Esto facilita el razonamiento sobre el código y reduce los errores, ya que no depende de variables globales o estados cambiantes.

### Ejemplo de Función Pura

```javascript
// Función impura (depende de una variable externa mutable)
let contador = 0;
function sumar(num) {
    contador += num;
    return contador;
}

console.log(sumar(5)); // Devuelve 5
console.log(sumar(3)); // Devuelve 8

// Función pura (no depende de variables externas y no tiene efectos secundarios)
function sumarPuro(a, b) {
    return a + b;
}

console.log(sumarPuro(5, 3)); // Devuelve 8
console.log(sumarPuro(5, 3)); // Devuelve 8 (siempre el mismo resultado)
```

## Métodos `map`, `filter` y `reduce`

Estos métodos son fundamentales en programación funcional para transformar y reducir colecciones de datos de manera declarativa.

### `map`

El método `map` crea un nuevo array con los resultados de aplicar una función a cada elemento del array original.

```javascript
const numeros = [1, 2, 3, 4, 5];

const cuadrados = numeros.map(x => x * x);

console.log(cuadrados); // Devuelve [1, 4, 9, 16, 25]
```

### `filter`

El método `filter` crea un nuevo array con todos los elementos que pasan una prueba implementada por la función proporcionada.

```javascript
const numeros = [1, 2, 3, 4, 5];

const pares = numeros.filter(x => x % 2 === 0);

console.log(pares); // Devuelve [2, 4]
```

### `reduce`

El método `reduce` aplica una función a un acumulador y a cada elemento de un array (de izquierda a derecha) para reducirlo a un único valor.

```javascript
const numeros = [1, 2, 3, 4, 5];

const suma = numeros.reduce((acumulador, valorActual) => acumulador + valorActual, 0);

console.log(suma); // Devuelve 15 (suma de todos los elementos del array)
```

## Conclusión

La programación funcional en JavaScript ofrece herramientas poderosas como funciones de orden superior, inmutabilidad y funciones puras, junto con métodos como `map`, `filter` y `reduce`, que permiten escribir código más claro, conciso y mantenible. Adoptar estos principios puede mejorar la calidad y la eficiencia de tu código, facilitando el manejo de datos y la gestión de estados en aplicaciones complejas.
