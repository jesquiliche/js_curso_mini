---
sidebar_position: 1

---
# Programación Orientada a Objetos
# Programación Orientada a Objetos

## Introducción
La Programación Orientada a Objetos (POO) es una manera de organizar y estructurar el código para que sea más fácil de entender, mantener y reutilizar. En este capítulo, exploraremos los conceptos básicos de la POO en JavaScript, incluyendo clases y prototipos, herencia y polimorfismo, y métodos estáticos y dinámicos.

## Clases y Prototipos

### Clases
Las clases en JavaScript son como plantillas para crear objetos. Piensa en una clase como un molde para hacer galletas: el molde define la forma de las galletas, pero cada galleta individual puede ser diferente.

#### Cómo Crear una Clase

```javascript
class Persona {
    // El constructor es una función especial que se llama cuando creas una nueva persona
    constructor(nombre, edad) {
        this.nombre = nombre; // Asigna el nombre pasado al constructor a la nueva persona
        this.edad = edad; // Asigna la edad pasada al constructor a la nueva persona
    }

    // Un método es una función que pertenece a una clase
    saludar() {
        console.log(`Hola, mi nombre es ${this.nombre} y tengo ${this.edad} años.`);
    }
}

// Crear una nueva persona llamada Juan de 30 años
const juan = new Persona("Juan", 30);
juan.saludar(); // Salida: "Hola, mi nombre es Juan y tengo 30 años."
```

**Explicación:**
- `class Persona { ... }`: Define una nueva clase llamada `Persona`.
- `constructor(nombre, edad) { ... }`: El constructor es una función especial que se ejecuta cuando se crea una nueva instancia de la clase.
- `this.nombre`: `this` se refiere a la nueva instancia de la clase que se está creando.
- `saludar() { ... }`: Define un método que pueden usar todas las instancias de `Persona`.

### Prototipos
Antes de que existieran las clases en JavaScript, se utilizaban prototipos para crear objetos y compartir métodos entre ellos.

#### Cómo Usar Prototipos

```javascript
// Crear una función constructora para la clase Persona
function Persona(nombre, edad) {
    this.nombre = nombre;
    this.edad = edad;
}

// Añadir un método al prototipo de Persona
Persona.prototype.saludar = function() {
    console.log(`Hola, mi nombre es ${this.nombre} y tengo ${this.edad} años.`);
};

// Crear una nueva persona llamada María de 25 años
const maria = new Persona("María", 25);
maria.saludar(); // Salida: "Hola, mi nombre es María y tengo 25 años."
```

**Explicación:**
- `function Persona(nombre, edad) { ... }`: Define una función constructora para crear objetos `Persona`.
- `Persona.prototype.saludar = function() { ... }`: Añade el método `saludar` al prototipo de `Persona`.

## Herencia y Polimorfismo

### Herencia
La herencia es cuando una clase toma prestadas propiedades y métodos de otra clase. Imagina que tienes una clase `Animal` y quieres crear una clase `Perro` que herede de `Animal`.

#### Cómo Usar Herencia

```javascript
class Animal {
    constructor(nombre) {
        this.nombre = nombre;
    }

    hacerSonido() {
        console.log(`${this.nombre} hace un sonido.`);
    }
}

class Perro extends Animal {
    constructor(nombre, raza) {
        super(nombre); // Llama al constructor de la clase base (Animal)
        this.raza = raza;
    }

    ladrar() {
        console.log(`${this.nombre}, el ${this.raza}, ladra.`);
    }
}

const miPerro = new Perro("Rex", "Labrador");
miPerro.hacerSonido(); // Salida: "Rex hace un sonido."
miPerro.ladrar(); // Salida: "Rex, el Labrador, ladra."
```

**Explicación:**
- `class Perro extends Animal { ... }`: `Perro` hereda de `Animal`, lo que significa que `Perro` tiene todas las propiedades y métodos de `Animal`.
- `super(nombre);`: Llama al constructor de la clase base (`Animal`) para inicializar la parte `Animal` del objeto `Perro`.

### Polimorfismo
El polimorfismo es cuando una clase puede ser tratada como una instancia de su clase base. Esto permite que diferentes clases respondan de manera diferente a la misma llamada de método.

#### Cómo Usar Polimorfismo

```javascript
class Gato extends Animal {
    hacerSonido() {
        console.log(`${this.nombre} maúlla.`);
    }
}

const miGato = new Gato("Mia");
miGato.hacerSonido(); // Salida: "Mia maúlla."

const animales = [miPerro, miGato];
animales.forEach(animal => animal.hacerSonido());

// Salida:
// "Rex hace un sonido."
// "Mia maúlla."
```

**Explicación:**
- `class Gato extends Animal { ... }`: `Gato` hereda de `Animal`.
- `hacerSonido() { ... }`: `Gato` tiene su propia implementación del método `hacerSonido`.

## Métodos Estáticos y Dinámicos

### Métodos Estáticos
Los métodos estáticos son funciones que pertenecen a la clase en sí misma, no a las instancias de la clase. Son útiles para operaciones que no dependen de una instancia específica de la clase.

#### Cómo Usar Métodos Estáticos

```javascript
class Calculadora {
    static sumar(a, b) {
        return a + b;
    }
}

console.log(Calculadora.sumar(5, 3)); // Salida: 8
```

**Explicación:**
- `static sumar(a, b) { ... }`: Define el método `sumar` como un método estático de `Calculadora`.

### Métodos Dinámicos
Los métodos dinámicos son funciones que pertenecen a las instancias de la clase. Son útiles para operaciones que deben realizarse en objetos específicos.

#### Cómo Usar Métodos Dinámicos

```javascript
class Contador {
    constructor() {
        this.cuenta = 0;
    }

    incrementar() {
        this.cuenta++;
        console.log(this.cuenta);
    }
}

const miContador = new Contador();
miContador.incrementar(); // Salida: 1
miContador.incrementar(); // Salida: 2
```

**Explicación:**
- `incrementar() { ... }`: Define un método dinámico que incrementa y muestra la cuenta de una instancia de `Contador`.

## Conclusión
La Programación Orientada a Objetos en JavaScript te permite organizar y estructurar tu código de una manera clara y reutilizable. Las clases y los prototipos facilitan la creación y gestión de objetos, mientras que la herencia y el polimorfismo permiten extender y personalizar el comportamiento de los objetos. Los métodos estáticos y dinámicos ofrecen diferentes formas de trabajar con las clases y sus instancias, proporcionando flexibilidad y modularidad en tu código. Con estos conceptos, podrás escribir programas más eficientes y fáciles de mantener.

---

Este capítulo ofrece una introducción accesible a la POO en JavaScript, con explicaciones simples y ejemplos prácticos para facilitar el aprendizaje de estos conceptos esenciales.