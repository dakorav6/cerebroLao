cursos o fuente de conocimiento:
- https://ellibrodepython.com/
- https://www.youtube.com/watch?v=ZFPqYyd0Hh8

- es un lenguaje interpretado(eso quiere decir que la computadora tiene un interprete que transforma python a lenguaje de maquina)
- archivos python tienen la extencion .py

---
# básico 

- ``print ("Hola mundo");``
- Ingreso de datos consola =>``nomVariable=  input( " Texto solicitar dato " )``
- ``# esto es un comentario``
- las ``variables`` va ser del tipo de dato que este contenga , solo ponemos el nombre de la variable y el = , ejemplo: x=5; 
-  Podemos realizar múltiples asignaciones ``a, b, c = 4, 3, 2``
- `False`, `True`  booleanos siempre la primera letra en mayúscula 
- El `and`, `or` y `not` son operadores lógicos 
- conversión a entero  `int(nomVariable)`
- para trabajar con calculos matematicos se debe importa `import math` y poder usar operaciones como raiz cuadrada `math.sqrt(nomVariable)`
---

# Concatenación y bloques de código 

- aquí los bloques de código no se limitan con los { } simplemente iniciamos con los dos puntos (:) con la identacion (nombre técnico en software lo que conocemos notros como sangría) limitamos el bloque de código y tampoco es necesario el ( ; ) sin embargo se puede usar para tener 2 sentencia en la misma linea `x = 5; y = 10` , ejemplo:
```
a = 10
if a == 10:
    print("Es 10")
else:
    print("No es 10")
```

- concatenas con el +  pero solo puedes concatenar cadenas de caracteres al quiere poner un numero tenemos que transformarlo con el str(nomVariable)
```
x = 10 
y = 20 
print("Los valores x, y son: " + str(x) + " , " + str(y))
```
- otra forma de concatenar es solo separarlo con comas `, `
```
x = 10
y = 20
print("Los valores x, y son:",  x   ,  y)
# Salida: Los valores x, y son: 10 20
```

- f-strings
	- son mas legibles y eficientes
	- evita errores de conversión automática 
```
def fechaActual(request):
    fecha_actual = datetime.datetime.now()
    documento = f'La fecha y hora actual es: {fecha_actual}'
    return HttpResponse(documento)

```



-  (  \ ) podemos romper el código en varias líneas, lo que en determinados casos hace que el código sea mucho más legible o solo podemos poner en paréntesis y solo dar un salto de linea.
```
opcion 2
x = 1 + 2 + 3 + 4 +\ 
5 + 6 + 7 + 8
opcion 1
x = (1 + 2 + 3 + 4 + 
5 + 6 + 7 + 8)
```



---
# Condicionales 
## if -elif - else 
```
x = 5
if x == 5:
    print("Es 5")
elif x == 6:
    print("Es 6")
elif x == 7:
    print("Es 7")
else:
    print("Es otro")
```
## operador ternario 
"código si se cumple" ``if`` condición`` else`` "código si no se cumple"
```
x = 5 
print("Es 5" if x == 5 else "No es 5") 
#Es 5
```

Si por ejemplo tenemos una variable a la que queremos asignar un valor en función de una condición.
```
a = 10
b = 5
c = a/b if b!=0 else -1
print(c)
#2
```


---
# Bucles 

- ``Do-while`` : no existe en python :C
- En Python no existe el switch

## for
`for` :  permite iterar clases iterables ( #nota aqui no hay ``for...of `` y tampoco existe el for tradicional con rango ``for (int i = 0; i < 5; i++)``)
```
for i in range(3): 
	print(i) 

# Salida: 0, 1, 2

#alternativa el for tradicional con rango ``for (int i = 0; i < 5; i++)

ejemplo 1:
for i in range(0, 5):
    print(i)

# Salida:
# 0
# 1
# 2
# 3
# 4

ejemplo 2:
for i in range(1, 10, 2):
	print(i)

```

#nota el uso de `range(5)` genera una secuencia de números del 0 al 4 y si quieres controlar el inicio, fin y incremento , puedes pasar más parámetros a 
`range(1, 10, 2)` en ese orden inicio , fin , incremento.
### for anidados 
```
lista = [[56, 34, 1], [12, 4, 5], [9, 4, 3]]

for i in lista:
    for j in i:
        print(j)
# Salida: 56,34,1,12,4,5,9,4,3


```

## while 
```
x = 5
while x > 0:
    x -=1
    print(x)

# Salida: 4,3,2,1,0
```

##  `break` y `continue`

### break
nos permite alterar el comportamiento de los bucles while y for, una vez se encuentra la palabra break, el bucle se habrá terminado.
### Continue 
La diferencia entre el `break` y `continue` es que el `continue` no rompe el bucle, si no que pasa a la siguiente iteración saltando el código pendiente.

---

## 🔹 **Truthy vs Falsy en Python**

### ✅ **Truthy (se evalúan como `True`)**

Son valores que, cuando se usan en un contexto booleano, se consideran `True`. Algunos ejemplos:

- **Números distintos de cero** (`1`, `-42`, `3.14`, etc.)
- **Cadenas de texto no vacías** (`"Hola"`, `"Python"`, etc.)
- **Listas, tuplas, conjuntos y diccionarios con elementos** (`[1, 2, 3]`, `{"clave": "valor"}`)
- **Cualquier objeto que no sea explícitamente `False`**

### ❌ **Falsy (se evalúan como `False`)**

Son valores que Python considera `False` en un contexto booleano:

- **El número `0`** (`0`, `0.0`)
- **Cadenas vacías** (`""`)
- **Listas, tuplas, conjuntos y diccionarios vacíos** (`[]`, `{}`, `()`)
- **El valor `None`**
- **El booleano `False`**


---

# Generar Ejecutable

1. debemos instalar py instaler desde la consola de windows `pip install pyinstaller`
2. abrir desde la ventana donde esta nuestro proyecto la consola o poner la ruta en consola donde esta el proyecto 
3. escribimos `installer nombreProyecto.py`
4. se generaran ficheron y carpetas, en la carpeta dist - nombreProyecto.exe 

- pero el problema es que se genera la aplicacion con una consola de fondo y se ve feo 
	- alternativa ejecutar en consola: `--windoweb --onefile nombreProyecto.py`

- quieres un icono personalizado? 
	en la carpeta donde esta el proyecto tienes que acompañarlo con un logotico con extencion .ico 
	y añadir una instruccion mas 
	`--windoweb --onefile --icon-./logo. nombreProyecto.py
