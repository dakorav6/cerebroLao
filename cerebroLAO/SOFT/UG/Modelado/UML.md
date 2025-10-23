

### Diagrama de Clase en UML

- Visibilidad
	- (  -  ) privado
	- (  + ) publico
	- ( #  ) protegido 


Clase: 
![[Pasted image 20240608191618.png]]

### Relaciones 

- Multiplicidad 
	- (0..1)  cero a uno
	- (n) (cantidad especifica)
	- (0 .. * ) cero a muchos 
	- (1 .. * ) uno a muchos


### **Relaciones:**
- **Asociación:** Línea simple entre clases definiendo su Multiplicidad (Pueden ser unidireccional o bidireccional) 
- **Herencia (Generalización):** Línea con un triángulo en la punta.
- **Implementación:** Línea discontinua con un triángulo en la punta.
- **Agregación:** Línea con un rombo vacío.
- **Composición:** Línea con un rombo relleno.


### Herencia => relacion de padre a hijos 
![[Pasted image 20240608191715.png]]
![[Pasted image 20240608192656.png]]



## Agregación
Cada clase es independiente (osea que una puede existir sin la otra) ejemplo: una tortuga puede vivir en un Tortuguero pero si sale del Tortuguero sigue siento una tortuga. 
La posicion del rombo blanco o vacío  se coloca en el extremo de la relación que apunta hacia la clase que actúa como el contenedor.
![[Pasted image 20240608191859.png]]


## Composición
Hay una relacion de dependencia una clase no puede existir sin la otra 
Se representa po run rombo negro 
La posicion del rombo esta en la clase principal  o se coloca en la clase que actúa como el contenedor (la clase compuesta), y la línea se dirige hacia la clase que actúa como el contenido (la clase componente).
![[Pasted image 20240608193215.png]]


### Implementación

se refiere a la relación entre una interfaz y la clase
Se representa con una linea discontinua con una flacha que apunta a la interfaz. 
![[Pasted image 20240608195615.png]]

