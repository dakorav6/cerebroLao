#### **1. Métodos de Array:**

- **`.push(elemento)`**: Agrega uno o más elementos al final de un array.
- **`.pop()`**: Elimina el último elemento de un array.
- **`.shift()`**: Elimina el primer elemento de un array.
- **`.unshift(elemento)`**: Agrega uno o más elementos al principio de un array.
- **`.slice(inicio, fin)`**: Devuelve una copia superficial de una porción del array dentro de un nuevo array.
- **`.splice(indice, cantidad, elemento)`**: Cambia el contenido de un array eliminando elementos existentes y/o agregando nuevos elementos.
- **`.map(función)`**: Crea un nuevo array con los resultados de aplicar una función a cada elemento del array.
- **`.filter(función)`**: Crea un nuevo array con todos los elementos que pasen una prueba (función).
- **`.reduce(función, valorInicial)`**: Aplica una función a un acumulador y a cada valor de un array para reducirlo a un único valor.
- **`.forEach(función)`**: Ejecuta una función para cada elemento de un array.
- ==**``.sort()``**== : ordena los elementos de un arreglo alfabéticamente, en caso de numero los ordena por su primer numero o digito. 
-  ==**`.indexOf(valorBuscado, [indiceInicio])`**==:
	- **Con arrays**: Devuelve el índice de la primera aparición de un elemento en un array. Si no se encuentra, devuelve `-1`.
- ==.join(simbolo)== : convierte el arreglo en un string con un simbolo como separador entre cada elemento del arreglo, por defecto son comas. 


#### **2. Métodos de String:**

- **`.length`**: Propiedad que devuelve la longitud de una cadena.
-  **`.indexOf(valorBuscado, [indiceInicio])`**:
	- **Con cadenas**: Devuelve el índice de la primera aparición de una subcadena en una cadena. Si no se encuentra, devuelve `-1`.
- **`.toUpperCase()`**: Convierte una cadena a mayúsculas.
- **`.toLowerCase()`**: Convierte una cadena a minúsculas.
- **`.trim()`**: Elimina los espacios en blanco de ambos extremos de una cadena.
- **`.includes(subcadena)`**: Determina si una cadena puede ser encontrada dentro de otra cadena, regresando `true` o `false`.
- **`.substring(inicio, fin)`**: Devuelve una parte de la cadena entre los índices especificados.
- **`.split(separador)`**: Divide una cadena en un array de subcadenas.
- **`.replace(valorABuscar, valorDeReemplazo)`**: Reemplaza un valor especificado con otro valor en una cadena.
- ``.repeat(x)`` : repite el string la x cantidad de veces 
- `` . endsWith ('A')`` : sirve para saber si la cadena termina con ese caracter. 
- ``.startsWith ('A')`` : sirve para saber si la cadena inicia con ese caracter. 
#### **3. Funciones Globales:**

- **`alert(mensaje)`**: Muestra un cuadro de alerta con un mensaje.
- **`console.log(mensaje)`**: Muestra un mensaje en la consola de desarrollo.
- **`parseInt(cadena, base)`**: Convierte una cadena en un número entero.
- **`parseFloat(cadena)`**: Convierte una cadena en un número de punto flotante.
- **`isNaN(valor)`**: Determina si un valor es NaN (Not-a-Number).

#### **4. Métodos del Objeto `Math`:**

- **`Math.random()`**: Devuelve un número pseudo-aleatorio entre 0 (inclusive) y 1 (exclusivo).
- **`Math.floor(numero)`**: Redondea un número hacia abajo al entero más cercano.
- **`Math.ceil(numero)`**: Redondea un número hacia arriba al entero más cercano.
- **`Math.round(numero)`**: Redondea un número al entero más cercano.
- **`Math.max(...valores)`**: Devuelve el número mayor de los argumentos proporcionados.
- **`Math.min(...valores)`**: Devuelve el número menor de los argumentos proporcionados.
- **`Math.sqrt(x)`** : la raiz cuadrada de x 
- **`Math.pow(x,y)`** : x elevado a la y 
- **`Math.abs(x)`** : devulve el valor absoluto de x sin desimal
#### **5. Métodos de Manipulación del DOM:**

- **`document.getElementById(id)`**: Devuelve el elemento que tiene el ID especificado.
- **`document.querySelector(selectores)`**: Devuelve el primer elemento que coincide con los selectores especificados.
- **`document.querySelectorAll(selectores)`**: Devuelve una lista de todos los elementos que coinciden con los selectores especificados.
- **`element.addEventListener(evento, función)`**: Asocia una función a un evento de un elemento.
- **`element.classList.add(clase)`**: Añade una o más clases al elemento.
- **`element.classList.remove(clase)`**: Elimina una o más clases del elemento.
- **`element.innerHTML`**: Propiedad que obtiene o establece el HTML dentro de un elemento.

#### **6. Métodos de Promesas y Asincronía:**

- **`fetch(url)`**: Realiza una solicitud HTTP para obtener datos de una URL y devuelve una promesa.
- **`.then(función)`**: Adjunta funciones que se ejecutarán después de que la promesa sea resuelta.
- **`.catch(función)`**: Adjunta funciones que se ejecutarán cuando la promesa sea rechazada.
- **`async` y `await`**: Palabras clave para manejar asincronía de manera más legible y ordenada.

