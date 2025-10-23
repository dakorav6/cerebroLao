indice tiobe top lenguajes de programación:
https://www.tiobe.com/tiobe-index/



### Operadores 

Aritméticos  
	suma (+)
	resta(-)
	multiplicación( * )
	división( / )
	modulo(%) => devuelve el residuo de una división 
	exponente ( ** )=> 2 elevado a 3 seria (2 ** 3=8)
	división entera ( // )=> devuelve solo la parte entera de una divi. ejem. (7//3 = 2)

Comparación 
	Igual que=> ( == )
	diferente que =>  (  != )
	mayor que => (  > )
	menor que => ( < )
	mayor igual que => ( >= )
	menor igual que =>  ( <=  )
Lógicos 
	AND => &&
	OR => || 
	NOT=> !

Asignación
	igual =>  ( = )
	incremento =>  ( += )
	decremento => ( -= )
	multiplicativo => ( * = )
	dividirlo=> ( /=)
	(  %= )
	( ** = )
	(// = )

Especiales 
	IS 
	IS NOT 
	IN
	NOT IN 

---
### Datos 

- int (numero enteros)
- long (numeros enteros grandes)
- byte (numeros pequeños -127 hasta 127)
- float (numeros decimales)
- double (numeros decimales con con parte decimal mas larga que float)
- decimal (numeros con decimal mas largas que double)
- string (cadena de caracteres)
- char (un unico caracter)
- bool (true o false)

### Conversiones de datos 
- implícita =>que es la que se hace de forma automatica con un dato pequeño a uno mas grande ejem: de entero a decimal. 
- explicita o Casting=> es todo lo contrario, va de uno grande a uno pequeño y hay perdida de datos  ejem: de float a entero. 
		- nomVariableInt = (int) nomVaraibleFloat
		- 

### Conversión de texto a numero:
- int.parse(nomVariable)
- double.parse(nomVariable) ... y asi con lo demas numeros 

Conversion de numero a String/texto

---
Métodos 
- El método main es el método principal donde inicia la ejecución de un programa. es estatico y no retorna nada(void) ejem: static void Main(string[] args)
- un metodo static no requiere un objeto para ser llamado.
- 
- existen de 2 tipos los que retornan que son de un tipo en espesifico y los que no retornan (void)

int sumarNumeros(){
//aqui bloque de codigo 
return resultado;
}

void sumaNumero(){

}


### Sobre Carga de Métodos 
se crear varios métodos con el mismo nombre pero lo que lo distingue es el paso de parámetros. (ya sean diferentes tipos de parámetros o cantidad de parámetros. )
![[Pasted image 20240620165707.png]]

---
Modificadores  
Static => no necesita de la creación del objeto para existir 
![[Pasted image 20240622205553.png||500]]

modificadores de accedo 
se aplican a las clases , atributos y metodos 
- Public = visible para todos.
- Private solo misma clase.
- No definido: visible mismo paquete.
- Protected= serán visibles en el mismo package y clases hijas.



---
Funciones por defecto 

Clase Math.
- Math.PI=> el valor de 3.14....
- Math.Max=> 
- Math.Min=>
- Math.Pow(base,exponente)=> es un numero elevado al exponente

String (java)
nomVariable. length() => nos devulve el tamaño de la cadena 
nomVariable.indexOf("hola")=> busca "Hola" en un String devlviendo la posicion 
nomVariable.toLowerCase()=> transforma el string a minusculas
nomVariable.toUpperCase()=> transforma el string a mayuscula 

---
# Flujo  de Control 

- if(condicion){  código se ejecuta si la condición es verdadera  }
		else{ caso contrario se ejecuta este bloque de código  }


- switch(valorVariable){
	case valorComparativo:   código      break;
	case valorComparativo:   código      break;
	case valorComparativo:   código      break;
	default:    código                              break;
}

Nota: no se puede usar ni float ni double para el switch para esos casos se recomienda if. 

---
bucles 

while(condición) {  si se cumple la condición se ejecuta este código  }

/////////////////////////////////////////////////////

do{
bloque de código que se ejecutara 1 vez por lo menos

}while(condición)

-----
Excepciones 
-  errores en tiempos de ejecución y las excepciones nos permite tratar esos errores 
como?
usando try .... catch (intenta .... captura)
	try{  código que intenta  ejecutar...
		  } catch(FormatException e) {   ///codigo que se ejecuta si hay escepcion  }

---
# Estructura de datos (colexion )

## Arrays

- pueden declararse vacías 
- se identifican los elementos por su posición, iniciando a partir de 0. 



----
Recursividad

Una función puede llamarse a sí misma. Esto se llama **recursión**. La recursión es una técnica en la que una función se llama a sí misma para resolver un problema más pequeño del mismo tipo. Es importante que exista una **condición de salida** o **caso base** para evitar que la función se llame infinitamente, lo que provocaría un desbordamiento de la pila (stack overflow).

ejemplo clasico: Factorial de un numero. 
