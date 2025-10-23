?
- es un entorno de ejecución de js que permite ejecutar js fuera del navegador (en este caso seria el servidor )
- es asincrono y es orientada a eventos 
- en consola podemos escribir simplemente node y comensar a escribir codigo en js 
- dentro de visual estudio en la consola y con la url correspondiente al archivo js que queramos ejecutar fuera del navegador ponemos: `node index.js`
- globalThis es una variable global en toda nuestra aplicación 


# Patrón de diseño de modulo

Es un patrón que permite **encapsular código** en bloques reutilizables, **evitando contaminar el ámbito global** y ayudando a **organizar** tu aplicación.
En Node.js esto se hace mediante archivos y la forma en que exportas/importas contenido entre ellos, es como cuando haciamos las funciones y para reutilizarlas teniamos que importar de otros archivos.
Un módulo puede contener **tantas funciones, clases, objetos o variables como necesites**, y tú decides **qué exportas**.
Existen 2 metodos para usar el atron de modulo en NodeJS

* **Encapsulación** cada archivo con modulo activo las variables definicas ahi nadie fuera lo ve
- **exportacion controlada** tu eliges que mostrar al exterior con **export** y dejar como privado sin exportar
- **una buena practica** es crear cada modulo por tematica que agrupo las funciones segun la misma. 

## 1. CommonJS ((con `require` y `module.exports`)

es el sistema de módulos por defecto hasta antes de ES Modules pero sigue siendo usado aun hoy. (forma vieja)

operaciones.js
```
// Encapsulamos funciones
function sumar(a, b) {
  return a + b;
}

function restar(a, b) {
  return a - b;
}

// Exportamos lo que queremos que esté disponible fuera
module.exports = {
  sumar,
  restar,
};
```

app.js
```
const math = require('./math');

console.log(math.sumar(5, 3));  // 8
console.log(math.restar(10, 4)); // 6
```

## 2. ES Modules (con `import` y `export`)
a partir de node.js v12 podemos usar los modulos nativos de JavaScript (forma moderna)

❗ Requiere que tu `package.json` tenga: ` "type": "module"`
o  que el archivo sea `.mjs` (la opcion mas practica a mi parecer)

**¿que es eso de archivo .mjs?**
en Node.js significa **"modulo JavaScript"** y se usa para indicar explicitamente que ese archivo esta escrito usando **ES Modules** (el sistema moderno con `import`/`export`), en lugar de CommonJS (`require`/`module.exports`).
**nota:** tanto para exportar como el que importa deben de tener la extensión .mjs

**operaciones.mjs**
```
export function sumar(a, b) {
  return a + b;
}

export function restar(a, b) {
  return a - b;
}
```

**app.mjs**
```
import { sumar, restar } from './math.mjs';

console.log(sumar(2, 2));  // 4
console.log(restar(7, 3)); // 4
```


# Módulos nativos 

es parte fundamental del entrorno de desarrollo backend  son bibliotecas ya incluidas en Node.js, no requiere instalarlos y estan disponible para ser importados y usarlos. 

**Ejemplos populares:**
- `fs` – para trabajar con el sistema de archivos
- `path` – para rutas de archivos
- `http` – para crear servidores web
- - `url` – para manejar URLs
- `os` – información del sistema operativo
- `crypto` – utilidades de cifrado
- `events` – sistema de eventos personalizado

**Como se usan?**
* sistema clasico
```
const fs = require('fs');
const path = require('path');
```
* sistema moderno
```
import fs from 'fs';
import path from 'path';
```
#nota: Node.js permite importar módulos nativos con `import` **sin necesidad de especificar ruta o extensión**.

## Aplicacion de modulos nativos (ejemplos)

**1. Información del sistema operativo**
```
import os from 'os';

console.log('Sistema operativo:', os.platform());
console.log('Memoria libre:', os.freemem());
console.log('CPU info:', os.cpus());
```

**2.Sistema de archivos**
```
import fs from 'fs';

// Leer un archivo de forma síncrona
const contenido = fs.readFileSync('archivo.txt', 'utf-8');
console.log(contenido);

// Escribir en un archivo
fs.writeFileSync('nuevo.txt', 'Hola Jordan!');

// Leer un archivo de forma asíncrona

```



