
- son como los procedimientos almacenados pero se activan con un evento, una acción que desencadena algo 
- TRIGGERS es un objeto 
- siempre va estas asociado a una tabla, desencadenara una acción cuando ocurra algo en esa tabla 
- se usa en tablas o vistas
- se considera los triggers como guardianes de los datos en la BD cuando intentamos hacer una actilizacion , o borrado o modificacion podemos programar un triggers que se ejecutara de forma automática. 
- que puede ocurrir en una tabla? (cuando pase una de estas cosas se dispara el TRIGGERS)
	- Insertar registros (INSERT )
	- actualizar registro(UPDATE)
	- alminar registros (DELETE)
	
en que casos usar? 
en el supuesto caso de que los usuarios inserten registro en una tabla, podemos guardar esos registro de modificacion en otra tabla usando un disparador de eventos TRIGGERS que nos indique que usuario ingreso y cuando .
Copias de seguridad de registros modificados o que eliminemos 


**Tipos de Triggers**
- Triggers DML (Data Manipulation Language): Se activan en respuesta a eventos DML como INSERT, UPDATE o DELETE.
- Triggers DDL (Data Definition Language): Se activan en respuesta a eventos DDL como CREATE, ALTER, o DROP.
- Triggers de LOGON: Se activan en respuesta a eventos de inicio de sesión en el servidor SQL.


#nota puedes usar la sentecia `create or alter trigger` esto se puede usar en todos los objetos simplemente nos dice eso crea o altera un objeto.
#nota la nomeclatura para saber que es un triggers es `trg_nombreTrigger`


**Triggers para controlar la Inserción , actualización o eliminacion de datos(INSERT , UPDATE o DELETE).** 
contexto: creamos una tabla de control el cual vamos a registrar informacion sobre la alteracion de la tabla , en esta tabla controla vamos a registrar nombre usuario, date y que hizo , hasta ahora e visto que hacer un triger por cada accion (INSERT , UPDATE o DELETE)
```
-- Crear el trigger AFTER INSERT
CREATE TRIGGER trg_nomTrigeer ON nomTabla
AFTER INSERT /*UPDATE o DELETE en caso de ser actualizacion o eliminacion*/  
AS
BEGIN
	declare @usuario nvarchar(30);
	set @usuario = suser_name();
	INSERT INTO nomTablaControl VALUES(@usuario, getdate() , 'Insert :D' )
END;

```
- ALTER INSERT => va a monitorear cualquier insert en esta tabla  
- suser_name()=> funcion que devuelve el nombre de usuario 
- getdate() => devuelve la fecha y hora actual 
- nomTablaControl => tabla creada por nosotros mismos para guardar registro de modificación, en esta misma tabla podemos guardar todas las modificaciones 
- 


CREAR TRIGGER 
- ==CREATE TRIGGER== nomTrigger ==AFTER  INSERT ON== nomTabla ==FOR EACH ROW== 
- ==INSER INTO== nomTablaRegistro (nomColumn1, nomColumn2) ==VALUES==(NEW.nomColumn2 ,NEW.nomColumn2 , NOW() )
	- aqui se define si es AFTER o BEFORE 
	- la accion:  INSERT , UPDATE O DELETE  Tambien se puede poner ==FOR DDL_TABLE_EVENTS==  esto quiere decir que va a registrar todo(insert,update o delete)
		- 
	- podemos hacer que se genere un registro por el lote de datos ingresados o que genere un registro por cada dato ingresado. => (FOR EACH ROW - por cada fila ) o (FOR EACH STATEMENT - por cada sentencia)
	- ahora definimos cual es la tarea del triggers :
		- la funcion NOW() =captura el momento justo que se genera la accion para campos tipo fecha/hora
		- NEW =>el nuevo valor que se ingresa en caso de OLD=> seria para el valor que se esta dejando atras o cambiando. 
	


Los desencadenadores (triggers) en SQL Server pueden estar asociados tanto a tablas específicas como a la base de datos en su conjunto.
- - **Triggers de Tabla**: Estos se asocian a una tabla específica y se disparan en respuesta a eventos DML (Data Manipulation Language) como `INSERT`, `UPDATE` y `DELETE`.
    
- **Triggers de Base de Datos**: Estos se asocian a la base de datos en su conjunto y se disparan en respuesta a eventos DDL (Data Definition Language)  
- Los eventos DDL incluyen `CREATE`, `ALTER` y `DROP` 


-------------


### Tablas lógicas en triggers:
las tablas lógicas `inserted` y `deleted` en SQL Server se utilizan principalmente en los triggers para manejar las filas afectadas por las operaciones `INSERT`, `UPDATE`, y `DELETE`.(en caso de actualizacion de usan tanto la tabla lógica `inserted` como la tabla lógica `deleted`. )
1. **`inserted`**: Contiene una copia de las filas que se van a insertar en la tabla objetivo. Esta tabla está disponible en los triggers `AFTER INSERT` y `AFTER UPDATE`.No guarda historial a lo largo dle tiempo solo contiene los registros de la operacion actual. 
2. **`deleted`**: Contiene una copia de las filas que se van a eliminar de la tabla objetivo. Esta tabla está disponible en los triggers `AFTER DELETE` y `AFTER UPDATE`.No guarda historial a lo largo dle tiempo solo contiene los registros de la operacion actual. 

- Creacion de una tabla registro que me ingrese la fecha del registro y lo que registro en la tabla principal 

```
-- Crear el trigger para copiar registros a Libros_historial
CREATE TRIGGER trg_InsertarLibroHistorial
ON Libros
AFTER INSERT
AS
BEGIN
    INSERT INTO Libros_historial (ISBN, Titulo, NombreAutor, ApellidoAutor, Precio, FechaHoraInsercion)
    SELECT ISBN, Titulo, NombreAutor, ApellidoAutor, Precio, GETDATE()
    FROM inserted;
END;
```

Ejemplo triger con usuario y fecha y copia del registros
```
CREATE TRIGGER trg_registroLibros_historial ON LIBROS
AFTER INSERT
AS
BEGIN
	declare @usuario nvarchar(30);
	set @usuario = suser_name();
    INSERT INTO Libros_historial (Usuario , fechaHora , ISBN, Titulo, NombreAutor, ApellidoAutor, Precio)
    SELECT @usuario , GETDATE() ,  ISBN, Titulo, NombreAutor, ApellidoAutor, Precio
    FROM inserted;
END;
```

-----------
