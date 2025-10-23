
### Listas (arreglos para otros lenguajes)

- sintaxis: `mi_lista = [10, 20, 30, 40, 50]`
- acceder a un elemento especifico: `elemento = mi_lista[2]
- en Python podemos guardar diferentes tipos de valores en un misma lista.
- se expande de manera dinamica no se define el tamaño
- acceder a una porcion ejem:`` print (nomList [ 0 : 3 ]) ``accede al primer elemento hasta el segundo el tercero lo omite 
- Se pueden **anidar**, es decir, meter una dentro de la otra.
`



- ``nomList = [ elem1 , elem2 , elmen3  ... ]``
	- insertar elementos(posicion , valor)=> ``nomList.insert( 2, "Sandra" )``
	- insertar varios elementos => ``nomList.extend([ elem4 ,elem5 , elem6 ])``
	- insertar elementos al final de la lista=> ``nomList.append("Sandra")``
	- eliminar elemento=> ``nomList.remove("nomElemen")``
	- eliminar ultimo elemento=> ``nomList.pop()``
	- imprimir la lista completa => ``nomList[ : ]``
	- contar numero de elementos => `len(nomArreglo)`
otras funciones 
- unir o sumar 2 listas=> ``nomList3= nomList1+nomList2``
 - devuelve la  posición de un valor => ``nomList.index(" Jordan ")``
- Función in devuelve true o false si esta en la lista=> ``print("Jordan" in nomList)``
- Devuelve la cantidad de veces que el elemento aparece en la lista. => `nomLista.count(elemento)`
- ordena la lista de menor a mayor por defecto: nomList.sort()


casos de uso:

- recorrido en bucle`` for   in`` y el uso de la función `range()` ya que trabaja con la posición del arreglo  y no con el elemento como tal.  
```
numero = [10, 20, 30, 40] 
for pos in range(0, len(numero) - 1):
	print(pos, numero[pos])

```
range(inicio, fin  ) => se utiliza para generar una secuencia de números enteros. Es muy común en los bucles `for` 




---
# Tuplas

- Sintaxis - aqui usamos (  )  
	-  `nomList = (elemento1, elemento2,elemento3 ....) `
	- podemos omitir los paréntesis y seria una tupla también. 

- son listas inmutables, es decir , no se pueden modificar despues de su creacion. (no permite añadir , eliminar , mover elementos)
- si permiten busquedas con el INDEX y si podemos usar el in 
	- ``print("Jordan" in nomTupla)``
	- tambien podemos usar  Count para contar elementos que se repiten en la lista. 
- si permiten extraer porciones pero el resultado seria otra tupla o.0
- si permite comprobar si un elemento se encuentra en la tupla (menos mal :p)
- entonces para que sirve esta mierda?
	- son mas rapidas que las listas
	- menos espacio en memoria 
	- se pueden utilizar como claves en un diccionario (las listas no)
 

- se trabaja igual que los arreglos en sus posiciones. 
- se puede convertir una tupla en un arreglo `nomLista=List(nomTupla)`
- convertir un arreglo en una tupla `nomTupla=tuple(nomLista)`

- empaquetado de tupla : es solo poner los elementos en la tupla
	- ``miTupla=("Juan", 16,09,2024)``
- desempaquetado de tupla: guardamos en variables el contenido de la tupla
	- ``nombre, dia , mes , agno = miTupla``

---

# Diccionarios 

* son una estructura de datos 
- la principal caracteristicas de los diccionarios es que los datos se almacenan asociados a un tipo de relacion ==clave:valor== 
- los elementos no estan ordenados el orden no importa aqui.
- se puede almacenar cualquier tipo de dato es mas podemos almacenar  dentro del diccionario otro diccionario o incluso una tupla.

Sintaxis -  aqui se usa   {   }    
```
nomDiccionario = {"Alemania": "Berlin" , "Francia": "Paris" , "Ecuador": "Quito" , 29:"Jordan" , "Andrea":20000000}
print(  nomDiccionario["Ecuador"]  )
```
#nota me parece poco absurdo que se use los mismos { }  para imprimir un valor, ten en cuenta  que se usa [ ] 

- añadir elemento => `nomDiccionario["Peru"]="Cusco"` 
- modificar elemento=> `nomDiccionario["Peru"]="Puyo"`
- Eliminar elemento=> ``del nomDiccionario["Peru"]

#nota podríamos usar una tupla para asignar clave al diccionario. 
```
nomTupla=[1,2,3,4,5]
nomDiccionario= {nomTupla[0]: "Jordan" , nomTupla[1]:"Andrea" ,nomTupla[2]:"Liam" , nomTupla[3]:"Ranita" }
pint(nomDiccionario)

```
- ejemplo de un diccionario con una tupla 
```
# Diccionario con una tupla como valor
diccionario = {
    "nombre": "Juan",
    "edad": 28,
    "hobbies": ("leer", "futbol", "ajedrez")  # Este es el valor en forma de tupla
}

# Accediendo a la tupla
print(diccionario["hobbies"])  # Salida: ('leer', 'futbol', 'ajedrez')

# Accediendo al segundo elemento de la tupla
print(diccionario["hobbies"][1])  # Salida: futbol
```
- algunos métodos 
	- devuelva solo claves `nomDiccionario.key()`
	- devuelve solo los valores ``nomDiccionario.values()``
	- devuelve el tamaño del diccionario `len(nomDiccionario)`




