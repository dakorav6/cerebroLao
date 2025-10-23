- las variables son del tipo de dato que almacenen 
- declaración de variable 
	- `let nomvariable; `
	- `var nomvariable;`  => no se recomienda usar por problemas de hosting? 

- Mostrar datos por consola:
	- concatenación: ``console.log("Hola, " + nombre + "!");``
	- alternativa: Template Strings
		- `console.log('hola ${nomVariable} que hace')`
- Ingreso de datos: ` var nomVariable = prompt("Ingrese Dato")`
- Mostrar informacion en la ventanita emergente o pop-up: ``alert("Holiii")``
- Mostrar datos en una etiqueta HTML
	- necesitamos poner el script para enlazar el html con css y ponrle una id a una etiqeuta en html 
	- js:
```
const cualNom1 = document.getElementById('nomIdEtiquetaHTML')
cualNom1.textContent ='Aqui iria el texto que queremos mostrar'

```

- enlazar html con JS:   va al final del body
	`<script src = "nomScriptJS.js">  </script>;`
- ingreso valor por consola:  
	- `let nombre = prompt("Por favor, introduce tu nombre:");`

- Flujo de control especial en js (Operador Ternario):
	- ``(condicion>0) ?    si se cumple   :  si no se cumple; ``
- Arrays:  ``let numeros = [1,2,3,4,5,6]``


---
# Los bucles `for...in` y `for...of`

### **`for...in` en JavaScript**

El bucle `for...in` se usa para iterar sobre las propiedades de un objeto.
```
const persona = {
  nombre: "Juan",
  edad: 30,
  ocupacion: "Ingeniero"
};

for (let propiedad in persona) {
  console.log(propiedad + ": " + persona[propiedad]);
}

```


## `for...of` en JavaScript

El bucle `for...of` se utiliza para iterar sobre los valores de una colección iterable, como un array, un string, un `Map`, un `Set`, etc.

```
const numeros = [10, 20, 30, 40];

for (let numero of numeros) {
  console.log(numero);
}

```


----
# Funciones 


PENDIENTE INVESTIGAR  : Asincronía en Javascript: Callbacks, promesas y Async / Awai? 

**2 formas de escribir una función:**


**1 .- Vieja :**  ` function nomFuncion(){  //codigo   } `

**2.- Nueva (llamada función flecha):**  `const nomFuncion =()=> { //codigo     }`

- Si hay 1 sola línea de retorno, puedes quitar { } y return: 
	- ``const multiplicar = (a , b) => a*b; ``
-  Si hay 1 solo parámetro, puedes quitar los paréntesis.
	 -  ``const multiplicar = x => x * 2 ``       // ✅ válido (un solo parámetro)
- Si no hay parámetros, igual colocar los parentesis
	- ``const saludar = () => "hola" ;``
#nota el paso de parametros como se puede deducir no se requiere especificar el tipo de dato solo se pondria el nombre de la variable ejem:
```
function imprimir(frase){ document.write(frase) }

imprimir("Hola amigos")
```

## Función callback

Un **callback** es una función que se pasa como argumento a otra función y se ejecuta después de que esta termina.

```
function saludar(nombre, callback) {
  console.log("Hola, " + nombre);
  callback(); // se llama después
}

function despedida() {
  console.log("Adiós!");
}

saludar("Jordan", despedida);
```

----

## Promesa 

Una **promesa** es un objeto que representa un valor que puede estar disponible ahora, en el futuro o nunca. Esto se usa debido a que js es una programacion lineal y no multihilo, ósea que no avanza a la siguiente linea de codigo hasta que termine de ejecutar en la que esta. Con promesa podemos podemos seguir avanzando en la ejecucion del codigo mientras se resuelve la promesa. 

```
let promesa = new Promise((resolve, reject) => {
  // Aquí va el código que se ejecuta (puede tardar tiempo)
});
```

 🔍 **¿Qué son `resolve` y `reject`?**

Son **funciones** que vienen incluidas en la promesa. Tú decides cuándo llamarlas:
- `resolve(valor)` → Se llama cuando todo sale bien.
- `reject(error)` → Se llama cuando hay un problema o error.

```
let promesa = new Promise((resolve, reject) => {
  let exito = true;

  // Tú decides si todo salió bien o no
  if (exito) {
    resolve("¡Sí funcionó!"); // Esto activa el .then()
  } else {
    reject("¡Falló!"); // Esto activa el .catch()
  }
});

promesa
  .then((mensaje) => {
    console.log("✔️ Éxito:", mensaje);
  })
  .catch((error) => {
    console.log("❌ Error:", error);
  });
```

**El `.then()` y `.catch()` no deciden eso por sí mismos**, ellos simplemente **esperan** que tú les digas si fue un éxito o un error. Esa decisión ocurre _dentro_ de la promesa.


----

## sincrono y asincrono

javascript es mono hilo por asi decirlo osea que tiene solo una linea de ejecucion 

### **Sincrono**
es cuando el código se **ejecuta línea por línea**, en orden, y **espera a que cada línea termine antes de seguir con la siguiente**.

### **Asincrono**
El código puede **iniciar una tarea que tarda (como esperar tiempo o pedir datos de un servidor)** y **seguir con otras cosas sin esperar que termine**.

ejemplo:
```
console.log("1. Empieza");

setTimeout(() => {
  console.log("2. Después de 2 segundos");
}, 2000);

console.log("3. Termina");

```

consola quedaria asi:

```
1. Empieza
2. Termina
3. Después de 2 segundos
```

¿Por qué? Porque `setTimeout` es **asíncrono**: se pone en cola y se ejecuta más tarde, **sin bloquear** el flujo principal.

