
🔹 **Módulos y archivos:** nombres en **minúsculas** y con guiones bajos (`snake_case`).  
✅ `mi_script.py`  
❌ `MiScript.py`

🔹 **Variables y funciones:** nombres en **minúsculas** con guiones bajos (`snake_case`).  
✅ `edad_usuario = 25`  
❌ `EdadUsuario = 25`

🔹 **Clases:** nombres en **CamelCase** (primera letra en mayúscula, sin guiones bajos).  
✅ `class Persona:`  
❌ `class persona:`

🔹 **Constantes:** nombres en **mayúsculas** y con guiones bajos (`SNAKE_CASE`).  
✅ `PI = 3.1416`  
❌ `pi = 3.1416`

🔹 **Métodos y atributos privados:** prefijo con `_` (subrayado).  
✅ `_atributo_privado`  
❌ `atributoPrivado`

🔹 **Métodos y atributos realmente privados:** doble subrayado `__`.  
✅ `__atributo_muy_privado`

----
## **📌 2. Convenciones de Espaciado y Sangría**

🔹 **Usar 4 espacios por nivel de indentación (NO tabulaciones).**

🔹 **Espacios alrededor de operadores.**  
✅ `x = 5 + 3`  
❌ `x=5+3`

🔹 **No dejar espacios dentro de paréntesis, corchetes o llaves.**  
✅ `lista = [1, 2, 3]`  
❌ `lista = [ 1, 2, 3 ]`

---
## **📌 3. Convenciones en Funciones y Clases**

🔹 **Funciones deben tener nombres descriptivos.**

```
def calcular_edad(año_nacimiento):
    return 2025 - año_nacimiento
```

🔹 **Las clases deben usar nombres en `CamelCase` y las funciones en `snake_case`.**
```
class MiClase:
    def metodo_de_clase(self):
        pass

```
🔹 **Usar docstrings (`"""comentario"""`) en funciones importantes.**
```
def sumar(a, b):
    """Devuelve la suma de dos números."""
    return a + b

```

----

## **4. Convenciones en Importaciones**

🔹 **Cada importación en una línea distinta.**
🔹 **Orden correcto de imports:**

1. **Librerías estándar de Python**
2. **Librerías externas (instaladas con pip)**
3. **Módulos del proyecto**
```
import os
import sys

import requests

from mi_proyecto import modulo

```

----
## **5. Convenciones en Estructuras de Control**

🔹 **Siempre usar paréntesis en condiciones complejas.**
```
if (edad > 18 and 
    tiene_permiso and 
    tiene_identificacion):
    print("Acceso permitido")

```
🔹 **No usar comparaciones con `True` o `False` explícitas.**
```
if activo:   # Correcto

if activo == True: # Incorrecto
```
🔹 **Usar `is None` en lugar de `== None`.**
```
✅
if variable is None:
	pass
❌
if variable == None:
    pass

```

---
## **6. Convenciones en Manejo de Excepciones**

🔹 **Siempre capturar excepciones específicas.**
```
✅
try:
    resultado = 10 / 0
except ZeroDivisionError:
    print("Error: División por cero")

❌
try:
    resultado = 10 / 0
except:
    print("Error")

```
🔹 **Evitar capturar todas las excepciones con `except Exception:` si no es necesario.**
```
try:
    archivo = open("datos.txt")
except FileNotFoundError:
    print("Archivo no encontrado")

```
---
## **📌 7. Otras Buenas Prácticas**

🔹 **Usar `with` al trabajar con archivos** (evita olvidarse de cerrar el archivo).
```
with open("archivo.txt", "r") as f:
    contenido = f.read()

```



----

## 📌 8. Ejemplo de Código con Buenas Prácticas

```
import os
from datetime import datetime

class Usuario:
    """Clase que representa a un usuario."""

    def __init__(self, nombre: str, edad: int):
        self.nombre = nombre
        self.edad = edad

    def mostrar_info(self) -> str:
        """Devuelve la información del usuario."""
        return f"Usuario: {self.nombre}, Edad: {self.edad}"

def obtener_fecha_actual() -> str:
    """Devuelve la fecha actual en formato YYYY-MM-DD."""
    return datetime.now().strftime("%Y-%m-%d")

usuario = Usuario("Jordan", 25)
print(usuario.mostrar_info())
print("Fecha actual:", obtener_fecha_actual())

```