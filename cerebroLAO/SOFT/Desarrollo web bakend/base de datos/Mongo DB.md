estudiante:  Orbe Rojas Jordan 

NoSQL
las bases de datos NoSQL están diseñadas para manejar grandes volúmenes de datos

ejemplos de BD NoSQL 
- amazon DynamoDB
- Cassandra
- Google Big Table

ejemplo de sistema de manejo de BD 
- MONGO DB
- COUCHDB
- SIMPLE DB 


### Mongo DB 
- Es una base de datos NoSQL de tipo documento
- no se basa en tablas y columnas. Mongo DB contiene colecciones que a su vez contiene documentos. 
- cada documento debe tener un id obligatorio 
- Una colección es un grupo de documentos 
- las colecciones deben estar escritas en plural como norma
- En MongoDB, que es una base de datos NoSQL, no es necesario declarar el tipo de datos de las variables
- En MongoDB, puedes insertar documentos con diferentes estructuras y tipos de datos en la misma colección sin ninguna configuración previa.

### Gestión de los datos en Mongo DB
- String => {"name": "keyboard"}
- numero =>{"price": 29.99} 
- Booleanos => {"available": true}
- Fechas (Dates) => Generalmente se utilizan con el constructor `ISODate` o `new Date()`.
	- {"releaseDate": ISODate("2023-07-31T00:00:00Z")}
- Arreglos (Arrays) => {"tags": ["electronics", "accessories"]}


### herramientas (id)
- Compass => es la interfaz grafica por defecto en mongo DB (podriamos probar con DOCKER)
- Robot 3T dicen que es mejor que compass por ser mas rapido y ligero

### Comandos


- crear y usar una base de datos => `use nomBD`
- mostrar base de datos=> `show dbs` #nota solo te va  a mostrar las base de datos que tenga al menos un documento creado por eso que al momento de crearlo con el use no podemos ver la creacion de la bd 
- limpiar comando=> `clear`


**Colecciones** 
- mostrar colecciones => `show collections`
- crear coleccion => `db.createCollection("products")`
- eliminar coleccion => `db.products.drop()`

**Documentos**
- mostrar documentos de una colección => `db.nomColeccions.find()`
	- mostrar documento filtrando busqueda=> `db.products.find({name: "mouse"})`
- mostrar documentos en un mejor formato visual=>`db.products.find().pretty()`
	- mostrar documento filtrando busquda=>`db.products.find({price: 999.99}).pretty()`
- insertar un documento a la colección => `db.products.insert({"name": "keyboard"})`
	- `db.products.insert({"_id": 1, "name": "keyboard"});`
	- `db.products.insert([{"name": "mouse","description": "razer mouse","tags": ["computers", "gaming"],"quantity": 14,"created_at": new Date()},{"name": "monitor","description": "lg monitor","tags": ["computers", "gaming"],"quantity": 3,"created_at": new Date()}])`
- insertar multiples documentos en una coleccion => 
```
db.usuario.insertMany([
    {
        "nombre_usuario": "usuario1",
        "cuenta_twitter": "@usuario1",
        "nombre": "Nombre1",
        "descripcion": "Descripción del usuario 1",
      
    },
    {
        "nombre_usuario": "usuario2",
        "cuenta_twitter": "@usuario2",
        "nombre": "Nombre2",
        "descripcion": "Descripción del usuario 2",
    },
]);
```

#nota cada documento que insertamos tiene un **`_id`**: MongoDB automáticamente agrega un campo `_id` a cada documento insertado si no lo especificas. Este campo es único para cada documento y se utiliza como clave primaria.
 
**Anidación de documentos** 
en MongoDB es posible anidar documentos dentro de otros documentos, lo que permite crear estructuras de datos jerárquicas.
ejemplo:
```
   {
        nombre_usuario: "usuario1",
        cuenta_twitter: "@usuario1",
        nombre: "Nombre1",
        descripcion: "Descripción del usuario 1",
        telefonos: ["123456789"],
        direccion: {
            calle: "Calle 1",
            numero: "1",
            ciudad: "Ciudad1",
            cp: "10001"
        }
    }
```
#nota puedes anidar documentos dentro de otros documentos sin restricciones específicas de profundidad de anidación. Esto significa que puedes tener un documento que contiene otro documento, y ese documento interno puede contener a su vez otro documento, y así sucesivamente. Pero se debe considerar buenas practicas y el ==uso de Referencias.== 


---

### Consultas 
- selección múltiple parámetro =>  
	- `db.products.find({"tags": "computers", "name": "monitor"})`
- ver el primer elemento que contenga el valor =>  
	- `db.products.find({"tags": "computers", "name": "monitor"})`
- ?¿ --ver los productos que tengan como valor en su atributos tags "computers" (pero solo obtener el nombre y la descripcion)
db.products.findOne({"tags": "computers"},{"name": 1, "description": 1})
- filtrar busqueda y ordenar alfabeticamente por su nombre =>  
	- `db.products.find({"tags": "computers"}).sort({name: 1})`
- mostrar solo 2 productos (por defecto se mostraria segun el orden en el que fueron ingresados)=>
	- `db.products.find().limit(2)`
- contar cuentos documentos tiene una coleccion => 
	- `db.products.count()`
- mostrar todos los documentos de una coleccion pero solo mostrar el nombre =>
	- `db.products.find().forEach(product => print("Product Name: " + product.name))`

### Actualizar datos
- actualizar valor de un documento con un nombre para filtrar ejemplo:  "keyboard"
	- `db.products.update({"name": "keyboard"},{$set:{"price": 99.99}})`
- actualizar documento añadiendo mas atributos o variables 
	- `db.products.update({"name": "laptop"}, {$set: {"description": "lg gran laptop"}})`
- ?¿ no entiendo: 
	- --Actualizar el producto con nombre "desktop" (para que a pesar que no exista lo guarde y se agreguen otros datos) db.products.update({"name": "desktop"}, {$set: {"description": "Gaming Desktop"}}, {upsert: true})
* actualizar documento solo para incrementar un valor numerico 
	* `db.products.update({"name": "keyboard"}, {$inc: {"price": 0.01}})`
- Actualizar o cambiar el nombre de un atributo ejemplo: cambiar nombre "name" a "nombre"=> 
	- `db.products.update({"name": "laptop"}, {$rename: {"name": "nombre"}})`
	
### Eliminar
- eliminar un documento filtrando por nombre 
	- `db.products.remove({"nombre": "keyboard"})`
- elimina todos los documentos de una coleccion 
	- `db.products.remove({})`


----

### Indice Unico 
Un índice único en MongoDB  garantiza la unicidad de los valores en los campos indexados. Esto significa que no puede haber dos documentos en la colección con el mismo valor.

```
db.nomColeccion.createIndex(
    { "nombre_usuario": 1, "cuenta_twitter": 1 },
    { unique: true }
);
otro ejemplo:
db.usuarios.createIndex({ email: 1 }, { unique: true })

```
- `{ email: 1 }` define el campo `email` como índice en orden ascendente. (-1 para descendente)
- `{ unique: true }` establece el índice como único.

Para saber que elementos tienen indice unico: `db.usuario.getIndexes()`


---
### Operadores de Comparación
(`>=`, `<=`, `>`, `<`)

MongoDB utiliza una sintaxis JSON para las consultas, lo que implica que los operadores de comparación deben estar representados como claves en un objeto.

```
db.usuarios.find({ "edad": { $gte: 18 } })

```
- Esto selecciona todos los documentos en la colección `usuarios` donde el campo `edad` es mayor o igual a 18.
```
db.usuarios.find({ "salario": { $lt: 50000 } })

```
- Esto selecciona todos los documentos en la colección `usuarios` donde el campo `salario` es menor que 50,000.

 **Resumen de Operadores de Comparación**

- `$eq`: Igual a.
- `$ne`: No igual a.
- `$gt`: Mayor que.
- `$gte`: Mayor o igual que.
- `$lt`: Menor que.
- `$lte`: Menor o igual que.
