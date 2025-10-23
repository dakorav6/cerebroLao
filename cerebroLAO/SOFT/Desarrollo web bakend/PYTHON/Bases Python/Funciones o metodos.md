

- Declaración  ``def  nomFuncion():``
-  llamar a la función => ``nomFuncion()``
- al igual que las variables no se inicializa el tipo si queremos que retorne solo ponemos el return y recuerda la sangria de espacio por que no se usan los corchetes 
```
def funcion_suma(a, b): 
	return a + b 
	
suma = funcion_suma(3, 5)
print("La suma es", suma) 
# Salida: La suma es 8
```

#nota cuando colocas un `*` delante de un nombre de parámetro (como en `*numeros`), esa función puede recibir cualquier cantidad de argumentos, y todos esos argumentos serán recogidos en una **tupla** dentro de la función. En el ejemplo, en la llamada `sumar(1, 2, 3)`, **`numeros`** se convierte en la tupla `(1, 2, 3)`.
```
def sumar(*numeros):
    return sum(numeros)

# Llamamos a la función con diferentes números de argumentos
print(sumar(1, 2, 3))          # Salida: 6
print(sumar(10, 20))           # Salida: 30
print(sumar(4, 5, 6, 7, 8))    # Salida: 30
```

#nota si ponemos `pass` dentro del cuerpo de una función podemos dejarla vacía solo para declararla . 
```
def ejemFuntion(self):

    pass
```

---

# Funciones lambda
- funciones  para vagos 
- son funciones que no tienen nombre 
- Son útiles cuando necesitas una función simple y temporal que no será reutilizada en otro lugar.
- `` lambda argumentos: expresión``
	- **`argumentos`**: una lista de parámetros (puede ser vacía).
	- **`expresión`**: el cuerpo de la función, que solo puede tener una expresión (no declaraciones). El resultado de esta expresión es lo que la función devuelve.
	
```
# Definiendo una función lambda que suma 2 números
suma = lambda x, y: x + y 

# Usando la función 
resultado = suma(3, 5)
print(resultado)
```
## 1. Usando `lambda` con `map()`:
La función `map(funcion, iterable)` aplica una función a todos los elementos de una lista.
```
numeros = [1, 2, 3, 4, 5] 

# Usando lambda para elevar al cuadrado cada número 
cuadrados = list(map(lambda x: x**2, numeros)) 
print(cuadrados)

#resultado: [1, 4, 9, 16, 25]
```

## 2. Usando `lambda` con `filter()`:
La función `filter()` filtra elementos de una lista (o iterable) según una condición dada por una función.
```
numeros = [1, 2, 3, 4, 5, 6] 
# Usando lambda para filtrar números pares
pares = list(filter(lambda x: x % 2 == 0, numeros)) 
print(pares)

#resultado: [2, 4, 6]
```
## 3. Usando `lambda` con `sorted()`:
La función `sorted()` puede ordenar listas o colecciones. Puedes usar una función `lambda` para definir un criterio de ordenación.
```
# Lista de tuplas (nombre, edad) 
personas = [("Jordan", 28), ("Ana", 22), ("Luis", 31)]

# Usando lambda para ordenar por edad 
personas_ordenadas = sorted(personas, key=lambda x: x[1]) print(personas_ordenadas)

#resultado: [('Ana', 22), ('Jordan', 28), ('Luis', 31)]

```

---

# Yield (generadores) 

- se utiliza en una función para convertirla en un **generador**.
- Cuando una función contiene la palabra clave **`yield`**, en lugar de devolver un valor (``return``) y finalizar, **`yield`** permite que la función "pause" su estado y retorne un valor al mismo tiempo.
- La función puede luego reanudar su ejecución desde donde se detuvo, lo que permite producir una secuencia de valores a lo largo del tiempo
- conclusión: cada vez que llamas a la función generadora, esta te dará el siguiente valor en la secuencia, uno a la vez, en lugar de devolver todos los valores 

```
def contador(limite):
    for i in range(limite):
        yield i  # Pausa aquí y devuelve el valor de i

# Usamos el generador
for numero in contador(5):
    print(numero)

#salida: 0 1 2 3 4

# tambien podemos imprimir numero por numero 

numCon=generaNumero(5)

print(next(numCon))
print(next(numCon))
print(next(numCon))
print(next(numCon))
print(next(numCon))

#salida:
0
1
2
3
4
```

un ejercicio hecho por mi que genera numeros primos 
```
#generar primos con generador 

def esPrimo(num):
	primo = True

	for i in range(2,int(num**0.5)+1):
		if num% i ==0 : primo=False 
	return primo


def generadorPrimos(limite):
	

	for i in range(2,limite):
		if esPrimo(i) : yield i 

numeroPrimo=generadorPrimos(10)

print(next (numeroPrimo)) 
print(next (numeroPrimo)) 
print(next (numeroPrimo)) 
print(next (numeroPrimo)) 
```
#### next() 

El **`next()`** en Python se utiliza para obtener el siguiente valor de un **iterador** o **generador**. Cada vez que llamas a **`next()`**, el generador o iterador produce el siguiente valor disponible, y si no hay más valores disponibles, lanza una excepción **`StopIteration`**.
#### yield  from 
nos permite simplificar el codigo en lugar de usar un for anidados para sacar los elementos que estan dentro de una lista de otra lista ejemplo: `[[1,2,3],[4,5,6],[7,8,9]]`

```
def devuelveLetras(*nombres):
	for elemento in nombres:
		yield from elemento

letras= devuelveLetras("Jordan","Andrea","Liam","Ranita")

print(next(letras))
print(next(letras))
print(next(letras))

resultado: 
J
o
r
```

----

# Decorador (Falta informacion)

Un **decorador** es esencialmente una función que recibe otra función como parámetro, la modifica o extiende su comportamiento, y luego devuelve una nueva función. Es como un "envoltorio" para añadir funcionalidad adicional a una función ya existente

Ejemplo: Aquí, `mi_decorador` es un decorador que toma una función `func`, imprime algo antes y después de llamar a la función, y luego devuelve una nueva función.
```
def mi_decoradorCualquierNombre(func):
    def nueva_funcion():
        print("Antes de ejecutar la función")
        func()  # Llama a la función original
        print("Después de ejecutar la función")
    return nueva_funcion

```

## Cómo usar un decorador: la sintaxis `@`
Para aplicar un decorador a una función, se usa la sintaxis especial `@decorador` justo antes de la definición de la función que quieres decorar.
```
@mi_decoradorCualquierNombre
def saludar():
    print("Hola, mundo!")


saludar()

#CONSOLA:
Antes de ejecutar la función 
Hola, mundo! 
Después de ejecutar la función
```

