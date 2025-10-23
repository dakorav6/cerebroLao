
---
[[teoría base SQL]]

ojo=> el taller es el examen así que pilas 

https://campusvirtual2.ug.edu.ec/altlogin/index.html

---


link de videos: https://ugye-my.sharepoint.com/personal/francisco_alvarezs_ug_edu_ec/_layouts/15/onedrive.aspx?ga=1&id=%2Fpersonal%2Ffrancisco%5Falvarezs%5Fug%5Fedu%5Fec%2FDocuments%2FCICLO%201%202024%20%2D%202025%2FBase%20de%20datos%20avanzada%2FUnidad%201%2FSemana%202


---
tabla de parametizacion 
	no se modifica 
tabla transaccional 
	se modifica siempre 


funciones 
	sumar=> sum(nomColumna) 
		ejemplo => SELECT SUM(nomColumn) FROM nomTabla
	agrupar por fecha cronologica => GROUP BY FECHA ORDER BY 1 
	![[Pasted image 20240530165314.png]]
		order by 1 hacer referencia a la primera columna osea que va a ordenar la primera columna si es 2 seria la segunda columna de la tabla que muestra al ejecutar el comando puedes poner el nombre de la columna tambien osea FECHA  tambien es valido .
	
calcular el promedio de ventas para un rango especifico de fechas 
calcular el promedio=> AVG
rango => aplicar fintro WHERE 
![[Pasted image 20240530170419.png]]
otra forma 
between (entre )
![[Pasted image 20240530170747.png]]

la fecha = como podemos ver esta la fecha como un solo numero en string 
otra forma:
	de la misma forma que esta en la tabla (otro formato de fecha y hora)
		funcion CONVERT 
				![[Pasted image 20240530171157.png]]
				el 121 es un formato de fecha y hora
conclusion: de la primera forma de string nos permite año mes y dia pero no fecha y hora 


minimo y maximo 
![[Pasted image 20240530172313.png]]

![[Pasted image 20240530173209.png]]


proyecto
primer parcial solo el modelo entidad relacion 
hasta el 4 solo quier ele modelo entidad relacion para el proyecto. 

---
![[Pasted image 20240531155604.png]]

---
- ORDER BY ? (ordenar por )
	CONTEXTO: seleccionar todo desde la tabla ordenandola por sueldo 
	SELECT * FROM empleado ORDER BY sueldo;



---
- el uso del IN 
	Contexto: actualizar sueldo de empleado en 950 donde el id del empleado sea (5,17,31)
	![[Pasted image 20240711185040.png]]
