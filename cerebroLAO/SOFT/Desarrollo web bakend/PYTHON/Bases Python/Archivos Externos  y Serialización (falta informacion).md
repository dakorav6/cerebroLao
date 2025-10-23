
---
# With ... as
La sentencia `with ... as` en Python se utiliza para gestionar **recursos** que deben abrirse y luego cerrarse, o configurarse y luego limpiarse, de manera **automática** como archivos, conexiones de red, bases de datos, entre otros.
su proceso seria:
- **Configura el recurso** (como abrir un archivo).
- **Ejecuta un bloque de código** que usa el recurso.
- **Limpia todo al terminar** el bloque, incluso si ocurre un error.
ejemplo esta en el siguiente tema "Archivos Externos"

----

# Archivos Externos 

Aqui el objetivo es la persistencia de datos o el guardar información de la aplicación 

para esto tenemos 2 opciones:
1. Guardar en archivos externos 
2. trabajar con bases de datos 

## Archivos Externos: 

- existen 3 modos de abrir 
	1. lectura "r" => da error si el archivo no existe
	2. escritura `w` => crea el archivo si no existe, borra el contenido si ya existe
	3. append "a" => añade contenido sin borrar lo existente
	4. lectura y escritura "r+" =>(no borra el contenido, pero da error si el archivo no existe).

### Crear y escribir en un archivo de texto
```
with open("archivo.txt", "w") as archivo:

    archivo.write("¡Hola, Jordan!\n")

    archivo.write("Este es un archivo de texto creado desde Python.\n")
```
### Leer un archivo de texto
```
# Abrir el archivo en modo lectura ('r')
with open("archivo.txt", "r") as archivo:
    contenido = archivo.read()

# Mostrar el contenido del archivo
print(contenido)
```
### Añadir información a un archivo existente
```
# Abrir el archivo en modo de añadir ('a')
with open("archivo.txt", "a") as archivo:
    archivo.write("Esta es una nueva línea añadida.\n")

```

----
# Serialización

la serialización convierte datos en algo que pueda ser fácilmente guardado o enviado.


**a) Serializar un objeto usando Pickle:**
```
import pickle

# Un objeto Python (en este caso, un diccionario)
datosPersonales = {
    "nombre": "Jordan",
    "edad": 29,
    "lenguajes": ["Python", "JavaScript"],
    "casado": True
}

# Serializar el objeto con pickle
with open("datos.pkl", "wb") as archivo_pickle:
    pickle.dump(datosPersonales, archivo_pickle)

print("Datos serializados con Pickle y guardados en archivo")
```
- **`pickle.dump(objeto, archivo)`** serializa el objeto y lo guarda en un archivo binario. Usa el modo `"wb"` (write binary) para escribir el archivo.
- crea el archivo si no esta creado


b) Deserializar un objeto desde Pickle:

```
import pickle

# Deserializar (cargar) el objeto desde el archivo pickle
with open("datos.pkl", "rb") as archivo_pickle:
    datos_recuperados = pickle.load(archivo_pickle)

print("Datos deserializados desde Pickle:", datos_recuperados)

```
- **`pickle.load(archivo)`** deserializa el objeto guardado en el archivo binario. Usa el modo `"rb"` (read binary) para leer el archivo.

(FALTA INFORMACION)