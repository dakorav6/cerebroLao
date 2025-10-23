

---



Propiedades de Inicio de sección (pestaña de configuración: contraseña, y muchas cosas mas )
- Dentro de la carpeta de "seguridad" en el sector de carpetas y subcarpetas - doble clic a usuario que deseemos configurar o clic derecho propiedades. 
Denegar acceso e inicio de sección. 
- dentro de la misma ventana en la pestaña "Estado"


---

**Crear  inicio de sección  o conexión.** (LOGIN) (a nivel de servidor es esto)
- Clic derecho  carpeta de seguridad - crear nuevo inicio de sección (Esto es fuea de la carpeta BD)
- Transact 
	- ==CREATE LOGIN== Luis ==WITH PASSWORD== ='contraseña' , DEFAULT_DATABASE= nomBD ;
nota: cuando quieras ingresar el inicio de seccion de un login nueva te aparece un recaudro verdad? y te sale el ususario sas y solo ese. Resulta que si esperas que el programa te despliegue una lista de login estas equivocado tienes que escribir el nombre de usuario y contraseña en la primera vez  -.-  . Ya las proxima veces si sale 

- Crear usuario  asignar un LOGIN  
	- Un usuario de base de datos debe estar asociado a un login.
	- USE nombreDeLaBaseDeDatos;
	- ==CREATE USER== nomUser ==FOR LOGIN== nomLogin;

- **Crear usuario y asignar SCHEMA** 
	- Puedes asignar un esquema por defecto al usuario, pero no es obligatorio. Si no se especifica un esquema, el usuario utilizará el esquema `dbo` por defecto.
	- nota: la creacion de usuario se debe hacer en una BD especifico no en la BD master. (Cada usuario de base de datos está asociado a una base de datos específica.)
		- **WITH DEFAULT_SCHEMA**: asigna a un schema ya creado.  
	- ==CREATE USER== nomUser ==FOR LOGIN== nomLogin ==WITH DEFAULT_SCHEMA== = INV;


Nota: los usuario no tienen contraseña para eso esta lo LOGIN 

Asignar a un Login una BD 
	Fuera de la carpeta de BD - seguridad - inicios de session - escogemos el LOGIN (ejemlo:sa) - clic derecho propiedades - pestaña asignación de usuarios. 

---
### **Esquemas** => 
es un contenedor como una carpeta que almacena objetos de BD como tablas , vistas , procedimientos almacenados , funciones, indice y otros.

NOTA: La creación de los schemas se debe realizar en una BD especifica no en la master o general. Cada schemas pertenece a una base de datos especifico. 

- Características de los Esquemas: 
	-  Agrupación lógica de objetos de base de datos (tablas, vistas, procedimientos), básicamente organiza objetos.
	- si schema se parece a  Grupos de archivos  pero no es lo mismo.(los grupos de archivos son para gestión de almacenamiento distribuyendo un grupos de archivos para mejorar el rendimiento en diferentes discos por ejemplo)
	- puedes tener dos objetos con el mismo nombre en diferentes esquemas dentro de la misma base de datos sin que haya conflicto.
	-  Puedes otorgar permisos a un esquema completo en lugar de a objetos individuales, simplificando así la administración de la seguridad.(PERO PARA ESO ESTAN LOS ROLES)
	- Organización: Ayudan a organizar los objetos de la base de datos en categorías lógicas. Esto es especialmente útil en bases de datos grandes con muchos objetos, ya que facilita la administración y el mantenimiento.
	- pueder ver el esquema creado en el explorador dentro de la BD - seguridad-esquemas.
-

- ==CREATE SCHEMA== nomEsquema ==AUTHORIZATION==  dbo;  GO
	- dbo=> es un usuario especial en SQL Server que es el propietario de todas las bases de datos, el esta en todas las base de datos. 

- **Asignar Objetos (tablas) a un Schema o diferentes Schemas.** 
	- ==ALTER SCHEMA== nomEsquema ==TRANSFER==  dbo.nomTabla; 
		- nota: para llegar a la tabla usar la nomenclatura del punto. 
	- 


- Otorgar/denegar Privilegios a los Usuario/Esquemas en las tablas.
	Contexto: En SQL Server, los permisos deben otorgarse a usuarios o roles específicos, ya que los permisos por sí mismos no pueden existir sin estar asociados a un principal (usuario o rol).Por esto aqui usamos al usuario. :/ que mierda para eso uso roles. 
	- Privilegios son: SELECT, INSERT, UPDATE (modificar o actualizar) / DELETE para denegar
	- GRANT es otorgar / DENY es denegar 
	- ==GRANT SELECT , INSERT , UPDATE ON== SCHEMA::nomSchema ==TO== nomUsuario. 
	- ==DENY DELETE ON== SCHEMA::nomSchema ==TO== nomUsuario.

![[Pasted image 20240612112201.png]]

---
 
### - **Crear Roles** 
Los roles son los conjuntos de permisos. Estos conjuntos existen a tres niveles distintos: servidor - base de datos - aplicación. Los roles permiten agrupar los derechos y gestionar mas fácilmente los diferentes usuarios y las conexiones. 

- **`CREATE SERVER ROLE`**: Crea un rol a nivel de servidor. (Aplica a la instancia, solo a la instancia que se este trabajando no a las otras) (pueden abarcar múltiples bases de datos dentro de esa instancia.)(**Permisos**: Puedes asignar permisos que afectan a toda la instancia del servidor SQL, como permisos de administración de inicios de sesión, configuración del servidor, etc.)
- **`CREATE ROLE`**: Crea un rol a nivel de base de datos. (**Permisos**: Puedes asignar permisos específicos a estos roles en objetos dentro de la base de datos, como tablas, vistas, procedimientos almacenados, etc.)
- CREATE APPLICATION ROLE : crea roles para aplicaciones que se conecten a la BD


Crear Rol
	 a nivel de BD => ==CREATE ROLE== nomRol(FACTURACION); (NOS ENFOCAREMOS EN ESTE POR AHORA)
	a nivel de servidor => ==CREATE SERVER ROLE== nomRol; 
	Eliminar rol => DROP ROLE nombreDelRol;
	


- Añadir usuario al Role
	- a nivel de BD => ==ALTER ROLE ==nomRol(FACTURACION) ==ADD MEMBER==
		nomUsuarioLogin; 
	- A nivel de servidor => ==ALTER SERVER ROLE== nomRol(FACTURACION) ==ADD MEMBER==
	nomUsuarioLogin; 
	- Eliminar una Conexión a un rol => ==ALTER SERVER ROLE== nomROLServidor ==DROP MEMBER== nomUsuarioLogin ; 

OTORGAR PERMISOS 
- a nivel de base de datos(ON) : 
	- Permitir crear tablas => ==GRANT CREATE TABLE TO== nomRoyl;
	- Permitir crear vistas => ==GRANT CREATE VIEW TO== nomRol;
	- permitir conectar a la bd=> ==GRANT CONNECT TO== nomRol;
	- permitir Seleccionar datos de todas las tablas y vistas de la bd => ==GRANT SELECT TO== nomRol;
	- permitir Insertar datos en la tabla => ==GRANT INSERT TO== nomRoL;
	- permitir actualizar datos en las tablas y vistas de la bd => ==GRANT UPDATE TO== nomRol;
	- permitir eliminar datos de las tablas y vistas de la bd => ==GRANT DELETE TO ==nomRol;
	- Permite ejecutar procedimientos alamacenados y de funciones => ==GRANT EXECUTE TO== rolTSQL;
	- Permite modificar cualquier esquema de la bd => ==GRANT ALTER ANY SCHEMA TO==  rolTSQL;
	




- Roles Predefinidos(estas en todas las base de datos por defecto):
	- db_owner => es el equivalente a ser dueño amo y señor de la BD
	- db_accessadmin => permite añadir o eliminar usuario de la BD
	- db_datareader => permite consultar (SELECT )  en EL BD
	- db_datawriter => permite INSERT , UPDATE , DELETE para las tablas en la BD
	- db_ddladmin => permite CREATE . ALTER , DELETE para Objetos para BD
	- db_securityadmin =>  permite gestionar roles
	- db_backupoperaor => permite las copias de seguridad
	- db_denydatareader => prohibe visualizar los datos en la BD
	- db_denydatawriter => prohibe modificar datos en la BD

### Con ayuda del SSMS 
CREAR ROL
- en la parte de navegación -  escoge una BD - carpeta seguridad - roles - clic derecho añadir
- hay 3 pestañas en la general se coloca el nombre 
- en la pestaña elementos protegibles vamos a especificar que elementos vamos a trabajar con el boton BUSCAR - elementos específicos
- se abre una ventana mas y podemos escoger "Tipos de objetos " ejemplo: tablas y en la parte inferior especificar cuales son esos nombres de tablas. 
- una vez ya añadido los elementos (tabla) en la parte inferior hay un recuadro donde podremos CONCEDER  los permisos.(elemento por elemento)
OTORGAR ROL
- Creamos un inicio de sección o buscamos un Login ya creado  (recuerda que esto es fuera de la BD en seguridad) 
- una vez dentro de un login nos vamos  a la pestaña asignacion de ususarios 
- Escogemos la BD que queramos asignar y en la parte de abajo estara el rol reado 
- ![[Pasted image 20240605113747.png]]
- 



checar los roles (obtener informacion de los roles del servidor )
	EXEC sp_helpsvrole;  
	 EXEC sp_helpsrvrolemember 


### A nivel de aplicacion (hablamos de programas escrtprio, web , servicio de backend o cualquier otro programa que se conecte a a base de datos)

USE MiBaseDeDatos; 
	CREATE APPLICATION ROLE nomRolApp WITH PASSWORD = 'AppRolePassword'; 

oportar permisos al rol Aplicacion 
	GRANT SELECT, INSERT, UPDATE, DELETE ON SCHEMA::Sales TO SalesAppRole;





---

### - Configurar correo electrónico. 
	- en el explorador de objetos en la carpeta administración - correo electrónico de base de datos - clic derecho configurar correo- marcar opción administrar cuentas y perfiles de correo. - crear una nueva cuenta. 
		- ![[Pasted image 20240531110419.png]]
		- La contraseña tiene que ser la misma que la de tu correo 
		- - **Server name** (Nombre del servidor): `smtp.office365.com`
		- - **Port number** (Número de puerto): `587`

	- Enviar correo electrónico - simplemente clic derecho sobre correo electrónico de BD y enviar. 

### Tareas programadas (caso hipotético de que surja un error se enviar a un correo )

- Crear un operador 
	- en el explorador carpeta operador- Agente SQL - operador - clic Derecho nuevo operador 
- Configuración del agente SQL  ()
	- clic derecho en agente SQL - propiedades -  - avilitar perfil de correo - seleccionar correo - habilitar operador - seleccionar operador - habilitar notificar por correo 
- Programar una tarea programada 
	- Procedimiento almacenado? 
	- 


### En propiedades de un JOBS podemos usar -  NOTIFICACIONES por correo 
- en el explorador - clic en el trabajo creado - propiedades- notificaciones - enviar correo -si el trabajo a culminado o si no etcc...


### NOTA POSIBLE ERROR:  

En el explorador hay un "Agente SQL SERVER " tiene que estar activo . 
El Agente SQL Server es un servicio de Microsoft SQL Server que automatiza tareas de administración como la ejecución programada de trabajos (jobs), envío de alertas y notificaciones, y mantenimiento de bases de datos, mejorando la eficiencia y la gestión del servidor.


----
### Instancia de desarrollo 
Es basicamente volver al instalador SQL (No el ssms), y reinstalar el servidor te dara la opción de crear una nueva instancia. 





---
