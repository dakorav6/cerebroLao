- sobrecarga de métodos no existe en Python
# clases 

Para establecer las propiedades (o atributos) de un objeto dentro de una clase, normalmente usas el método especial `__init__()` que vendría a ser el constructor . Aquí definiremos las  propiedades iniciales del objeto utilizando el parámetro `self`. 

```
class MiClase: 


	def __init__(self): 
		print("Creando objeto de MiClase")
		
objeto = MiClase() 
# Salida: Creando objeto de MiClase
```

# método constructor 

En otros lenguajes el nombre de la clase es el mismo que el del metodo constructor , en python no pasa esto se usa **`__init__`** 

- **`__init__`** es el **método constructor** especial que se ejecuta automáticamente cuando se crea un nuevo objeto de una clase. Su función es **inicializar los atributos** del objeto

# Objetos 
## ¿Qué es `self`?
- **`self`** es una referencia al **objeto actual** que está invocando el método.
- Es el primer parámetro en los métodos de instancia de una clase, y permite acceder a los **atributos** y **métodos** de ese objeto en particular.
```
class Persona: 
	def __init__(self, nombre, edad): 
		self.nombre = nombre 
		self.edad = edad 
		self.nota="solo se pone como paso de parametros lo valores que se pasan si inicializamos aqui una variable no hace falta ponerlo en paso de parametros, por ejemplo nota no iria"

	def saludar(self): print(f"Hola, soy{self.nombre} y tengo {self.edad} años.")
```

#nota Si no haces `self.nombre = nombre`, el valor de `nombre` no quedará guardado en la instancia del objeto. Por lo tanto, no podrás acceder a ese valor después de la creación del objeto.

#nota para trabajar con propiedades dentro de un metodo debemos de pasar como parámetro el self y asi poder acceder a las propiedades.  Osea que todos los metodos al nivel del objeto se van a pasar como parametro el `self` y en el cuerpo del metodo accederemos a cierta propiedad con la nomeclatura del punto  `self.nombreAtributo` 
ejemplo de metodos a nivel de objeto 


## Creación objetos 

Cuando creas una instancia de la clase `Persona`, `self` permite acceder y modificar los atributos (`nombre` y `edad`) **específicos de esa instancia**.

```
persona1 = Persona("Jordan", 28)
persona2 = Persona("Ana", 22)

# Llamar a los métodos
persona1.saludar()  # Salida: Hola, soy Jordan y tengo 28 años.
persona2.saludar()  # Salida: Hola, soy Ana y tengo 22 años.

```


# Métodos de clase  y variable de clase (requieren `cls` en lugar de `self`)

En lugar de operar sobre una **instancia** de la clase `self` , operan sobre la **clase** en sí misma. En lugar de usar `self`, usan **`cls`** como primer parámetro (una referencia a la clase en lugar del objeto).
- Requieren **`cls`** como primer parámetro, en lugar de `self`, y se declaran con el decorador `@classmethod`.
- las variables a nivel de clase solo se ponen fuera del método como esta en el próximo código de ejemplo. 


y para que me sirve esto?: 
- Cuando necesitas trabajar con **datos que pertenecen a la clase y no a una instancia en particular**.
- Por ejemplo, si tienes un contador de cuántas instancias de la clase se han creado, o si necesitas crear un método que afecte a todas las instancias de la clase.
- También es útil cuando tienes que crear **constructores alternativos** que crean objetos de una forma diferente a la del constructor principal (`__init__`).
```
class Persona:
    # Variable de clase (compartida por todas las instancias)
    num_personas = 0

    def __init__(self, nombre):
        self.nombre = nombre
	    # Incrementa el contador de la clase cada vez que se crea una instancia
        Persona.num_personas += 1

    # Método de clase que opera sobre la clase
    @classmethod
    def total_personas(cls):
        return f"Total de personas creadas: {cls.num_personas}"
```

# Métodos estáticos (staticmethod)

El método estático en Python, definido con el decorador `@staticmethod`, es un método que **no necesita acceso** ni a la instancia (`self`) ni a la clase (`cls`). Es decir, no depende ni de los atributos de la instancia ni de los de la clase.

Si es raro y es dificil para mi ahora encontrarle una utilidad pero solo ten la idea de que un metodo estatico no usa las funcionalidades ni propiedades de los objetos ni de la clase es un ser independiente de si mismo.  ejemplo: 

```
class Matematicas:
    @staticmethod
    def sumar(a, b):
        return a + b

    @staticmethod
    def restar(a, b):
        return a - b

```

Aquí tienes operaciones matemáticas agrupadas en la clase `Matematicas`. No es necesario que estas funciones accedan a algún atributo de la clase, pero su organización dentro de `Matematicas` hace que todo esté más claro.


# Encapsulamiento 


En Python, puedes aplicar encapsulamiento usando niveles de visibilidad:

1. **Público** (por defecto, sin guión bajo): son accesibles desde cualquier lugar
2. **Protegido** (un guión bajo, `_atributo`): no se usa
3. **Privado** (dos guiones bajos, `__atributo`):**no pueden ser accedidos directamente** desde fuera de la clase


# Getters y Setters

```
class Coche:
    def __init__(self, marca):
        self.__marca = marca  # Atributo privado

    def get_marca(self):  # Getter
        return self.__marca

    def set_marca(self, nueva_marca):  # Setter
        self.__marca = nueva_marca

coche = Coche("Toyota")
print(coche.get_marca())  # Acceso controlado a través del getter

coche.set_marca("Honda")  # Modificar el valor a través del setter
print(coche.get_marca())  # Ahora es "Honda"
```

También podemos encapsular métodos
- esto es util para usar metodos dentro de otros metodos que estan en la clase misma clase.

```
class Coche:
    def __encender_bateria(self):  # Método privado
        print("Batería encendida.")

    def __activar_sistema_electrico(self):  # Método privado
        print("Sistema eléctrico activado.")

    def arrancar(self):  # Método público que controla el flujo
        self.__encender_bateria()
        self.__activar_sistema_electrico()
        print("Coche encendido.")

coche = Coche()
coche.arrancar()  # Se accede solo al método público

```


# Herencia 

se da cuando una clase copia a otra clase, heredando sus propiedades y metodos para luego diferenciarse desarrollando sus propios metodos y funcionalidades usando como base la clase padre que heredo. (ejemplo: perro hereda de animal.)

```
# Definimos una clase padre
class Animal:
    pass

# Creamos una clase hija que hereda de la padre
class Perro(Animal):
    pass
```

## Uso de super()

La función `super()` nos permite acceder a los métodos de la clase padre desde una de sus hijas. Volvamos al ejemplo de `Animal` y `Perro`.

```
# Clase base (superclase)
class Vehiculo:
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo

    def arrancar(self):
        print(f"El {self.marca} {self.modelo} está arrancando.")

# Clase derivada (subclase)
class Coche(Vehiculo):
    def __init__(self, marca, modelo, color):
        # Llamamos al constructor de la clase base para reutilizar marca y modelo
        super().__init__(marca, modelo)
        self.color = color

    def tocar_claxon(self):
        print(f"El coche {self.marca} está tocando el claxon.")

# Crear una instancia de la subclase
mi_coche = Coche("Toyota", "Corolla", "Rojo")

# Usamos métodos de la clase base y subclase
mi_coche.arrancar()  # Método heredado de la clase Vehiculo
mi_coche.tocar_claxon()  # Método propio de la clase Coche

```

Uso de isinstance()
## Herencia múltiple 

Python permite que una clase herede de más de una clase, lo que se conoce como **herencia múltiple**. Sin embargo, hay que tener cuidado con ella, ya que puede llevar a situaciones complicadas. Aquí un ejemplo simple:
```
class Vehiculo:
    def moverse(self):
        print("El vehículo se está moviendo.")

class Avion:
    def volar(self):
        print("El avión está volando.")

class Avioneta(Vehiculo, Avion):
    pass

mi_avioneta = Avioneta()
mi_avioneta.moverse()  # Hereda el método de Vehiculo
mi_avioneta.volar()  # Hereda el método de Avion

```
#nota un posible problema que se nos puede presentar en la herencia multiple es que al momento de crear un objeto con la clase que hereda de 2 padres, tendremos que lidiar con la existencia de 2 constructores, y aqui nace la pregunta, que chucha hacer?
pues eso es sencillo de contestar, esto depende de quien esta primero 
- ``class Avioneta(Vehiculo, Avion)`` en este ejemplo tenemos primero Vehiculo, entonces se le va a otorgar prioridad al constructor Vehículo, ese es el que sera aplicado.  


## Sobrescrita de métodos
Las subclases pueden sobrescribir los métodos de la superclase si necesitan un comportamiento diferente. Veamos cómo hacer eso:

sobreescribiendo completamente el metodo:  solo ponemos el mismo nombre y lo que queremos que haga, lo mas comun es que si queremos usar la funcionalidad del padre y añadir algo mas, solo copiamos y pegamos el codigo al hijo para despues poner ese agregado.

```
class Vehiculo:
    def arrancar(self):
        print("El vehículo está arrancando.")

class Coche(Vehiculo):
    def arrancar(self):
        print("El coche está arrancando.")

# Crear una instancia de la subclase
mi_coche = Coche()
mi_coche.arrancar()  # Sobrescribe el método de Vehiculo

```

# Polimorfismo 

[[Duck Typing]] 



