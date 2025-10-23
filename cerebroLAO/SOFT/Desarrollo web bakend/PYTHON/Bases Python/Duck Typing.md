
**"Si camina como un pato y habla como un pato, entonces es un pato"**

- al usar **duck typing**, no se preocupa por las  herencia o relaciones de clase. Solo le importa si el objeto tiene los métodos que necesita. Esto hace que el código sea más flexible y menos rígido, pero al mismo tiempo introduce el riesgo de errores en tiempo de ejecución si el objeto no tiene los métodos adecuados.
-  En Python, **duck typing** se enfoca en **qué puede hacer un objeto** (sus métodos y comportamientos), en lugar de en **qué tipo de objeto es**.


Un Ejemplo de Duck Typing

```
class Cuadrado:
    def __init__(self, lado):
        self.lado = lado

    def area(self):
        return self.lado ** 2

class Circulo:
    def __init__(self, radio):
        self.radio = radio

    def area(self):
        return 3.1416 * self.radio ** 2

class Triangulo:
    def __init__(self, base, altura):
        self.base = base
        self.altura = altura

    def area(self):
        return (self.base * self.altura) / 2


```
 Duck typing en acción: a función **`imprimir_area(figura)`** no se preocupa de qué tipo exacto es **`figura`** (si es un cuadrado, un círculo o un triángulo). Solo le interesa que **`figura`** tenga un método llamado **`area()`**.
```
 def imprimir_area(figura):
    print(f"El área es: {figura.area()}")
```
Creamos diferentes figuras geométricas
```
cuadrado = Cuadrado(5)
circulo = Circulo(3)
triangulo = Triangulo(4, 7)
```
Llamamos a la función con diferentes tipos de figuras
```
imprimir_area(cuadrado) # Salida: El área es: 25 imprimir_area(circulo) # Salida: El área es: 28.2744 imprimir_area(triangulo) # Salida: El área es: 14.0
```

#ñota Otros lenguajes como Java no soporta el _duck typing_, pero se puede conseguir un comportamiento similar cuando los objetos comparten un interfaz (si existe herencia entre ellos). Este concepto relacionado es el polimorfismo.