

### Restauración de base de datos
nota: cuando dice restaurar esto aplica para restaurar y añadir una BD nueva.  tampoco quiere decir que vamos a restaurar todo el sistema solo vamos a modificar o añadir una bd en especifico . 


Con ayuda del SSMS

Con el archivo  (.BAK)(el .bak es para restaurar o añadir una bd)
	Si ya tienes un archivo de copia de seguridad (`.bak`) de la base de datos , puedes restaurarlo siguiendo estos pasos:
	1. clic derecho a la carpeta de base de datos (si a la carpeta no a un bd)
	2. restaurar base de datos 
	3. Selecciona "Dispositivo" y luego "Agregar" para buscar y seleccionar tu archivo de copia de seguridad.
	4. Haz clic en "Aceptar" para iniciar la restauración de la base de datos GESCOM

Con el archivo (.SQL) (el .sql solo es un archivo script no sirve para restaurar)
	- Abre el archivo SQL (`script.sql`) que contiene el script de creación de la base de datos GESCOM.
	- Selecciona y ejecuta el script para crear la base de datos y los objetos en ella.



- Notas:
	- en archivo de programas /Microsoft SQL / MSSQL16.MSSQLSERVER hay una carpeta de backup donde esta el archivo para restaurar la BD en caso de que queramos pegar una BD de otra fuente la pegamos aqui. 
	- En el mismo lugar MSSQL donde esta la carpeta backup tambien tenemos DATA donde van los archivos .mdf (archivos de datos)y la carpeta Log donde van los archivos ldf (archivo de diario)

### Restauración por código: 

```
RESTORE DATABASE PlantAndHealth
FROM DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL16.MSSQLSERVER\MSSQL\Backup\PlantAndHealth.bak'
WITH MOVE 'PlantAndHealth' TO 'C:\Program Files\Microsoft SQL Server\MSSQL16.MSSQLSERVER\MSSQL\DATA\PlantAndHealth.mdf',
MOVE 'PlantAndHealth_Log' TO 'C:\Program Files\Microsoft SQL Server\MSSQL16.MSSQLSERVER\MSSQL\Log\PlantAndHealth_Log.ldf',
REPLACE;
```

==RESTORE DATABASE== nombreArchivoBackup( .bak) ,
==FROM DISK== =  ' C:\Program Files\Microsoft SQL Server \MSSQL16.MSSQLSERVER\MSSQL\Backup\AdventureWorks2022.bak' (RUTA del archivo BACKUP)
==WITH MOVE==  'AdventureWorks2022' (nombre Archivo Backup que vamos a mover  )
==TO==  C:\Program Files\Microsoft SQL Server\MSSQL16.MSSQLSERVER\MSSQL\DATA\ AdventureWorks2022.mdf    ,
==MOVE== 'AdventureWorks2022_Log' ==TO== 'C:\Program Files\Microsoft SQL Server\MSSQL16.MSSQLSERVER\MSSQL\Log\AdventureWorks2022_Log.ldf'
==, REPLACE==; 
![[Pasted image 20240611233130.png|600]]

Explicación:
RESTORE DATABASE => Indicamos nombre de la BD a restaurar
FROM DISK =ruta de la carpeta Backup en el sistema 
WITH MOVE 'MiBaseDeDatos_Data' TO (aqui va la ruta de la carpeta data)  
WITH MOVE 'MiBaseDeDatos_Log'(ni busques ese archivo solo ponle_Log al nombre de la bg) TO ( aqui va la ruta de la carpeta LOG ) 
Replace;


posible error : Error de sistema operativo 5(Acceso denegado.). => esto puedo ocurrir por que estas en una instancia donde no tienes permisos en las carpetas de windows y estan como solo lectura 


### Como crear un respaldo 

![[Pasted image 20240615151143.png]]
```
BACKUP DATABASE PlantAndHealth TO DISK ='C:\ExamenPrimeParcial\Backup\PlantAndHealth.bak'
WITH NOFORMAT, NOINIT,
	NAME = 'JORDAN ORBE - PlantAndHealth';
```

==BACKUP DATABASE== nomBD  ==TO DISK = '==C:\Backups\MiBaseDeDatos.bak'
WITH FORMAT,
MEDIANAME = 'SQLServerBackups', NAME = 'Full Backup of MiBaseDeDatos';
- - **`TO DISK`**: Especifica el archivo de destino para el respaldo.
- **`WITH FORMAT`**: Formatea el medio de respaldo, sobrescribiendo cualquier dato existente en el archivo de respaldo especificado.
- **`NAME`**: Proporciona una descripción legible del respaldo.

### Como crear un respaldo en un dispositivo de seguridad 

BACKUP DATABASE [NombreDeLaBaseDeDatos] ==TO== UAL(cual es el nombre del dispositivo creado por nosotros)
WITH NOFORMAT, NOINIT,
	NAME = 'Full Backup of NombreDeLaBaseDeDatos', 
	
nota: `WITH NOFORMAT, NOINIT`: Estas opciones indican que no se formatee el medio de respaldo y no se inicialice (es decir, no sobrescriba los respaldos existentes en el dispositivo).


Respaldo Diferencial 
BACKUP DATABASE GESCOM TO UAL WITH DIFFERENTIAL, NAME = 'Differential Backup of GESCOM'; 

Respaldo transacciones diarias 
BACKUP LOG GESCOM TO UAL WITH NAME = 'Respaldo transaccional GESCOM programacion';



---

### Dispositivo de copia de seguridad 

es un contenedor que almacena copias de seguridad (un archivo en un disco )
- Crear un dispositivo de copia de seguridad
	- ==EXEC sp_addumpdevice 'disk',== 'UAL', 'C:\Path\To\Backup\UAL.bak';
		- - `sp_addumpdevice`: Es el procedimiento almacenado de SQL Server para añadir un dispositivo de copia de seguridad.
		- `'disk'`: Indica que el dispositivo de copia de seguridad es un archivo en disco.
		- `'UAL'`: Es el nombre del dispositivo de copia de seguridad.
		- `'C:\Path\To\Backup\UAL.bak'`: Es la ruta y el nombre del archivo físico donde se almacenarán las copias de seguridad. Debes reemplazar esta ruta con una ruta válida en tu sistema.




---




