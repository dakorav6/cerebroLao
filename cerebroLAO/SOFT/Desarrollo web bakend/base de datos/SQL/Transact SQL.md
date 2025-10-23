
[[COMANDOS SQL]]

---

- print 'hola mundo '
- concatenacion: print 'El nombre del empleado es: '+ @nombre;
- En formato tabla SELECT 'Hola mundo' AS NombreEncabezado; 
- dentro de un bloque de codigo no se usa los corchetes y al momento de programar en transaSQL visualmente puede ser caotico el desorden asi que aconseja usar BEGIN anidados ejemplo: conclusion con los BEGIN definimos bloques de ejecución. 
	- ![[Pasted image 20240709201059.png]]
- Update => actualizar 
- SET= > definir o inicializar o darle valor a
- if exists => si existe (condición )
- create proc  o create procedure => crear procedimiento almacenados  AS (como) BEGIN
- ejecutar procedimiento almacenado => EXEC  nomProcAlma


---
Operadores lógicos

AND=> SELECT * FROM TABLA WHERE condicion1 AND condición2;
OR=> SELECT * FROM TABLA WHERE condicion1 OR condición2;




---

- se usan para el manejo de transacciones (Transact se invento por que no esta bien visto manipular una base de datos borrando información  con algún script )
- son 4=> (Nota: el | es o es nuestra seña que indica uno | lo otro )
	- BEGIN TRAN=> indica el inicio de una transacción o inicio de operaciones.  
		- ==BEGIN TRAN|TRANSACTION== nombreTransaccion 
		
	- COMMIT TRAN=> guardar los cambios permanentemente en la base de datos. (no es reversible)
		- ==COMMIT TRAN|TRANSACTION== nomPuntoGuardadoDelSaveTran
		- ![[Pasted image 20240524105338.png]]
		- ![[Pasted image 20240602205736.png]]
		- 
	- ROLLBACK TRAN=>deshacer los cambios temporales (Sí, ejecutar `ROLLBACK` en una transacción cancela todas las operaciones realizadas desde el último `BEGIN TRANSACTION`. Esto significa que todos los cambios realizados después de `BEGIN TRANSACTION` se deshacen y la base de datos vuelve a su estado original antes de que la transacción comenzara.)
		- ==ROLLBACK TRAN|TRANSACTION== nomTransaccion|nomPuntoGuardado / o tambien puede ir vacio solo el ROLLBACK 
	- SAVE TRAN=>permite definir los puntos de guardado y estos permite anular una parte de la transaccion en curso. es posible definir varios puntos de guardado en una misma transaccion. SINTAXIS: ==SAVE TRAN | TRANSACTION==   nombrePuntoParada ;
	- ![[transacciones sql.png|800]]![[Pasted image 20240602211152.png|800]]
---

checkpint  :: fn_dblog?

----
Bulk insert  => almacena registro externos en la base de datos.
- se requiere crear la tabla con los encabezados antes de usar el Bulk insert 
- ==bulk insert==  nomTablaDestino ==from==  ´URLdondeTenemosGuardadoElArchivo´ (el archivo tiene que ser txt) (podemos pasar d excel a txt )(ojo con las comillas)
- 

---

### Condicionales

- if  ==exists== => si se cumple la condicion. ejem:
	- if exists (select * from articulos where cantidad=0) 
	- else select 'No hay nadaaa de nadaaaaaa d:'
	- 
-  if OBJECT_ID('nomTabla') is not null 
	- drop table nomTabla.
	- elimina la tabla si no esta nulo 
- NOTA: podemos restar y mostrar por ejemplo SELECT (CAPACIDAD-ENTRADAS) AS "DISPONIBILIDAD"
- nota: select 'Holiiii texto ' as resultado. 

---

Variables => se declaran en la seccion de declare en el bloque 

==declare==
@nomVariable  int ,
@nomVariable2  varchar(20) ,
@telefono  numeric(10);


==begin==...
==end==

notas:
- no existen variables globales solo son por bloque 


asignamos valor con el set
![[Pasted image 20240708215100.png]]
tambien se puede inicializar y delcarar ahi mismo
![[Pasted image 20240708215311.png]]

Buscar coincidencia de palabras => uso de la funcion like
![[Pasted image 20240708223346.png]]

---

variable de tipo table => son tablas del tipo variable con tablas momentáneas que seran usada para el bloque de codigo y despues sera eliminada cuando termina la ejecucion.  
declare 
	@tabla1 table (
		id int,
		nombre varchar(20),
		telefono numeric (10)
	)
	

---
