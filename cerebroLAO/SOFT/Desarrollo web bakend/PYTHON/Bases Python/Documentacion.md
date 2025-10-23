
La **documentación** es esencial en cualquier proyecto de Python para que otros (y tú mismo) puedan entender el código, mantenerlo y extenderlo fácilmente.


1. **Comentarios en el código**
Los comentarios ayudan a explicar pequeñas secciones de tu código que podrían no ser obvias para otros programadores (o para ti en el futuro).

2. **Docstrings**

Los **docstrings** son cadenas de texto que van al principio de módulos, clases y funciones para describir su comportamiento.

Formato básico:

- Los docstrings van encerrados entre comillas triples (`"""`) y se colocan justo debajo de la definición de una función, clase o módulo.
```
def sumar(a, b):
    """
    Suma dos números.

    Args:
        a (int): El primer número.
        b (int): El segundo número.

    Returns:
        int: La suma de los dos números.
    """
    return a + b
```

