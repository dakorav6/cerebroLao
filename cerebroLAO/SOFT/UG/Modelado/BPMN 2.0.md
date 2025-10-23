 es un tipo de modelado orientado a los procesos de negocios
Business Process Model and Notation (Notacion para el modelado de proceso de negocio)

![[Pasted image 20240609100137.png]]


Elementos: 

1.- Piscinas y Carriles(Pools y Lanes) => representa las diferentes entidades involucradas en el proceso 
		Pools=> representa organizaciones / procesos  (Procesos => nombre + adjetivo ( gestion de pagos ) - minusculas)
		Lanes => representa roles o departamentos en una organizacion (quien va hacerlo)
		

2.-Eventos => nombre + participio ( Factura emitida ) - primera letra mayuscula 
- Marcan el inicio, la final o algun cambio importante durante el proceso.
- se representa por un circulo 

3.- Actividades =>verbo + nombre ( Aprobar orden) - primera letra mayúscula
- son las actividades 
- ![[Pasted image 20240609162549.png]]
4.-Pasos de Decisión (Gateway) => representa la toma de una decisión en el proceso. 
- **Decisión Exclusiva (XOR)**: ==Sólo una de las salidas== puede ser seguida.
	- Notoce que la tercer salida tiene una "/ " quiere decir que se aplica si las anteriores salidas no. 
	- ![[Pasted image 20240609155228.png]]
	- 
- **Decisión Paralela (AND)**: ==Todas las salidas== se siguen simultáneamente.
	- ![[Pasted image 20240609112131.png]]
	- Union en paralelo: Une dos o mas tareas 
	- ![[Pasted image 20240609112218.png]]
- Nodo Inclusivo => el flujo continua por ==todas las alternativas que cumplan la condición.==
	- ![[Pasted image 20240609155942.png]]
	- 


ejemplo










