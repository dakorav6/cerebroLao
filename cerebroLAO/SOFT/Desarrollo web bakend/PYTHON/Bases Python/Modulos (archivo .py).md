
- es un archivo con extencion .py puede contener variables,funciones, clases e incluso otros modulos. 
- para que sirve?, para organizar y reutilizar codigo (modularizacion y reutilizacion) 
- como crear modulo? tan sencillo como crear un archivo con extencion .py 

#  Paquetes (carpetas)

- **que son los paquetes?** directorio donde se almacenan módulos relacionados entre si. (ósea un grupo de módulos almacenados en una carpeta) 
- **para que sirven?**   para organizar y reutilizar código
- puedes tener un paquete dentro de otro
- 

### Como se crea
- es solo una carpeta pero en su interior debe de tener un archivo con este nombre `__init__.py` (Este archivo puede estar vacío, pero su presencia indica que la carpeta debe ser tratada como un paquete.)
### Acceder a un paquete

```
# en el from va las carpetas y subcarpetas hasta llegar a los modulos que queremos y import van los modulos. 

from mi_paquete.calculos.operacionesBasicas import matematicas, texto

resultado_suma = matematicas.suma(5, 3) 
resultado_resta = matematicas.resta(10, 4)


```
#nota como podemos apreciar el paquete operacionesBasias esta dentro de otros paquetes y modulo donde llamamos estos paquetes esta en la raiz o carpeta principal al inicio del todo 

### Otra forma de importar 
bueno esta opción mas elegante pero a mi parecer podria ser algo confusa si trabajamos con muchas clases pero es de igual de importante a tener en cuenta 
Aqui simplemente tenemos que poner en el from una ruta que se accede por puntos de los paquetes , subpaquetes y el modulo que quetemos importar  ejempplo:

tomando en cuenta el ejemplo anterior tenemos:

```
#from paquete.subpaquete.modulo import *
from mi_paquete.calculos.operacionesBasicas.matematicas from *

resultado_suma = suma(5, 3) 
resultado_resta = resta(10, 4)


```

---

# Paquetes distribuibles (hay que empaquetar el paquete)

(FALTA INFORMACION)
pasos:
1. Crear paquete 
2. instalar paquete

- Si tu objetivo es **crear herramientas reutilizables** o librerías para que otros usen o para facilitar el uso en tus propios proyectos, los paquetes distribuibles son muy útiles.
- Si solo estás trabajando en **aplicaciones concretas** y no necesitas compartir ni reutilizar el código, entonces no es necesario hacer un paquete distribuible.

---

