Existen varias formas de hacer la conexión desde el mismo visual estudio en una clase se puede configurar todos los parámetros pero dice el profesor que es mas pro hacerlo desde un archivo de configuración(App.config). y mas pro aun seria usar encriptamiento de conexion a la base de datos pero eso es mas avanzado quedando para mas adelante


### Método Archivo de configuración (App.config) 

PRIMER PASO: Creación del App.config (Desde el visual Estudio):**
1. nos vamos al explorador donde estan las carpetas y subcarpetas 
2. clic derecho - agregar - nuevo elemento - archivo de configuración de la aplicacion
3. lo creamos como App.config

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

	<connectionStrings>
			<add name="PlantAndHealthDB" connectionString="Server=ENTERPRISE/DESARROLLO;
			Database=PlantAndHealth;User Id=sa;Password=P2ssw0rd;" providerName="System.Data.SqlClient" />
	</connectionStrings>
	
</configuration>
```

Parámetros:
- `<add>`: Añade una nueva cadena de conexión.
- `name`: El nombre que usarás para referenciar esta cadena de conexión en tu código (`"PlantAndHealthDB"` en este caso), ósea puedes poner cualquier nombre. 
- `connectionString`: La cadena de conexión en sí.
	- ![[Pasted image 20240712103546.png]]
	- Server= indica el nombre del servidor en este caso DESKTOP-FT13VMH
	- Database=nombre de la base de datos a usar
	- User ID= nombre de inicio de session 
	- Password= contraseña de ese inicio de session
	- 
- `providerName`: El proveedor de datos. En este caso, `System.Data.SqlClient` para SQL Server.
	- otros proveedores de BD
		-  **MySQL**: `MySql.Data.MySqlClient`
		- **Oracle**: `Oracle.DataAccess.Client`
		- **SQLite**: `System.Data.SQLite`


**SEGUNDO PASO: establecer clase para ejecutar la conexión**
1. Creamos una clase para ejecutar la conexion
2. ponemos la cadena de conexión y el metodo para la conexion 

```
  public static class ConectBD /*Esta es la clase que creamos para la conexion el nombre varia segun nuestro criterio*/
  { 
  
	/*CADENA DE CONEXION*/
      private static string connectionString = ConfigurationManager.ConnectionStrings["PlantAndHealthDB"].ConnectionString;
      
	/*METODO DE CONEXION*/
      public static SqlConnection GetConnection()
      {
      return new SqlConnection(connectionString);
      }
  }
```

#nota es importante tener habilitado en la cabecera de la clase para la conexión:(se habilita dando clic derecho a la carpeta del programa en el explorador- agregar-referencias-system.configuration)
- using System.Configuration;
- using System.Data.SqlClient;


**TERCER PASO: Creacion de un metodo dentro de la clase  para ingreso de datos usando un procedimiento Almacenado.**

![[Pasted image 20240713134640.png]]

- Conexión a la base de datos { Crear objeto comando  }
```
using (SqlConnection nombreConexionCualquiera = nombreDeLaClaseDondeEstaConexion.GetConnection()) 
{
using (SqlCommand nombreObjetoComandoCualquiera = new SqlCommand("nomProcedimientoAlma", nombreConexionCualquieraqueYaCreamos)) 
{
/* AQUI VA LO DE ABAJO SOBRE EL OBJETO COMANDO */
}
}

```

- Se especifica que el objeto comando es un procedimiento almacenado y abrir conexión:
```
nomObjComando.CommandType = CommandType.StoredProcedure;
nomConexion.Open();
```

En este punto se bifurcan 2 caminos: AÑADIR O OBTENER una variable de la base de datos.

### PRIMER CAMINO: añadir o registrar - ExecuteNonQuery()`

 añadir parametros o valores:
```
nomObjComando.Parameters.AddWithValue("@Nombre",Estudiante.Nombre)

```
Parametros:
-  @Nombre=> sabemos que es una variable del SQL 
- Estudiante.Nombre=> es un objeto de la clase Estudiante con su parametro.


**`ExecuteNonQuery()`**: 
se usa aquí porque  no devuelve filas de datos, sino que ejecuta una operación que afecta la base de datos (como `INSERT`, `UPDATE` o `DELETE`). 

```
nomObjComando.ExecuteNonQuery();
```
En resumen:
- Usas `ExecuteReader()` cuando esperas que el procedimiento almacenado devuelva filas de datos que necesitas leer y procesar.
- Usas `ExecuteNonQuery()` cuando el procedimiento almacenado realiza una acción (como una inserción, actualización o eliminación) y no necesitas recuperar filas de datos.

#Nota La conexión a la base de datos se cierra automáticamente al finalizar el bloque `using`. El bloque `using` garantiza que los recursos se liberen correctamente, incluso si ocurre una excepción
#nota en el codigo del programa osea en la parte del fontend no usemos comando de transaq eso el profesor lo ve "antihigenico", debemos manejarnos con procedimientos almacenados. 

### **SEGUNDO CAMINO: Obtener o Leer (Se usa un tercer using... o.0)- ExecuteReader()` 

- - Se ejecuta el comando y se obtiene un `SqlDataReader` para leer los datos devueltos por el procedimiento almacenado.(contexto : si estas en la misma clase por qu estos metodos van en la misma clase ) 
![[Pasted image 20240713140121.png]]
falta el return regiones; 
![[Pasted image 20240803184653.png]]

- `ExecuteReader` se utiliza principalmente para leer conjuntos de resultados devueltos por una instrucción `SELECT` dentro de un procedimiento almacenado.
```
using (SqlDataReader reader = cmd.ExecuteReader()) {

}

```

- ``reader.Read()``=> El método `reader.Read()` de la clase `SqlDataReader` se utiliza para avanzar el lector a la siguiente fila de un conjunto de resultados. Devuelve un valor booleano que indica si hay más filas disponibles para leer. Devuelve false si no hay mas filas. 
- 
**Conversiones de datos** 
- Cuando accedes a los datos de una columna usando `reader["ColumnName"]` en `SqlDataReader`, el tipo de dato devuelto es `object`. Esto significa que `reader["ColumnName"]` devuelve un valor genérico que puede ser convertido al tipo de dato apropiado basado en la estructura de la base de datos.
- conversiones de datos:
	// Convertir string
    string nombre = reader["NOMBRE"].ToString();
    
    // Convertir int
    int id = Convert.ToInt32(reader["ID"]);
    
    // Convertir double
    double precio = Convert.ToDouble(reader["PRECIO"]);
    
    // Convertir decimal
    decimal costo = Convert.ToDecimal(reader["COSTO"]);
    
    // Convertir bool
    bool esActivo = Convert.ToBoolean(reader["ES_ACTIVO"]);
    
    // Convertir DateTime
    DateTime fecha = Convert.ToDateTime(reader["FECHA"]);
	
	// Convertir CHAR 
	char inicial = reader["INICIAL"].ToString()[0]; // Aquí asumimos que INICIAL es de tipo CHAR(1) en la base de datos




**Como seria el procedimiento almacenado para obtener regiones?**
```
CREATE PROCEDURE spObtenerRegiones
AS
BEGIN
    -- Selecciona todas las regiones de la tabla Regiones
    SELECT REGION_ID, REGION
    FROM Regiones;
END;

```



### **En caso de que un procedimiento almacenado tenga salida de datos (OUTPUT)**

SQL PROC ALMA:
```
CREATE PROCEDURE spObtenerValorSalida
    @InputParam INT,
    @OutputParam INT OUTPUT
AS
BEGIN
    -- Alguna lógica para calcular el valor de salida
    SET @OutputParam = @InputParam * 2
END

```
NO TENGO PUTA IDEA PREGUNTE AL PROFE, por que segun chat gpt tienes que declarando un parametro de sql dentro del bloque de codigo c# 



---
