
LIMPIAR COLUMAS POR ESPACIOS 
LIMPIEZA PROFUNDA 
	UPDATE CLIENTES
	SET ORIGEN = REPLACE(REPLACE(REPLACE(REPLACE(ORIGEN, CHAR(9), ''), CHAR(10), ''), CHAR(13), ''), CHAR(160), '');

LIMPIEZA NORMAL 
	UPDATE NOMTABLA
	SET NOMCOLUMN= LTRIM(RTRIM(NOMCOLUMN));


---

Ingreso de datos en una tabla 
INSERT INTO nomTABLA(nomColumn1, nomColumn2, nomColumn3)
VALUES ( 12 ,   23, 23 );

NOTA: NO PODEMOS insertar un key como tal , estos se generan automaticamente por ser identificador unico. 
![[Pasted image 20240615110214.png]]

