
[[teoría base SQL]]
*****************
- INSTRUCCCIONES 
	- ==USE== nomBD; => selecciona o posiciona en una base de datos 
	- GO => se utiliza para dividir un script SQL en varios lotes. Un lote es un conjunto de instrucciones T-SQL 
		- Contecto de ejecucion: - Cada lote se ejecuta en su propio contexto. Por ejemplo, las variables declaradas en un lote no están disponibles en el siguiente lote. Esto puede ser útil para controlar el flujo de ejecución y manejar dependencias entre instrucciones.
		- ejemplo: ![[Pasted image 20240528223428.png|300]]
	- ==SELECT== => Selecciona las filas que queremos mostrar.
		- ==SELECT ... FROM== nomTablaUsar=> seleccionar y desde(FROM) que tabla usar. (siempre va al final) (usa la selección de punto para encontrar el archivo baseDatos.NombreTabla)
		- ==SELECT ... INTO== nomTablaNueva => selecciona y las inserta en una nueva tabla (Esta tabla puede ser temporal o persistente???)
		- ==INSERT INTO ... SELECT== =>Inserta en una tabla ya existente las filas de otra tabla. ejemplo: INSERT INTO table1 (col1, col2, col3, …) SELECT col1, col2, col3, … FROM table2
		- AS => (como) nos permite mostrar el encabezado con otro nombre EJEMPLO: SELECT  * AS otroNombre FROM unaTablaCualquiera
	-  INSERT INTO => Insertar columnas a una tabla ya existente. 
		- INSERT INTO tableName (Column1, Column 2....) VALUES (value1, value2, ...);
	
	
	
	- Count() => contar ejemplo: SELECT COUNT( * ) FROM nomTabla
	- * => es todos 
	

---


---

- **Crear BD**

![[Pasted image 20240611222919.png]]
	- (en la parte izquierda donde se encuentra todas las carpetas y subcarpetas), clic derecho en la carpeta BD y nueva BD
	- COMANDO=> ==create database== Prueba2;
		- En caso de querer parámetros específicos/ Archivos de datos  . mdf/ LOG ON es para archivo de diario. .ldf
			- ==CREATE DATABASE== nomBD  ==ON PRIMARY (==NAME= 'nombreBD' , FILENAME =URL o 'C:\Taller\nomBD.mdf' , SIZE = 6 MB , MAXSIZE= 20MB , FILEGROWTH= 1MB) 
			- LOG ON (NAME='nomBDDiario_log' , FILENAME=RUTA o "C:\Taller\nomBDdiario_log.ldf" , SIZE= 8MB , MAXSIZE= 15MB , FILEGROWTH= 10% ) ;GO
		- puede ser por defecto o configurar algunos parámetros a continuación
				- NAME=>nombre lógico
				- FILENAME=> ruta donde se guardara archivo BD (nombre físico)
				- SIZE=> tamaño inicial
				- MAXSIZE=>tamaño maximo
				- FILEGROWTH=>crecimiento  automático.  
	- **Eliminar** =>  COMANDO=> ==drop database== nombreBD  o (Clic derecho sobre la base de datos y eliminar )
	- Nota: en las dos formas de debe especificar nombre, ubicación, size.... 
	INTEGRACION DE UNA BASE DE DATOS???

```
CREATE DATABASE EXAMEN ON PRIMARY
(
NAME='EXAMEN',
FILENAME='C:\ExamenSegundoParcial\EXAMEN.mdf',
SIZE=10MB,
MAXSIZE=30MB,
FILEGROWTH=1MB
)LOG ON(
NAME='EXAMEN_log',
FILENAME='C:\ExamenSegundoParcial\EXAMEN_log.ldf',
SIZE=10MB,
MAXSIZE=20MB , 
FILEGROWTH=10%
);
```

---
# ALTER DATABASE 
 ### **GRUPOS DE ARCHIVOS**
- Es una colección de archivos(si es como una carpeta ) esto nos permite administrar y organizar datos como tablas , indices . vistas , procedimientos almacenados y otros objetos. 
- Esta coleccion de archivos no se visualiza en el ssms a menos que sea con comando para almacenar archivos como objetos (tablas , vistas, procedimientos) se recomienda usar Schema (mira abajo )
 - **Crear =>**  ==ALTER DATABASE== nomBD ==ADD  FILEGROUP==  NomGrupoArchivos ; 

- **Añadir archivos a un grupo de archivos ya existente (TO) =>** ==ALTER DATABASE== nomBD ==MODIFY FYLE== (NAME = 'nomArchivo'  , FILENAME = 'NuevaRuta\NombreDelArchivo.ndf') ==TO FILEGROUP== nomGrupoArchivo ; 

- **Eliminar un archivo en el Grupo de archivos =>** ==ALTER DATABASE== NombreDeLaBaseDeDatos ==REMOVE FILE== NombreDelArchivo;

- **Creación tabla y Guardado en un grupo de archivo (ON)=>**==CREATE TABLE== Usuarios ( ID INT PRIMARY KEY, Nombre NVARCHAR(50), Email NVARCHAR(100) ) ==ON== GrupoArchivosEjemplo;
- ![[Pasted image 20240524085224.png]]

Crear archivos de datos** (aun no se para que sirven estos archivos de datos que se crean aqui) => 
- 
- ![[Pasted image 20240603235515.png]]
	
	 - parámetros=> NAME es el nombre lógico?, filegorwnth es el factor de crecimiento automático? , SIZE es el tamaño inicial, MASIZE  es el tamaño máximo , `Ruta\NombreDelArchivo.ndf`: Es la ruta física y el nombre del archivo de datos que se creará en el sistema de archivos del servidor.
	ejemplo=>
	![[Pasted image 20240604005037.png]]

 SEGUNDA FORMA SSMS
	 - clic derecho en la base de datos - propiedades -archivos- agregar. 



como visualizar o en donde ver estos filegroup 
	


---




---
 (NO LO VA A EVALUAR)
SHINKDATABASE (Compactación o reducción del tamaño de archivo) 
- NOTA: se recomienda hacer una copia de seguridad antes de hacer una compactación de la base de datos  que se va a compactar y de la base de datos MASTER. 
	- la ejecución del comando no se aplica al instante, toma su tiempo.
- DBCC SHINKDATABASE=> no es posible bajar el tamaño ocupado por los datos??? 
- DBCC SHINKFILE=> permite reducir el tamaño de un archivo a un tamaño inferior 
	

- AUTO_CREATE_STATISTISC => auto creación de estadística  
- SP_HELPDB => averigua el conjunto de bases de datos que existen en el servidor 
- SP_SPACEUSED =>averigua el espacio de almacenamiento que ocupada BD


---


---

---



- **Comentar**
	- --ASI PONEMOS COMENTARIO
	
---



---
