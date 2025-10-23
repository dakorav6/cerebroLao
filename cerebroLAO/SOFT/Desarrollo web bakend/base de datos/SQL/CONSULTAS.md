Operaciones 
- **`SUM()`**:
    - Calcula la suma total de los valores en una columna numérica.
    - Ejemplo: `SUM(ventas.total_documento)`
- **`COUNT()`**:
    - Cuenta el número de filas en un conjunto de resultados.
    - Ejemplo: `COUNT(*)` cuenta todas las filas, `COUNT(id_cliente)` cuenta solo las filas donde `id_cliente` no es `NULL`.
- **`AVG()`**:
    - Calcula el valor promedio de los valores en una columna numérica.
    - Ejemplo: `AVG(ventas.total_documento)`
- **`MIN()`**:
    - Encuentra el valor mínimo en una columna.
    - Ejemplo: `MIN(ventas.total_documento)`
- **`MAX()`**:
    - Encuentra el valor máximo en una columna.
    - Ejemplo: `MAX(ventas.total_documento)`

---

**Como hacemos un Ranking** (`ROW_NUMBER() OVER (PARTITION BY REGION ORDER BY TOTAL DESC) AS Ranking`)

```
otro cadena code...),
SEXTO AS (
    SELECT 
        TOTAL,
        ID_CLIENTE,
        REGION,
        ROW_NUMBER() OVER (PARTITION BY REGION ORDER BY TOTAL DESC) AS Ranking
    FROM 
        QUINTO
)
SELECT
    TOTAL,
    ID_CLIENTE,
    REGION,
	Ranking
FROM 
    SEXTO
WHERE 
    Ranking <= 5;
```

nos mostraria un ranking por region:
![[Pasted image 20240727192708.png]]


- ROW_NUMBER() => La función que genera números de fila.
- OVER => Indica que estamos utilizando una función de ventana.La cláusula `OVER` se utiliza en funciones de ventana (como `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `SUM()`, etc.) para definir el conjunto de filas sobre las que la función opera.
- **PARTITION BY REGION**: Divide las filas en particiones basadas en el valor de `REGION`. Cada región tendrá su propia numeración.




---
### ``SELECT ``

 Seleccionar columna ...desde 
- ``SELECT ``columna1, columna2, ...        ``FROM ``nombre_de_tabla;
- `SELECT` anidados=> se utilizan para realizar operaciones complejas donde una consulta depende de los resultados de otra. 
Una subconsulta en la cláusula WHERE
```
SELECT nombre, salario
FROM Empleados
WHERE salario > (SELECT AVG(salario) FROM Empleados);
```
Subconsulta del SELECT 
 ``` 
SELECT nombre, salario, (SELECT AVG(salario) FROM Empleados) 
AS salarioPromedio
FROM Empleados; 
 ```

### Filtrar Datos (``WHERE``)
- La cláusula `WHERE` se utiliza para filtrar filas basadas en una condición.
```
SELECT nombre, edad FROM empleados WHERE edad > 30;
```

### Ordenación de Datos (``ORDER BY``)

```
SELECT nombre, edad FROM empleados ORDER BY edad DESC;
```
- orden ascendente (`ASC`) o descendente (`DESC`).
		
### Agrupación de Datos (`GROUP BY`) (agrupa los datos iguales  por fila )
```
SELECT columna 1 , SUM(COLUMNA2) FROM nomTabla GROUP BY nomColumnQueQueremosAgrupar; 
```

	![[Pasted image 20240606103304.png]]
	- funciones de agregación como `COUNT`, `SUM`, `AVG`, etc. 
	- 
### ``HAVING ``=>Se utiliza junto con la cláusula `GROUP BY` para filtrar grupos de filas
Nota: A diferencia de WHERE, que se utiliza para filtrar filas antes de agruparlas, HAVING se aplica después de que se han agrupado las filas.
	NOTA: La condicional al final es necesario, no funciona sin eso.
		![[Pasted image 20240606112332.png]]
		![[Pasted image 20240606112426.png]]
		
		
- Inserción de Datos (`INSERT INTO`)(insertar datos a la tabla)
	- INSERT INTO empleados (nombre, edad, departamento_id) VALUES ('Juan', 28, 3);
- Actualización de Datos (`UPDATE`) 
	- UPDATE empleados SET edad = 30 WHERE nombre = 'Juan';
- Eliminación de Datos (`DELETE`)
	- DELETE FROM empleados WHERE nombre = 'Juan';



---

### ``JOIN ``(UNE TABLAS)
contexto de caso de uso: Supongamos que tienes dos tablas: `Clientes` y `Pedidos`. La tabla `Clientes` tiene información sobre los clientes y la tabla `Pedidos` tiene información sobre los pedidos realizados por los clientes. Las tablas se pueden relacionar a través de una columna común, por ejemplo, `ClienteID`.

==SELECT== Clientes.Nombre, Clientes.Apellido, Pedidos.NumeroPedido, Pedidos.FechaPedido ==FROM== Clientes  ==INNER JOIN== Pedidos 
==ON== Clientes.ClienteID = Pedidos.ClienteID;

![[Pasted image 20240612204404.png]]
PODEMOS TRABAJAR CON MAS DE 2 TABLAS (ejemplo de 4tablas)
![[Pasted image 20240613114316.png]]
Otro ejemplo con 3 tablas + where:

![[Pasted image 20240713232456.png]]

### Tipos de `JOIN`

1. **INNER JOIN**: Retorna las filas que tienen coincidencias en ambas tablas.
2. **LEFT JOIN (o LEFT OUTER JOIN)**: Retorna todas las filas de la tabla izquierda y las coincidencias de la tabla derecha. Si no hay coincidencias, se devuelve `NULL` para la tabla derecha.
3. **RIGHT JOIN (o RIGHT OUTER JOIN)**: Retorna todas las filas de la tabla derecha y las coincidencias de la tabla izquierda. Si no hay coincidencias, se devuelve `NULL` para la tabla izquierda.
4. **FULL JOIN (o FULL OUTER JOIN)**: Retorna todas las filas cuando hay una coincidencia en una de las tablas. Si no hay coincidencias, se devuelven `NULL` para la tabla que no tiene coincidencias.


### Usar una Tabla Derivada 
Podemos usar una tabla resultante de una consulta para hacer otra consulta asi:
![[Pasted image 20240612221008.png]]
también esta la opción de subconsultas anidadas 

![[Pasted image 20240612221106.png]]

---
OPERADORES LOGICOS 

Los operadores lógicos en SQL se utilizan para combinar una o más condiciones en una cláusula `WHERE`, `HAVING`, o en una sentencia `JOIN`. Los operadores lógicos más comunes son `AND`, `OR`, y `NOT`.

1.-AND (si una es falta => 0)
	SELECT * FROM empleados WHERE edad > 30 AND departamento = 'Ventas'
2.-OR ( si una es verdadero => 1 )
		SELECT * FROM empleados WHERE edad > 30 OR departamento = 'Ventas';
3.-NOT (negar una condición)
	SELECT * FROM empleados WHERE NOT departamento = 'Ventas';

Ejemplo completo 
	SELECT * FROM empleados WHERE (edad > 30 AND departamento = 'Ventas') OR (edad < 25 AND departamento = 'IT');




Operadores de comparación 

- Operadores de comparación (= , < , > , <= , >= )
	- Operador de diferencia:  (   <>  ) 
		- SELECT * FROM empleados WHERE departamento <> 'Ventas';  (mostraria todos menos el departamente de ventas )
- - BETWEEN (ENTRE)
	- SELECT * FROM empleados WHERE edad BETWEEN 25 AND 35;
- LIKE (Coincidencia de patrones)
	- SELECT * FROM empleados WHERE nombre LIKE 'J%'; -- Nombres que comienzan con 'J' 
		- `%`: Este símbolo comodín  indica que puede haber cero o más caracteres después de la letra 'J'. (Entonces, `'%j%'` seleccionaría cualquier cadena que tenga la letra 'j' en cualquier lugar dentro de la cadena.)
- IN (se utiliza para verificar si un valor está presente en un conjunto de valores.)
	- Esto es útil cuando quieres comparar un valor con múltiples opciones.
	- ![[Pasted image 20240606123541.png]]
- 
- a
- a
- 
---
### Vistas
- Una vista es una consulta almacenada que se puede utilizar como una tabla virtual. No almacena datos por sí misma, sino que almacena una consulta que puede recuperarlos. Las vistas se utilizan para simplificar consultas complejas

Crear vista 
```
CREATE VIEW ClientesActivos 
AS
	SELECT ClienteID, Nombre, CorreoElectronico
	FROM Clientes
	WHERE Activo = 1;
```
   
Llamar a la vista
```
SELECT * FROM ClientesActivos;
```



---

EJEMPLOS DE CONSULTAS 

- CANTIDAD DE REGISTROS ALMACENADOS EN LA TABLA DE VENTAS
	- SELECT COUNT(*) FROM VENTAS
- CALCULAR EL PROMEDIO DE VENTAS PARA UN RANGO ESPEC�FICO DE FECHAS
	- SELECT AVG(TOTAL_DOCUMENTO) FROM VENTAS WHERE FECHA >= '20150101' AND FECHA <= '20150131' ; 
	- SELECT AVG(TOTAL_DOCUMENTO) FROM VENTAS WHERE FECHA BETWEEN '20150101' AND '20150131'
	- SELECT AVG(TOTAL_DOCUMENTO) FROM VENTAS  WHERE FECHA BETWEEN CONVERT(datetime,'2015-01-01 00:00:00.000', 121) AND CONVERT(datetime,'2015-01-31 23:59:59.997', 121) nota: 121 es el tipo de estilo o formato
-  ENCONTRAR EL VALOR MiNIMO Y MaXIMO DE LA COLUMNA TOTAL DOCUMENTO
	- SELECT MIN(TOTAL_DOCUMENTO) AS MinimoTotal, MAX(TOTAL_DOCUMENTO) AS MaximoTotal FROM VENTAS
- --AGRUPAR LAS VENTAS POR AñO, MES Y CALCULAR EL TOTAL Y EL PROMEDIO DE VENTAS POR MES
	- SELECT YEAR(FECHA) AS Año,    MONTH(FECHA) AS Mes,   SUM(TOTAL_DOCUMENTO) AS SumaTotal, AVG(TOTAL_DOCUMENTO) AS PromedioTotal FROM VENTAS GROUP BY YEAR(FECHA), MONTH(FECHA) ORDER BY Año, Mes ; 
-  CONTAR CUANTAS VENTAS SE REALIZARON POR CADA CLIENTE
	- SELECT TOP 5 ID_CLIENTE, COUNT(*) AS NumeroDeVentas FROM VENTAS GROUP BY ID_CLIENTE ORDER BY NumeroDeVentas DESC
- LISTAR LOS CLIENTES QUE TIENEN UN TOTAL DE VENTAS SUPERIOR A UN CIERTO VALOR (1000)
	- SELECT ID_CLIENTE, SUM(TOTAL_DOCUMENTO) AS SumaTotal FROM VENTAS GROUP BY ID_CLIENTE HAVING SUM(TOTAL_DOCUMENTO) > 3000 ORDER BY SumaTotal DESC
-  Supongamos que queremos agrupar las ventas por mes y calcular el total y el promedio de ventas por mes.
	- SELECT  YEAR(FECHA) AS A�o,  MONTH(FECHA) AS Mes,  SUM(TOTAL_DOCUMENTO) AS SumaTotal, AVG(TOTAL_DOCUMENTO) AS PromedioTotal FROM VENTAS GROUP BY YEAR(FECHA), MONTH(FECHA) ORDER BY A�o, Mes;
- Contemos cu�ntas ventas se realizaron por cada cliente:
	- SELECT  ID_CLIENTE,  COUNT(*) AS NumeroDeVentas FROM VENTAS GROUP BY ID_CLIENTE  ORDER BY NumeroDeVentas DESC
- Usamos las funciones MIN y MAX para encontrar las fechas de la primera y �ltima venta de cada cliente:
	- SELECT  ID_CLIENTE,  MIN(FECHA) AS FechaPrimeraVenta,  MAX(FECHA) AS FechaUltimaVenta FROM VENTAS GROUP BY ID_CLIENTE ORDER BY ID_CLIENTE
- 
- a
- a
- a
- a
- a
- a
- a
- a
- a
- 



