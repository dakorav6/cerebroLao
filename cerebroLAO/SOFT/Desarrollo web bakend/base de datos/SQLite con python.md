- sqlite forma parte del programa que desarrollamos esto trae ciertas ventajas como que ocupe poco espacio y sea eficiente y rapido. 
- sin administrados /  no existen usuarios 
- **SQLite** es una base de datos ligera y fácil de usar que no requiere configuración de servidor, lo que la hace perfecta para pequeños proyectos, aplicaciones móviles o prototipos.
- Es la base de datos por defecto en Django y se almacena en un solo archivo en disco.
- SQLite no utiliza un servidor separado, sino que se almacena como un archivo en el sistema de archivos.
- SQLite es de código abierto y se puede usar de forma gratuita, con una licencia de dominio público.


1. **Conectar a una base de datos SQLite**

Primero necesitas importar el módulo `sqlite3` y luego establecer una conexión con una base de datos. Si la base de datos no existe, Python la creará por ti.

```
import sqlite3

# Conectar a una base de datos o crearla si no existe
conexion = sqlite3.connect('mi_base_de_datos.db')

# Crear un cursor para interactuar con la base de datos
cursor = conexion.cursor()

print("¡Conexión a la base de datos establecida!")

```
2.  **Crear una tabla**

Vamos a crear una tabla llamada `usuarios` con columnas `id`, `nombre`, y `edad`.
```
# Crear la tabla usuarios (si no existe)
cursor.execute('''
    CREATE TABLE IF NOT EXISTS usuarios (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        nombre TEXT NOT NULL,
        edad INTEGER NOT NULL
    )
''')

# Guardar (commit) los cambios
conexion.commit()

print("¡Tabla creada!")

```
#nota la triple comilla es útil cuando la instrucción es larga 
3. **Insertar datos en la tabla**

Puedes insertar filas en la tabla usando SQL con la función `execute`.
```
# Insertar un usuario en la tabla
cursor.execute("INSERT INTO usuarios (nombre, edad) VALUES ('Jordan', 29)")
cursor.execute("INSERT INTO usuarios (nombre, edad) VALUES ('Andrea', 27)")

# Guardar los cambios
conexion.commit()

print("¡Datos insertados!")

```

4.  **Consultar datos**

Para obtener datos de la tabla, usamos la sentencia `SELECT`.
```
# Seleccionar todos los usuarios
cursor.execute("SELECT * FROM usuarios")

# Obtener todos los resultados
usuarios = cursor.fetchall()

# Mostrar los resultados
for usuario in usuarios:
    print(usuario)

# Ejemplo de output: (1, 'Jordan', 29), (2, 'Andrea', 27)

```
- **`fetchall()`**: Devuelve todos los registros de la consulta como una lista de tuplas.

5. **Actualizar y eliminar registro**
También puedes actualizar o eliminar registros con las sentencias SQL correspondientes.

 a) Actualizar un registro:
 ```
# Actualizar la edad de un usuario
cursor.execute("UPDATE usuarios SET edad = 30 WHERE nombre = 'Jordan'")

# Guardar los cambios
conexion.commit()

print("¡Usuario actualizado!")
 
```
b) Eliminar un registro:
```
# Eliminar un usuario por nombre
cursor.execute("DELETE FROM usuarios WHERE nombre = 'Andrea'")

# Guardar los cambios
conexion.commit()

print("¡Usuario eliminado!")
```

6. **Cerrar la conexión**
```
# Cerrar la conexión
conexion.close()

print("¡Conexión cerrada!")
```

