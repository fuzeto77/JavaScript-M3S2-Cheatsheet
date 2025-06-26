# 📚 **Cheatsheet JavaScript - M3 S2**

## 📋 **Tabla de Contenidos**

1. [🎯 Temas Principales Utilizados](#-temas-principales-utilizados)
2. [📖 1: Estructuras de Datos](#-1-estructuras-de-datos-de-javascript---objetos)
   - [Métodos en JavaScript](#-métodos-en-javascript)
   - [Tipos de Datos Primitivos](#-tipos-de-datos-primitivos)
   - [Arrays](#-arrays)
   - [Objetos](#-objetos)
   - [Sets](#-sets)
   - [Maps](#-maps)
   - [Visualización de Datos](#-visualización-avanzada-de-datos)
3. [📖 2: Hoisting, Closures, Callbacks](#-2-hoisting-closures-callbacks-scope-y-this)
   - [Hoisting](#-hoisting)
   - [Scope](#-scope-en-javascript)
   - [Closures](#-closures)
   - [Bucle de Eventos](#-bucle-de-eventos)
   - [Callbacks](#-callbacks)
   - [This](#-this-en-javascript)
4. [📖 3: Promesas, Async/Await](#-3-promesas-asyncawait-prototipos-clases-y-modularidad)
   - [Promesas](#-promesas)
   - [Async/Await](#-asyncawait)
   - [Prototipos](#-prototipos)
   - [Clases ES6](#-clases-es6)
   - [Modularidad](#-modularidad-en-javascript)
5. [📋 TRAINING S2](#-training-s2-requisitos-para-entregar)
   - [Requisitos Técnicos](#-requisitos-técnicos-obligatorios)
   - [Criterios de Evaluación](#-criterios-de-evaluación-100-puntos-totales)
   - [Timeline](#-timeline-sugerido-4-horas)
6. [💡 Tips y Mejores Prácticas](#-tips-y-mejores-prácticas)

---

## 🎯 **Temas Principales Utilizados**

### 1. **Gestión de Datos Avanzada (CRUD)**
- **Estructuras de datos complejas**: Objects, Sets, Maps
- **Campos estándar**: id, nombre, contenido, categoría, fecha, is_active
- **Operaciones**: Crear, Leer, Actualizar, Eliminar

### 2. **Manejo de Estados y Soft Delete**
- **Campo `is_active`**: Control de visibilidad de elementos
- **Eliminación lógica**: Elementos marcados como inactivos sin eliminar físicamente
- **Estados de datos**: Activo, Inactivo, Archivado

### 3. **Manipulación del DOM**
- **Formularios HTML**: Captura de datos del usuario
- **Renderizado dinámico**: Actualización automática de la interfaz
- **Event handling**: onclick, onsubmit, addEventListener
- **Selección de elementos**: `document.getElementById()`, `createElement()`

### 4. **Manejo de APIs REST**
- **Métodos HTTP**: GET, POST, PATCH, DELETE
- **JSON Server**: Simulación de backend
- **Fetch API**: Peticiones asíncronas
- **Manejo de respuestas**: JSON parsing y error handling

### 5. **Modularidad y Arquitectura**
- **Separación de responsabilidades**: UI, API, lógica de negocio
- **Módulos ES6**: Import/Export
- **Patrones de diseño**: Factory, Observer, Singleton

---

## 📖 **1: Estructuras de Datos de JavaScript - Objetos**

### **🔸 Uso del Punto y Coma (;)**
```javascript
// Buena práctica: usar ; al final de cada declaración
const nombre = "JavaScript";
let edad = 30;
const activo = true;
```

### **🔸 Métodos en JavaScript**

#### **📋 Definición**
Un método es una **función que pertenece a un objeto**. Nos permite realizar acciones sobre los datos de ese objeto o manipular sus propiedades.

```javascript
// Ejemplo básico de objeto con métodos
const car = {
    make: "Tesla",
    model: "Model 3",
    year: 2020,
    
    // Método para describir el auto
    getDescription: function() {
        return `This car is a ${this.year} ${this.make} ${this.model}.`;
    },
    
    // Método para actualizar el modelo
    updateModel: function(newModel) {
        this.model = newModel;
        return `The model has been updated to ${this.model}.`;
    }
};

// Uso de los métodos
console.log(car.getDescription()); // "This car is a 2020 Tesla Model 3."
console.log(car.updateModel("Model S")); // "The model has been updated to Model S."
```

#### **📊 Métodos de Object (Built-in)**
```javascript
// Métodos nativos de Object
const obj = { nombre: "Juan", edad: 25 };
Object.keys(obj);        // ["nombre", "edad"]
Object.values(obj);      // ["Juan", 25]
Object.entries(obj);     // [["nombre", "Juan"], ["edad", 25]]
Object.assign(obj, { activo: true }); // Combinar objetos
```

#### **🔢 Métodos de Number**
```javascript
const numero = 3.14159;
numero.toFixed(2);       // "3.14" - redondear decimales
parseInt("42");          // 42 - convertir string a entero
parseFloat("3.14");      // 3.14 - convertir string a decimal
Number.isNaN(NaN);       // true - verificar si es NaN
```

#### **📝 Métodos de String**
```javascript
const texto = "JavaScript";
texto.toUpperCase();     // "JAVASCRIPT" - convertir a mayúsculas
texto.toLowerCase();     // "javascript" - convertir a minúsculas
texto.includes("Script"); // true - verificar si contiene dicho texto
texto.split("");        // ["J","a","v","a","S","c","r","i","p","t"] - dividir en array
```

#### **📋 Métodos de Array**
```javascript
const array = [1, 2, 3, 4, 5];
array.push(6);           // [1,2,3,4,5,6] - agregar al final
array.pop();             // 6 - eliminar del final
array.includes(3);       // true - verificar si contiene dicho elemento
array.indexOf(4);        // 3 - encontrar posición del elemento
```

### **🔸 Tipos de Datos Primitivos**
```javascript
// Tipos primitivos
let texto = "Hola";          // string
let numero = 42;             // number
let booleano = true;         // boolean
let indefinido = undefined;  // undefined
let nulo = null;            // null
let simbolo = Symbol("id");  // symbol
let grande = 123n;          // bigint
```

### **🔸 Identificación con typeof**
```javascript
typeof "texto";      // "string"
typeof 123;          // "number" 
typeof true;         // "boolean"
typeof undefined;    // "undefined"
typeof null;         // "object" (peculiaridad de JS)
typeof {};           // "object"
typeof [];           // "object"
typeof function(){}; // "function"
```

### **🔸 Arrays**
```javascript
// Creación y manipulación
const frutas = ["manzana", "banana", "naranja"];
frutas.push("uva");          // Agregar al final
frutas.pop();                // Eliminar del final
frutas.unshift("kiwi");      // Agregar al inicio
frutas.shift();              // Eliminar del inicio

// Métodos de iteración
frutas.forEach(fruta => console.log(fruta));
frutas.map(fruta => fruta.toUpperCase());
frutas.filter(fruta => fruta.length > 5);
```

### **🔸 Objetos**
```javascript
// Creación de objetos
const persona = {
    nombre: "Ana",
    edad: 28,
    activo: true,
    saludar: function() {
        return `Hola, soy ${this.nombre}`;
    }
};

// Acceso a propiedades
persona.nombre;           // Notación punto
persona["edad"];          // Notación corchetes
persona.saludar();        // Llamar método
```

### **🔸 Sets**
```javascript
// Creación y uso de Sets
const numeros = new Set([1, 2, 3, 2, 1]); // {1, 2, 3} - elimina duplicados
numeros.add(4);           // Agregar elemento
numeros.has(2);           // true - verificar existencia
numeros.delete(1);        // Eliminar elemento
numeros.size;             // Tamaño del set

// Iteración
for (let numero of numeros) {
    console.log(numero);
}
```

### **🔸 Maps**
```javascript
// Creación y uso de Maps
const mapa = new Map();
mapa.set("nombre", "Carlos");
mapa.set("edad", 30);
mapa.set(1, "primer elemento");

mapa.get("nombre");       // "Carlos"
mapa.has("edad");         // true
mapa.delete(1);           // Eliminar entrada
mapa.size;                // Tamaño del map

// Iteración
mapa.forEach((valor, clave) => {
    console.log(`${clave}: ${valor}`);
});
```

### **🔸 Iteraciones Especiales**
```javascript
// for...in (objetos)
const obj = { a: 1, b: 2, c: 3 };
for (let clave in obj) {
    console.log(`${clave}: ${obj[clave]}`);
}

// for...of (iterables)
const arr = [1, 2, 3];
for (let valor of arr) {
    console.log(valor);
}

// forEach para Arrays
arr.forEach((valor, indice) => {
    console.log(`${indice}: ${valor}`);
});
```

### **🔸 Visualización avanzada de datos**
```javascript
// console.table() - Mostrar datos en formato tabla
const usuarios = [
    { id: 1, nombre: "Ana", edad: 25 },
    { id: 2, nombre: "Luis", edad: 30 },
    { id: 3, nombre: "María", edad: 28 }
];

console.table(usuarios); // Muestra tabla organizada en consola

// También funciona con objetos
const producto = { id: 1, nombre: "Laptop", precio: 800 };
console.table(producto);

// Para Sets y Maps
const numeros = new Set([1, 2, 3]);
console.table(Array.from(numeros)); // Convertir Set a Array primero

const mapa = new Map([["clave1", "valor1"], ["clave2", "valor2"]]);
console.table(Object.fromEntries(mapa)); // Convertir Map a Object
```

---

## 📖 **2: Hoisting, Closures, Callbacks, Scope y This**

### **🔸 Hoisting**
```javascript
// Variables var son "elevadas"
console.log(x); // undefined (no error)
var x = 5;

// let y const no son accesibles antes de declaración
console.log(y); // ReferenceError
let y = 10;

// Funciones declaradas son completamente elevadas
saludar(); // "¡Hola!" - funciona
function saludar() {
    console.log("¡Hola!");
}
```

### **🔸 Scope en JavaScript**
```javascript
// Scope global
var global = "Soy global";

function miFuncion() {
    // Scope de función
    var local = "Soy local";
    
    if (true) {
        // Scope de bloque (let/const)
        let bloque = "Soy de bloque";
        const constante = "También de bloque";
    }
    
    console.log(global); // Accesible
    console.log(local);  // Accesible
    // console.log(bloque); // Error
}
```

### **🔸 Closures**
```javascript
// Función que retorna otra función
function crearContador() {
    let count = 0;
    
    return function() {
        count++;
        return count;
    };
}

const contador = crearContador();
console.log(contador()); // 1
console.log(contador()); // 2
// count sigue siendo accesible (closure)
```

### **🔸 Bucle de Eventos**
## **📺 Video explicativo:** [¿Qué 😵 es el event loop? - YouTube](https://www.youtube.com/watch?v=eiC58R16hb8)

```javascript
// Pila de ejecución y cola de callbacks
console.log("1");

setTimeout(() => {
    console.log("2");
}, 0);

console.log("3");
// Salida: 1, 3, 2
```

### **🔸 Callbacks**
```javascript
// Función que recibe otra función como parámetro
function procesar(datos, callback) {
    const resultado = datos.map(x => x * 2);
    callback(resultado);
}

procesar([1, 2, 3], function(resultado) {
    console.log(resultado); // [2, 4, 6]
});

// Callback con arrow function
procesar([1, 2, 3], resultado => console.log(resultado));
```

### **🔸 this en JavaScript**
```javascript
// En objeto
const persona = {
    nombre: "María",
    saludar: function() {
        console.log(`Hola, soy ${this.nombre}`);
    }
};

// En función regular
function mostrarThis() {
    console.log(this); // Window en navegador, global en Node
}

// Arrow functions heredan this del contexto
const obj = {
    nombre: "Pedro",
    saludar: () => {
        console.log(this.nombre); // undefined
    },
    saludarNormal: function() {
        const arrow = () => {
            console.log(this.nombre); // "Pedro"
        };
        arrow();
    }
};
```

---

## 📖 **3: Promesas, Async/Await, Prototipos, Clases y Modularidad**

### **🔸 Promesas**

#### **📋 Definición**
Las promesas son una forma moderna de manejar tareas asíncronas en JavaScript. Una promesa representa un valor que puede estar disponible ahora, en el futuro o nunca. Una promesa tiene tres estados posibles:

- **Pendiente (Pending)**: cuando la operación asíncrona aún no ha terminado.
- **Resuelta (Fulfilled)**: cuando la operación se completa exitosamente.
- **Rechazada (Rejected)**: cuando ocurre un error durante la operación.

```javascript
// Creación de promesa
const miPromesa = new Promise((resolve, reject) => {
    const exito = true;
    
    if (exito) {
        resolve("Operación exitosa");
    } else {
        reject("Error en la operación");
    }
});

// Uso de promesa
miPromesa
    .then(resultado => console.log(resultado))
    .catch(error => console.error(error))
    .finally(() => console.log("Promesa completada"));
```

### **🔸 Async/Await**
```javascript
// Función asíncrona
async function obtenerDatos() {
    try {
        const response = await fetch('https://api.ejemplo.com/datos');
        const datos = await response.json();
        return datos;
    } catch (error) {
        console.error('Error:', error);
        throw error;
    }
}

// ✅ Uso moderno con async/await
async function usarDatos() {
    try {
        const datos = await obtenerDatos();
        console.log(datos);
    } catch (error) {
        console.error('Error al obtener datos:', error);
    }
}
```

### **🔸 Prototipos**
```javascript
// Función constructora
function Persona(nombre, edad) {
    this.nombre = nombre;
    this.edad = edad;
}

// Agregar método al prototipo
Persona.prototype.saludar = function() {
    return `Hola, soy ${this.nombre}`;
};

// Uso
const juan = new Persona("Juan", 25);
console.log(juan.saludar()); // "Hola, soy Juan"

// Herencia de prototipos
function Estudiante(nombre, edad, carrera) {
    Persona.call(this, nombre, edad);  // Llama al constructor padre
    this.carrera = carrera;
}

Estudiante.prototype = Object.create(Persona.prototype);  // Hereda métodos
Estudiante.prototype.constructor = Estudiante;            // Restaura constructor

// Agregar método específico
Estudiante.prototype.estudiar = function() {
    return `${this.nombre} está estudiando ${this.carrera}`;
};

// Uso de la herencia
const ana = new Estudiante("Ana", 20, "Ingeniería");
console.log(ana.saludar());  // "Hola, soy Ana" (heredado)
console.log(ana.estudiar()); // "Ana está estudiando Ingeniería"
```

### **🔸 Clases (ES6)**
```javascript
// Definición de clase
class Vehiculo {
    constructor(marca, modelo) {
        this.marca = marca;
        this.modelo = modelo;
    }
    
    // Método
    arrancar() {
        return `${this.marca} ${this.modelo} está arrancando`;
    }
    
    // Método estático
    static tipoVehiculo() {
        return "Vehículo terrestre";
    }
}

// Herencia
class Auto extends Vehiculo {
    constructor(marca, modelo, puertas) {
        super(marca, modelo);
        this.puertas = puertas;
    }
    
    // Sobrescribir método
    arrancar() {
        return super.arrancar() + " con " + this.puertas + " puertas";
    }
}

// Uso
const miAuto = new Auto("Toyota", "Corolla", 4);
console.log(miAuto.arrancar());
```

### **🔸 Modularidad en JavaScript**
```javascript
// math.js - Exportación named
export function sumar(a, b) {
    return a + b;
}

export const PI = 3.14159;

export default function multiplicar(a, b) {
    return a * b;
}

// main.js - Importación
import multiplicar, { sumar, PI } from './math.js';
import * as matematicas from './math.js';

console.log(sumar(2, 3));      // 5
console.log(multiplicar(4, 5)); // 20
console.log(PI);               // 3.14159

// Importación dinámica
async function cargarModulo() {
    const modulo = await import('./math.js');
    console.log(modulo.sumar(1, 2));
}
```

#### **🔄 Importación Dinámica**
La importación dinámica permite cargar módulos de forma asíncrona solo cuando sean necesarios, lo que mejora el rendimiento en aplicaciones grandes.

```javascript
// Importación dinámica con async/await
import('./app.js')
    .then((module) => {
        module.greet("Riwi");
    })
    .catch((error) => {
        console.error('Error loading the module: ', error);
    });

// Con async/await (más moderno)
async function cargarModuloDinamico() {
    try {
        const modulo = await import('./app.js');
        modulo.greet("Riwi");
    } catch (error) {
        console.error('Error loading the module: ', error);
    }
}
```

---

## 📋 **TRAINING S2: Requisitos para Entregar**

### **🎯 Problema a Resolver**
**Gestión de Datos con Objetos, Sets y Maps en JavaScript**

### **📝 Objetivos del Entrenamiento**
1. **Consolidar estructuras de datos avanzadas**: Objects, Sets, Maps
2. **Implementar bucles eficientes**: `for...in`, `for...of`, `forEach()`
3. **Aplicar validaciones y pruebas** de integridad de datos

---

### **📝 Requisitos Técnicos Obligatorios**

#### **1. Estructura del Proyecto**
```javascript
// Archivo: gestion_datos.js
// Duración estimada: 4 horas
```

#### **2. Implementación de Estructuras de Datos**

**a) Objeto productos** (3 productos mínimo):
```javascript
const productos = {
    producto1: {
        id: 1,
        nombre: "Producto A",
        precio: 100
    },
    producto2: {
        id: 2,
        nombre: "Producto B",
        precio: 200
    },
    producto3: {
        id: 3,
        nombre: "Producto C",
        precio: 300
    }
};
```

**b) Conversión a Set** (eliminar duplicados):
```javascript
const productosSet = new Set(Object.values(productos));
```

**c) Map para información adicional**:
```javascript
const categorias = new Map();
categorias.set("Electrónicos", "Producto A");
categorias.set("Hogar", "Producto B");
categorias.set("Deportes", "Producto C");
```

#### **3. Métodos de Recorrido Obligatorios**

**a) `for...in` para objetos**:
```javascript
for (let clave in productos) {
    console.log(`${clave}: ${productos[clave]}`);
}
```

**b) `for...of` para Sets**:
```javascript
for (let producto of productosSet) {
    console.log(producto);
}
```

**c) `forEach()` para Maps**:
```javascript
categorias.forEach((valor, clave) => {
    console.log(`${clave}: ${valor}`);
});
```

#### **4. Métodos de Objeto Requeridos**
- `Object.keys()`
- `Object.values()`
- `Object.entries()`

---

### **🏆 Criterios de Evaluación (100 puntos totales)**

#### **Requerimientos Técnicos (20 puntos)**
- ✅ Archivo `gestion_datos.js` creado
- ✅ Uso correcto de `let`/`const`
- ✅ Punto y coma al final de cada línea
- ✅ Comentarios explicativos en cada sección
- ✅ Implementación correcta de Object, Set, Map

#### **Alcance de Objetivos (20 puntos)**
- ✅ 3 productos con propiedades: id, nombre, precio
- ✅ Conversión exitosa a Set para eliminar duplicados
- ✅ Map con categorías implementado correctamente
- ✅ Bucles `for...in`, `for...of`, `forEach()` funcionando

#### **Entregables Funcionales (20 puntos)**
- ✅ Lista completa de productos (Object)
- ✅ Lista de productos únicos (Set)
- ✅ Categorías y nombres (Map)
- ✅ Validación de datos completos e íntegros

#### **Entrega Puntual (20 puntos)**
- ✅ Archivo `.zip` o enlace GitHub público
- ✅ Subido a Moodle antes del plazo establecido
- ✅ Formato correcto de entrega

#### **Uso de Recursos (20 puntos)**
- ✅ VS Code como editor de código
- ✅ Consola del navegador para pruebas (F12)
- ✅ Documentación clara y profesional del código

---

### **📊 Resultado Esperado**

**La salida en consola debe mostrar**:

1. **Productos del objeto**: Listado completo usando `for...in`
2. **Productos únicos del Set**: Recorrido con `for...of`
3. **Categorías del Map**: Visualización con `forEach()`
4. **Validaciones**: Confirmación de que los datos están íntegros

---

### **🔄 Pasos del Desarrollo**

#### **Paso 1**: Configuración del proyecto
- Crear archivo `gestion_datos.js`
- Configurar VS Code como entorno de desarrollo

#### **Paso 2**: Creación de objeto productos
- Definir 3 productos con id, nombre, precio

#### **Paso 3**: Conversión a Set
- Eliminar duplicados usando Set

#### **Paso 4**: Creación de Map
- Asociar categorías con productos

#### **Paso 5**: Recorrido de datos
- Implementar `for...in`, `for...of`, `forEach()`

#### **Paso 6**: Validaciones y pruebas
- Verificar integridad de datos
- Mostrar resultados en consola

#### **Paso 7**: Entrega del proyecto
- Formato `.zip` o enlace GitHub
- Subir a Moodle

---

## ⏰ **Timeline Sugerido (4 horas)**

### **Hora 1: Setup y Core**
- Estructura de archivos (15 min)
- Implementación Objects, Sets, Maps (45 min)

### **Hora 2: Bucles y Métodos**
- for...in, for...of, forEach (30 min)
- Object.keys(), values(), entries() (30 min)

### **Hora 3: Funcionalidad**
- Validaciones (30 min)
- Pruebas y debugging (30 min)

### **Hora 4: Pulimiento**
- Documentación (20 min)
- Testing final (20 min)
- Preparación entrega (20 min)

---

**🎯 Recuerda: Enfócate en cumplir exactamente los requisitos antes de agregar funcionalidades extra.**

---

## 💡 **Tips y Mejores Prácticas**

### **🔸 Declaración de Variables**
```javascript
// Usar const por defecto
const datos = [];

// Usar let cuando necesites reasignar
let contador = 0;

// Evitar var en código moderno
// var x = 10; // ❌ Evitar
```

### **🔸 Funciones Arrow vs Regulares**
```javascript
// Arrow function para callbacks simples
const numeros = [1, 2, 3];
const duplicados = numeros.map(n => n * 2);

// Función regular cuando necesites 'this'
const obj = {
    nombre: "Test",
    saludar: function() {
        console.log(this.nombre); // ✅ Funciona
    }
};
```

### **🔸 Destructuring**
```javascript
// Destructuring de objetos
const persona = { nombre: "Ana", edad: 25 };
const { nombre, edad } = persona;

// Destructuring de arrays
const colores = ["rojo", "verde", "azul"];
const [primero, segundo] = colores;
```

### **🔸 Template Literals**
```javascript
const nombre = "Carlos";
const edad = 30;

// Usar template literals para strings
const mensaje = `Hola, soy ${nombre} y tengo ${edad} años`;
```

### **🔸 Manejo de Errores**
```javascript
// Try-catch para operaciones que pueden fallar
try {
    const datos = JSON.parse(jsonString);
    console.log(datos);
} catch (error) {
    console.error("Error al parsear JSON:", error);
}
```

---

**Antonio Santiago © 2025** - Developed with ❤️ and a couple of coffees ☕
