- La **programación orientada a objetos** (POO) es un paradigma de programación que organiza el software en torno a "objetos".
- 
- Un objeto es una instancia de una clase, y contiene atributos (datos o variables) y métodos (funciones) que definen su comportamiento.

- Creacion de un objeto a partir de una clase 
	- nomClase nomObjec = new nomClase(); 

- para acceder a propiedades o metodos usar nomeclatura del punto 

# definición de términos 

- clase : Una clase es una plantilla o molde para crear objetos. Define los atributos y métodos que los objetos de esa clase tendrán.
- **Objetos**: Un objeto es una instancia de una clase, y contiene atributos (datos o variables) y métodos (funciones) que definen su comportamiento.
- Instancia: es un objeto que nace a partir de una clase. 
- popularización : esta compuestos por partes o modulos , estas partes permite reutilizarse y si un modulo o parte de daña o no funciona, esto no afecta a los demas modulos. 
- nomenclatura del puno: con esto podemos acceder a propiedades o funcionalidades del objeto

# Principios de la Programación Orientada a Objetos (OOP)

1. **Encapsulamiento**: Las clases oculta los  datos y comportamiento para proteger y evitar la alteración de estos para que no puedan ser accedidos o modificados directamente desde fuera de la clase. Para poder acceder a funcionalidades o características de un objeto se debe funciones o métodos específicos.  
    
2. **Herencia**: Las clases pueden heredar características de otras clases. Esto permite la reutilización de código y la creación de jerarquías.
    
3. **Polimorfismo**: Permite que las clases tengan diferentes implementaciones de los mismos métodos o propiedades.
    
4. **Abstracción**: Facilita la creación de interfaces y clases abstractas que definen comportamiento sin implementarlo completamente.




---
### Encapsulación 

La encapsulación describe la capacidad de un objeto para ocultar sus datos y métodos del resto del mundo.
Es importante que exista modularidad entre las clases ósea que se respete que cada clase tenga lo suyo y que no pueda alterarse desde otra clase, que cada clase sea independiente de si y que si desea alterar algún parámetro sea la misma clase que del parámetro que la modifique.

¿Como encapsulamos? Con los modificadores de acceso como el  prívate en las propiedades.

Y solo podamos acceder a ellos mediante los métodos.

Por que lo hacemos? Para que no aya una violación de datos.

Para eso usamos un método para hacer el llamado correspondiente desde la clase usando el método getter y setters.
- private int edad; 
- public void setEdad(int edad){   codigo } => modificar 
- public int getEdad(){   codigo  return edad ; }=> obtener valor
nota: estos metodos solo sirven para modificar y obtener a lo mucho podemos verificar datos. 


----

Constructores 

- Tambien son metodos de cierta forma 
- tienen el mismo nombre de la clase 
- nos permite dar un estado inicial al objeto (inicializar al objeto)=> eso significa darle valor a los atributos 
2 tipos de constructores:
1.- por defecto=>  Java lo crea por defecto a partir de las clases para poder instanciar el objeto. Después del new es la llamada al constructor de la clase:
ejemplo: nomClase nomObjec = new nomClase(); aqui con el new estamos llamando al constructor por defecto. 

2.-parametrisado=> podemos tener varios contructores por sobrecarga de metodo 

nota: recuerda que el this. hace referencia a la misma clase, asi que si todos los parametros que se refieren dentro del constructor van con this.
![[Pasted image 20240622212522.png]]

Nota: si tenemos constructores parametrizado tenemos que poner un constructor por defecto por que java ya no lo va  a poder de manera automática por que ya estamos trabajando con un parametrizado. en caso de requerir uno sin parametros. 


----

### Caso: Creación y Uso de Objetos
Contexto: mi profesor en un programa creo una clase global y dentro de esa clase creo todos los objetos como  estáticos, para poder usarlos en todo el programa como variables estáticas globales. me surge la duda de saber si asi se hace? 
![[Pasted image 20240802103002.png]]

**que dicen las buenas practicas?** 
Existen 2 enfoques_
- Creación Bajo Demanda: Este enfoque sigue el principio de crear instancias de clases solo cuando sea necesario. La mejor práctica es instanciar objetos de las clases a medida que se necesitan, siguiendo principios como la inyección de dependencias y manteniendo las responsabilidades claramente definidas.
```
public class Program
{
    static void Main(string[] args)
    {
        RegionAlmacen regionAlmacen = new RegionAlmacen();
        ProvinciaAlmacen provinciaAlmacen = new ProvinciaAlmacen();

        // Usa los objetos según sea necesario
        regionAlmacen.SomeMethod();
        provinciaAlmacen.SomeMethod();
    }
}

```
- Uso de una Clase Global (no recomendado para todos los casos): Tu docente utilizó una clase global con objetos estáticos. Este enfoque puede ser útil en ciertos casos, como configuraciones compartidas o acceso a datos globales. Sin embargo, no es una práctica recomendada para todo, ya que puede violar el principio de encapsulamiento y hacer que el código sea menos mantenible.








---



