
## Captura de Excepciones 
El uso de `try`, `except` y `finally` nos permite controlar errores y actuar en consecuencia sin que el programa se pare. Esto es importante que el programa no caiga. 

```
try:
    numero = 10 / 0
except Exception as e:
    print("Error: No puedes dividir por cero.",e )

#consola: 
Error: No puedes dividir por cero. division by zero
```

ejemplo de ingreso de numeros con un bucle while 

```
while True:
    try:
        op1 = int(input("Ingrese un número: "))
        break  # Salir del bucle si la conversión es exitosa
    except Exception as e:  # Por si ocurre otro tipo de error inesperado
        print("Error inesperado:", e)

print("El número ingresado es:", op1)
```


- `finally` va a ejecutar el bloque de codigo contenido en el mismo sin importar que suceda o no la excepción, en que nos podría servir eso? pues podríamos cerrar la conexión con la base de datos .
## Lanzar Excepciones 

``raise NombreDeLaExcepcion("Mensaje de error que nos de la gana")``

Puedes lanzar cualquier tipo de excepción (por ejemplo, `ValueError`, `TypeError`, `KeyError`, entre otros) o incluso crear tus propias excepciones personalizadas. Debe de trabar consecuente a un control de flujo para caer en dicha excepción. 

```
def evaluaNum(num):
    if num< 0:
        raise TypeError("El numero es negativo")
    if num>0:
        return "El numero es correcto"

print(evaluaNum(-2))
```

- también podemos trabajar con clases personalizadas que heredan de la clase base Exception para gestionar errores esto lo veremos mas adelante....

---
# Expresiones Regulares

Las **expresiones regulares** son patrones que te permiten buscar, validar, extraer y manipular texto de una manera flexible y poderosa.

### Casos de uso comunes:

1. **Validación de datos**:
    
    - Asegurarse de que una dirección de correo electrónico tenga el formato correcto.
    - Verificar si una contraseña cumple con ciertos requisitos (números, letras, símbolos).
    - 
2. **Buscar y extraer texto**: como buscar todas las URLS y extraer numeros de telefonos 
3. Remplaza todas las apariciones de una palabra en un texto.
4. elimina caracteres no deseados
5. divide cadena de caracteres 


# Como de usa?

1. importamos `import re`
2. Funciones básicas:
	- **`re.match()`**: Comprueba si un patrón coincide desde el **principio** de una cadena.
	- **`re.search()`**: Busca el patrón en **cualquier parte** de la cadena.
	- **`re.findall()`**: Encuentra todas las coincidencias del patrón en la cadena.
	- **`re.sub()`**: Sustituye partes del texto que coincidan con el patrón.

```
import re

patron = "Hola"
cadena = "Hola, ¿cómo estás?"

if re.match(patron, cadena):
    print("Coincide")
else:
    print("No coincide")

```
Ejemplo 2: Buscar una palabra dentro de una cadena
```
import re

patron = r"Python"
cadena = "Estoy aprendiendo Python y es interesante."

resultado = re.search(patron, cadena)

if resultado:
    print("Palabra encontrada")
else:
    print("Palabra no encontrada")

```
Ejemplo 3: Encontrar todas las palabras en mayúsculas
```
import re

cadena = "Me llamo JORDAN y vivo en ECUADOR."
patron = r"\b[A-Z]+\b"

palabras_mayusculas = re.findall(patron, cadena)
print(palabras_mayusculas)  # Salida: ['JORDAN', 'ECUADOR']
```
Ejemplo 4: Reemplazar un texto
```
import re

cadena = "Quiero aprender Python. Python es genial."
patron = r"Python"

# Reemplaza "Python" por "programación"
nueva_cadena = re.sub(patron, "programación", cadena)
print(nueva_cadena)  # Salida: Quiero aprender programación. programación es genial.

```
5. **Modificadores útiles**: 
**`re.IGNORECASE`**: Hace que la búsqueda sea **insensible a mayúsculas y minúsculas**.

```
import re

cadena = "Hola Mundo"
patron = r"mundo"
resultado = re.search(patron, cadena, re.IGNORECASE)

if resultado:
    print("Coincidencia encontrada")

```
6. **Grupos**:Puedes capturar partes específicas de una cadena utilizando paréntesis `()`. Estos se llaman **grupos**.
Ejemplo: Extraer partes de una fecha
```
import re

patron = r"(\d{2})/(\d{2})/(\d{4})"
fecha = "Nací el 15/08/1994."

resultado = re.search(patron, fecha)
if resultado:
    dia, mes, anio = resultado.groups()
    print(f"Día: {dia}, Mes: {mes}, Año: {anio}")

```
Aquí, `(\d{2})` captura el día y el mes, y `(\d{4})` captura el año.


---
