
- Tipos de datos 
	- int => entero 
	- float (n) => decimales 
	- nvarchar(n) => cadena 
	- date => fecha 

---
Gestión de tablas con ayuda del SSMS

**Creación de tabla**
1. En el explorador de objetos expande el nodo de la base de datos en la que queremos trabajar - clic derecho en tabla - nueva tabla- se abre una pestaña donde podemos definir nombre de columna y tipo de dato.
2. También podemos establecer la llave primaria con clic derecho 
3. Una vez terminado guardamos con Control+s, aquí definiremos el nombre de la tabla. 
nota: podemos volver a modificar estos parametros dandole clic derecho a la tabla ya creada en el explorador de objetos -  Diseño

**Diseñador de Relaciones:** 
Dentro de la pestaña Diseño (clic derecho a la tabla - diseño), clic derecho en cualquier lugar del area de diseño  selecciona: Relationships o Relaciones. (se abre una ventana)
1. damos clic en Añadir o agregar 
2. en Especificacion de la tabla y columna le damos clic a  ... 
3. Tables and Columns Specification: Haz clic en los puntos suspensivos `...` para seleccionar la tabla y las columnas involucradas.
	1. **Primary Key Table:** Selecciona la tabla y columna que actúa como clave primaria.
	2. **Foreign Key Table:** Selecciona la tabla y columna que actúa como clave foránea.

**Ingreso de datos:**
1. Clic derecho en la tabla en el explorador de objetos y selecciona: Edit Top 200 Rows
2. Se abrirá una ventana con las primeras 200 filas de la tabla (puede estar vacía si es nueva).
3.  Ingresa los datos directamente en las filas en blanco.Cada vez que ingresas un nuevo valor en una columna y te mueves a la siguiente, SSMS guarda el dato automáticamente.


---



- **Crear tabla**
	1. Dentro de la BD hay una carpeta "tabla"
	2. clic derecho en tabla - nuevo - tabla 
	3. **Eliminar** => clic derecho sobre tabla -eliminar
	4. COMANDO=>==CREATE TABLE== NOMBRETABLA( --aquí se declara las variables que irían en el encabezado )
	5. ![[ejemplo creacion de tabla.png]]
	6. **Eliminar**=> ==DROP TABLE== nomtabla
	7. 
---

### Modificar Tabla
ALTER TABLE nomTabla
- Agregar una nueva Columna a una tabla  => ALTER TABLE   nomTabla ==ADD== edad int DEFAULT (valor que queramos añadir a la columna);
	- ejemplo: ALTER TABLE numeros ADD numerosPares int DEFAULT 2; 
- Modificar tipo de datos Column=>ALTER COLUMN nombreColumna nuevoTipoDato ;
- Eliminar Column => DROP COLUMN nomColumn;
- Agregar Restricciones => ADD CONSTRAINT nombreClavePrimaria PRIMARY KEY (nombreColumna);
- FOREIGN KEY => ALTER TABLE nomTabla ADD CONSTRAINT nombreClaveForanea FOREIGN KEY (nombreColumna) REFERENCES otraTabla(nombreColumna);
---
CRUD
Modificar/Actualizar valores de una tabla    

(UPDATE)
```
UPDATE nombre_tabla 
SET columna1 = valor1, columna2 = valor2, ... 
WHERE condicion;
```
Eliminar
```
DELETE FROM nomTabla
WHERE nomColumn = @variable;
```
Leer
```
SELECT * FROM nomTabla;
```
Crear
```
INSERT INTO nomTabla (NOMBRE_SUCURSAL, COMUNA_ID)
VALUES (@NOMBRE_SUCURSAL, @COMUNA_ID);
```


---

### Creación de una Columna con un campo  autoincremental: 

ID INT IDENTITY(1,1) NOT NULL PRIMARY KEY, ==> El campo ID comenzará en 1 y se incrementará en 1 para cada fila nueva Nombre NVARCHAR(100) ); 
![[Pasted image 20240615112817.png]]
IDENTITY(100,10): La columna de identidad comenzará en 100 y se incrementará en 10 para cada nueva fila.

 #Como **podemos saber si una tabla existente tiene un autoincreimental identity?**
1. clic derecho sobre tabla que queramos revisar en el explorador  - diseño
2. en la parte inferior sale la información busca la que dice "Especificación de identidad"

### Modificar una tabla añadiendo una columna autoincremental 

```
ALTER TABLE nomTabla ADD nomNuevaColumn INT IDENTITY(1,1) NOT NULL PRIMARY KEY;
```


---

Valor predefinido 
cuando creas una tabla y te indican que una columna debe tener como valor predefinido 1
```
CREATE TABLE CLIENTES
(
ESTADO BIT NOT NULL DEFAULT 1
)
```





---

### Restricciones o CONSTRAINT
utiliza para garantizar la integridad y la exactitud de los datos dentro de la tabla.

- Tipos de Constraints y Sus Usos
	- PRIMARY KEY=>valor unico, no repetitivo
		- nota: solo puede haber 1 primary key por tabla
		- no permite valores nulos
	- FOREIGN KEY=>valor único en 2 tablas con sus respectivas columnas 
		- ![[Pasted image 20240601130018.png|500]]
	- UNIQUE=>garantiza que los valores en la columna o conbinacion de columnas sean unicas 
		- nota:Puede haber múltiples constraints `UNIQUE` en una tabla.
		- permite valores nulos
	- CHECK => validar que los datos de una columna cumplan con una condición especifica .
		- ![[Pasted image 20240601141922.png]]
	- NOT NULL=> asegura que los valores de la columna no tenga valores nulos. 

---
### INGRESAR VALORES A LA TABLA  (INSERT INTO)
![[Pasted image 20240602215853.png]]
Insertar múltiples Filas 
![[Pasted image 20240602215930.png]]

### INGREAR VALORES A PARTIR DE OTRA TABLA (INSERT INTO ... SELECT)
La instrucción `INSERT INTO ... SELECT` es una herramienta poderosa para copiar datos de una tabla a otra, permitiendo agregaciones, transformaciones y filtrado de datos en el proceso. Esta técnica es fundamental para tareas de migración de datos, creación de reportes y preparación de datos para análisis.

```
INSERT INTO ClientesTotales (ID_Cliente, TotalVentas)
SELECT ID_Cliente, SUM(TotalVentas)
FROM Ventas
GROUP BY ID_Cliente;
```
otro ejemplo:
```
INSERT INTO ClientesTotales (ID_Cliente, TotalVentas)
SELECT 
    ID_Cliente, 
    TotalVentas
FROM 
    Vista_TotalVentasPorCliente;
```

Inserciones Secuenciales
Puedes realizar múltiples inserciones de manera secuencial:
```
INSERT INTO ClientesProductos (ID_Cliente, Producto, TotalVentas)
SELECT 
    ID_Cliente, 
    Producto, 
    TotalVentas
FROM 
    Vista_ClientesVentas

UNION ALL

SELECT 
    4 AS ID_Cliente, 
    'E' AS Producto, 
    400 AS TotalVentas
```

### CROSS JOIN 
- El `CROSS JOIN` es útil cuando quieres combinar cada fila de una tabla con cada fila de otra tabla sin ninguna condición específica para la combinación. Es menos común en aplicaciones prácticas debido a la gran cantidad de datos que puede producir, pero es útil en ciertos casos como generar combinaciones de todas las posibilidades.
EJEMPLO:
![[Pasted image 20240727224656.png]]
```
SELECT 
    A.A_ID, 
    A.A_Value, 
    B.B_ID, 
    B.B_Value
FROM 
    A
CROSS JOIN 
    B;

```
![[Pasted image 20240727224725.png]]


------------
#ejemplo de inserciones: en este ejemplo usamos una vista para ingresar datos en una tabla pero faltan 2 columnas de completar dentro de esta lista lo que hacemos es usar una funcion para llenar una columna y en otra poner todos los datos como 1 por que es un boolean 
```
CREATE PROC SP_REGISTRA_CLIENTES_VIP
AS
BEGIN 
    INSERT INTO CLIENTES_VIP (REGION_ID, ID_CLIENTE, TOTAL_FACTURADO, NIVEL, DESCUENTO, ESTADO)
    SELECT
        R.REGION_ID,
        RC.ID_CLIENTE,
        RC.TOTAL,
        RC.Ranking AS NIVEL,
        dbo.GET_DESCUENTO(RC.Ranking) AS DESCUENTO,
        1 AS ESTADO
    FROM 
        DBO.REGION_CLIENTE_TOTAL_VENTA RC
    INNER JOIN 
        REGION R ON R.REGION = RC.REGION;
END;

```



---

- Como visualizar las características de una tabla (restricciones , columnas , tipos de datos)
	- clic derecho sobre la tabla en el explorador - Diseño 



---

MODIFICAR TABLA 
- **Cambiar nombre de la tabla** =>ALTER TALBE nomTabla  RENAME TO OtroNomTabla
- **Modificar el nombre de las columnas (encabezado)**=> ALTER TABLE nomTabla RENAME COLUMN nomEncabezado TO otroNomColumn
- **Agregar columna** => ALTER TABLE nomTabla ADD NomNuevaColumn NUMBER(10) o el tipo de dato que sea. 
- **Modificar tipo de dato**=> ALTER TABLE nomTabla MODIFY nomColumn VARCHAR(10) que es el tipo de dato a cambiar. 
---


---
