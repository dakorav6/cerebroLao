
# No requieren importar módulos


# Números

```
# Valor absoluto
abs(-10)  # 10

# Potencias y raíces
pow(2, 3)   # 8 (2^3)
2 ** 3      # 8 (otra forma)
9 ** 0.5    # 3.0 (raíz cuadrada)

# Redondeo
round(3.1416, 2)  # 3.14 (2 decimales)
round(3.5)        # 4 (redondeo estándar)

# Mínimo y máximo
min(5, 10, 3)  # 3
max(5, 10, 3)  # 10

# Suma y promedio
sum([1, 2, 3, 4])  # 10
len([1, 2, 3, 4])  # 4 (número de elementos)
```

# String 
mas métodos de cadena: https://pyspanishdoc.sourceforge.net/lib/string-methods.html 


string (x=>variable)
- convertir cualquier cosa   a string=>  srt(x) 
- longitud de cadena  => len (x)
- cambiar todo mayucula=> x.upper()
- cambiar todo minuscula=> x.lower();
- cambiar primera letra en mayuscula => x.capitalize();
- contar cuantos caracteres aparece en la cadena=> x.count("a");
- buscar y devuelve la posición  => x.find("A")
- buscar y devolver la posicion desde atras hacia el inicio => x.rfin("")
- comprueba si solo hay letras => x.isalpha()
- comprueba si hay letras y numeros (alfanumericos) => x.isalpha()
- Dividiendo por espacios (sin separador especificado) => ``resultado = texto.split()``
	- ejemplo:
```
#ejemplo 1
texto = "Hola, ¿cómo estás?"
resultado = texto.split()
print(resultado)  # ['Hola,', '¿cómo', 'estás?']

ejemplo 2:
texto = "manzana,banana,naranja" 
resultado = texto.split(",") 
print(resultado) # ['manzana', 'banana', 'naranja']
```
- borra los espacio sobrantes al principio y al final => x.strip()
- remplaza una palabra o letra por otra =>  x.replace("e" , "a ")
- si empieza con determinado caracter => x.startswith("a")
- si termina con determinado caracter => cadena.endswith("o")


## Funciones para Listas y Tuplas

```
lista = [3, 1, 4, 1, 5, 9]
lista.append(6)    # Agregar un elemento
lista.remove(1)    # Eliminar la primera aparición de 1
lista.sort()       # Ordenar ascendente
lista.reverse()    # Invertir la lista

# Acceder a elementos
primero = lista[0]   # Primer elemento
ultimo = lista[-1]   # Último elemento

# Otras funciones útiles
len(lista)     # Número de elementos
sum(lista)     # Suma de todos los elementos
min(lista)     # Mínimo
max(lista)     # Máximo

```

## Funciones para diccionario 

```
dic = {"nombre": "Jordan", "edad": 25}

# Obtener un valor
edad = dic.get("edad")  # 25

# Obtener claves, valores o ítems (clave-valor)
claves = dic.keys()   # dict_keys(['nombre', 'edad'])
valores = dic.values() # dict_values(['Jordan', 25])
items = dic.items()   # dict_items([('nombre', 'Jordan'), ('edad', 25)])

# Agregar o modificar elementos
dic["profesion"] = "Desarrollador"

# Eliminar elementos
del dic["edad"]

```



----

# Requieren importar

## Funciones calculos matematicos (requiere math)

```
import math
math.sqrt(16)   # 4.0 (raíz cuadrada)
math.ceil(4.2)  # 5 (redondeo hacia arriba)
math.floor(4.8) # 4 (redondeo hacia abajo)
math.factorial(5) # 120 (5!)
math.log(100, 10) # 2.0 (logaritmo base 10)
math.pi        # 3.141592653589793
math.e         # 2.718281828459045

```

## Funciones para fechas (datetime)
```
from datetime import datetime, timedelta

# Obtener la fecha y hora actual
now = datetime.now()
print(now)  # 2025-02-07 12:34:56.789000

# Formatear fechas
print(now.strftime("%Y-%m-%d %H:%M:%S"))  # '2025-02-07 12:34:56'

# Convertir de string a fecha
fecha = datetime.strptime("2025-02-07", "%Y-%m-%d")

# Sumar/restar días
nueva_fecha = now + timedelta(days=5)  # Fecha actual + 5 días

```


