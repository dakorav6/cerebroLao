
- GETDATE() => devuelve hora y fecha actual del servidor
	- SELECT GETDATE();
-  **LEN()** => Devuelve la longitud de una cadena.
	- SELECT LEN('Hola Mundo'); -- Devuelve 10
- **CAST()** => Convierte una expresión de un tipo de datos a otro.
	- SELECT CAST('123' AS INT); -- Convierte la cadena '123' en el entero 123


Fecha y hora 
- `` YEAR()``=> extrae el año de una fecha 
	- SELECT YEAR('2023-06-15'); -- Resultado: 2023
- MONTH() => extrae el mes de una fecha 
	- SELECT MONTH('2023-06-15'); -- Resultado: 6
- GETDATE() =>Devuelve la fecha y hora actual del sistema
	- SELECT GETDATE(); -- Resultado: Fecha y hora actual
- CONVERT (date, nomColumnaFecha) => una funcion que convierte el campo 'FECHA' al tipo de dato date. osea solo nos dara el dia, mes y año. en caso de que el campo este adicionalmente con hora, minutos y segundos lo eliminaría. 

numéricas: 

- **SUM()** => Devuelve la suma de un conjunto de valores.
	- SELECT SUM(precio) FROM Productos;
- **AVG()** => Devuelve el promedio de un conjunto de valores.
	- SELECT AVG(precio) FROM Productos;
- **MIN()** => Devuelve el valor mínimo de un conjunto de valores.
	- SELECT MIN(precio) FROM Productos;
- **MAX()** => Devuelve el valor máximo de un conjunto de valores.
	- SELECT MAX(precio) FROM Productos;
- **COUNT()** => Devuelve el número de filas en un conjunto de valores.(comieza a contar cuantos hay)
	- SELECT COUNT(*) FROM Productos;
- **ABS()** => Devuelve el valor absoluto de un número.
	- SELECT ABS(-123); -- Devuelve 123
- **ROUND()** => Redondea un número a una cantidad específica de decimales.
	- SELECT ROUND(123.4567,    2  ); -- Devuelve 123.46
- **POWER()** => Devuelve el valor de un número elevado a la potencia especificada.
	- SELECT POWER(2, 3); -- Devuelve 8
- **SQRT()** => Devuelve la raíz cuadrada de un número.
	- SELECT SQRT(16); -- Devuelve 4

---

### Procedimientos almacenados  

#define Un procedimiento almacenado es un conjunto de sentencias SQL que se pueden almacenar en la base de datos y ejecutarse de manera recurrente.
Es similar a una función en la programación, donde puedes definir una serie de operaciones y llamarlas cuando las necesites. Los procedimientos almacenados pueden aceptar parámetros de entrada y salida, lo que los hace muy flexibles y reutilizables.
#para_que_sirve procedimientos almacenado  ejecuta la lógica del lado del servidor. 

Crear un procedimiento almacenado: 
1. seleccionar BD 
2. CREATE PROCEDURE ... /*nomPorc*/    AS ..../*codigo a ejecutar*/ 
3. ==CREATE PROCEDURE== nombreProcedimiento  ==AS==    ==BEGIN    ...   END== ; (el procedimiento se ejecutara sin problema si no pones el begin pero para usar bloques de sentencia es necesario, que hay dentro de un bloque de sentencia, flujo de control,bucles etc... osea programacion.  )
1. podemos abreviar: CREATE PROC
4. El bloque `BEGIN...END` contiene las sentencias SQL que se ejecutarán cuando se llame al procedimiento.
5. ejemplo: CREATE PROCEDURE nomProcedimiento AS BEGIN SELECT ClienteID, Nombre, Email FROM Clientes WHERE Activo = 1; END; GO
6. EJECUTAR  al procedimiento : EXEC nomProceAlma;
	1. O solo clic derecho sobre el procedimiento alamacenado y ejecutar
7. Eliminar => DROP PROCEDURE sp_ObtenerClientesActivos;
ejemplo:

![[Pasted image 20240706145412.png]]
#nota podemos observar que al momento de declarar el tipo usa AS esto puede ir o no, en lo personal creo que esta de mas, podria ser solo @EDAD INT , @ORIGEN nvarchar(10) pero el otro AS que va despues de clarar todo ese si es obligatorio. 
#nota podemos crear el PROC con ayuda del ssms dandole clic derecho a la carpeta de procedimiento almacenado - nuevo procedimiento almacenado. Se genera un scrip como plantilla base para poner nuestro codigo.   

### Procedimiento con paso de  parámetros:

- cuando se usa paso de parámetros se omite el uso de la palabra DECLARE 
- todo parametro inicia con el @  ejemplo:@nomParametro y se debe declarar el tipo
	- ejemplo: ==CREATE PROC== nomProcAlm (@nombParametro as varchar(4) , 
	@nombParametro2 as int    )
	==AS==
		/*aqui vendria el codigo ejeplo: vamos a actualizar restando un valor*/
		UPDATE  nomTabla SET  nomColumna=nomColumna- @Cantidad
		WHERE condProducto=@codigoProducto
				
EJECUTAR=>    EXEC nomProc   'A003'  , 45 

También podemos inicializar los valores dentro del paso de parámetro
![[Pasted image 20240709215215.png]]


### Procedimiento con salida de datos (``OUTPUT``)
Para que una variable funcione como parámetro de salida se debe establecer el ==output== en su declaración, SOLO SE PUEDE USAR OUTPUT en paso de parámetros, se se puede usar en DECLARE ósea por ejemplo esto no se puede hacer=>
declare @mostrarNumero INT output ; 

```
CREATE PROC sumaDosNumeros
	@valor1 INT,
	@valor2 INT,
	@resultado numeric (6,2) output
AS
BEGIN
	SET @resultado = (@valor1 + @valor2) ;
END; 
```

Usando la variable del procedimiento almacenado: 
```
DECLARE @mostrarNumero INT;
EXEC sumaDosNumeros @valor1=2,@valor2=2,@resultado=@mostrarNumero OUTPUT;
SELECT @mostrarNumero AS  encabezameEsta;
```

#nota como puedes apreciar capturamos el valor ejecutando el procedimiento almacenado e igualando todos los valores incluyendo el de salida, si el de salida se iguala ahí mismo se captura. Ni pienses en crear la variable para solo coger en igualar a la ejecución del procedimiento almacenado. 

#nota te parecerá confuso el hecho de que para que me sirve retornar un valor si lo puedo hacer con select? pues presisamente ese es el problema el Select devuelve un conjuno de valores en forma de tabla pero para hacer procesos en la logica del programa se requiere un valor como tal. ejemplo:
![[Pasted image 20240709232617.png]]
Return
El uso de `RETURN` en un procedimiento almacenado se limita a devolver un solo valor entero (de tipo `INT`).
```
CREATE PROC sumaDosNumeros
	@valor1 INT,
	@valor2 INT
	
AS
BEGIN
declare @resultado INT;
	SET @resultado = (@valor1 + @valor2) ;
	return @resultado;
END; 
```
o puede quedar mucho mejor:
```
CREATE PROC sumaDosNumeros
	@valor1 INT,
	@valor2 INT
	
AS
BEGIN
	return (@valor1 + @valor2)
END; 
```


---
### Funciones 
**Crear Funciones**
- **Función de tipo Tabla**
contexto: es una funcion para calcular el total usando el precio unitario y la cantidad.
esta funcion recibe 2 parametros, estos parametros pueden ser o bien un conjunto de datos como una columna del mismo tipo que se a declarado en la función o un escalar como un numero. La operacion me va a retornar una conjunto de valores. 
```
CREATE FUNCTION CalcularPrecioTotal(
@precioUnitario numeric(18, 2) ,
@cantidad int
)RETURNS numeric(18, 2)
AS
begin
return @precioUnitario * @cantidad
end
```
LLamar a la funcion
```
select dbo.CalcularPrecioTotal(ARTICULOS.PRECIO_UNITARIO , 9) as total from ARTICULOS
```


- **Función de tipo escalar**
Tenemos aqui una funcion de tipo escalar la cual va a trabajar 1 valor por cariable declarada y va a retornar un valor del tipo especificado. 
```
CREATE FUNCTION dbo.CalcularPromedio 
(
	@Numero1 FLOAT, 
	@Numero2 FLOAT 
) 
RETURNS FLOAT 
AS
BEGIN 
	DECLARE @Promedio FLOAT; 
	SET @Promedio = (@Numero1 + @Numero2) / 2; 
	RETURN @Promedio; 
	/*
	puedes acortar el codigo asi:
	RETURN (@Numero1 + @Numero2) / 2;
	*/
END;
```
Estructura del bloque de código 
- RETURNS FLOAT => no es un error, asi es por que en este apartado se determina que tipo de dato va  a retornar. 

llamar a la función
```
SELECT dbo.CalcularPromedio(10, 20) AS Promedio;
o en otro caso 
SELECT * from  ListaPreciosTotales() 

```

#nota retornar, si aqui podemos retornar todo, desde tablas hasta VARCHAR a diferencia de procedimiento almacenados que solo retorna enteros. 
#nota  `dbo` es el esquema predeterminado y más común en SQL Server, pero puedes definir y usar otros esquemas para organizar mejor tus objetos de base de datos y controlar el acceso a ellos. [[Gestión acceso al servidor y Usuarios#**Esquemas** =>]]

Ejemplo de otro caso...
```
CREATE FUNCTION GET_DESCUENTO
(
    @Num SMALLINT
) 
RETURNS SMALLINT 
AS
BEGIN 
    IF (@Num = 1) RETURN 25;
    IF (@Num = 2) RETURN 20;
    IF (@Num = 3) RETURN 15;
    IF (@Num = 4) RETURN 10;
    IF (@Num = 5) RETURN 5;
    
    RETURN 0;
END;
```
#nota No te preocupes, una vez que un `RETURN` se ejecuta, la función termina y no sigue ejecutando el resto del código. Por lo tanto, si uno de los `IF` devuelve un valor, la ejecución termina ahí y el `RETURN 0` final no se ejecuta. 
Sí, eso también se aplica en C# y Java. Cuando se encuentra un `return`, la ejecución de la función o método se detiene inmediatamente, y el control regresa al punto desde donde fue llamado. Así que cualquier código después de un `return` dentro de una función no se ejecutará.

mas ejemplos..
return Table(OJITO CON ESE BLOQUE DE RETURN)
```
CREATE FUNCTION ListaPreciosTotales()
RETURNS TABLE
AS
RETURN
(
    SELECT codigo_producto, nombre, precio_unitario, 
           dbo.CalcularPrecioTotal(precio_unitario, 19) AS precio_total
    FROM Articulos
);
/*LLAMAR A LA FUNCION */
SELECT * FROM dbo.ListaPreciosTotales();
```


---
**Flujo de control en SQL** 
#nota no podemos usar el swtich 


---

### CURSORES 

- son objetos que permiten recorrer filas de forma secuencial, 
- son funciones que nos permiten procesar registros de uno a la vez 
- Recorren filas para traer resultados de consultas de forma secuencial
- eso se utiliza cuando no se puede realizar una operación sobre un conjunto de datos y es necesario procesar las filas individualmente. 
- tambien podemos meter el cursor en un PROC 
- no te confundas y recuerda que en funciones o en proc el paso de parametros puede recibir columnas de algun tipo osea un conjunto de valores que se alteraran en conjunto, el cursor lo que hace es disernir ese conjunto de calores para poder darle un trato especial.


```
DECLARE @descripcion numeric(18,2)
DECLARE cursor_name CURSOR FOR
SELECT column1, column2, ...
FROM table_name
OPEN cursor_name
FETCH NEXT FROM cursor_name INTO @descripcion
WHILE @@FETCH_STATUS = 0
BEGIN  /*inicio del bucle */

	PRINT @descripcion
	FETCH NEXT FROM cursor_name INTO @descripcion /*volvemos a repetir esta linea de codigo para aplicar extraccion en cada iteracion*/

END/*final del buble*/

CLOSE cursor_name   /*siempre debemos cerrar un cursor*/
DEALLOCATE cursor_name  /*es para optimizar, una práctica importante en SQL Server para liberar los recursos del sistema y evitar posibles problemas de rendimiento */


```
- FETCH NEXT FROM=> 'Extrae el siguiente valor  de ' cursor_name INTO "introducelo en " @variable.  ojo tiene que ser del mismo tipo de dato que la columna a recorrer.
- (WHILE @@FETCH_STATUS = 0) esto es lo mismo para todo osea es una constante que siempre va a estar ahi , verificar el estado del último `FETCH` osea extracción, si es exitosa el buble debe continuar.  

- podemos trabajar el cursor con mas de 1 columna con el propósito de ubicar con la segunda columna la fila a modificar para hacer un UPDATE mas personalizado.  
```
CREATE PROCEDURE ActualizarPreciosArticulos
AS
BEGIN
    DECLARE @codigo_producto VARCHAR(10), @precio_unitario DECIMAL(10, 2);

    DECLARE cursor_articulos CURSOR FOR
    SELECT codigo_producto, precio_unitario
    FROM Articulos;

    OPEN cursor_articulos;
    FETCH NEXT FROM cursor_articulos INTO @codigo_producto, @precio_unitario;

    WHILE @@FETCH_STATUS = 0
    BEGIN
        UPDATE Articulos
        SET precio_unitario = @precio_unitario * 1.10
        WHERE codigo_producto = @codigo_producto;

        FETCH NEXT FROM cursor_articulos INTO @codigo_producto, @precio_unitario;
    END;

    CLOSE cursor_articulos;
    DEALLOCATE cursor_articulos;
END;

```

Uso de un cursor dentro