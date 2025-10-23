

Algoritmo Burbuja 

- se hacen recorridos hasta que el ultimo recorrido no haya hecho ningún cambio de posición. 
- en cada recorrido iniciamos de izquierda a derecha comparando el primer numero con el segundo y luego el segundo con el tercero, en caso de que el numero anterior sea mayor que el posterior se realiza un cambio de posición. 
```
numeros= [6,5,8,7,4]
numeros= [6,5,8,7,4]


def ordenarBurbuja (num):
	cambio=True
	while cambio :
		cambio=False 
		
		for pos in range(0 ,len(numeros)-1 ):
			numeroIzq = num[pos]
			numeroDer= num[pos+1]
			
			if numeroIzq> numeroDer:
				num[pos]=numeroDer
				num[pos+1]=numeroIzq
				cambio=True

	return num

print(ordenarBurbuja(numeros)); 

```

---
# Quick Sort 
![[Pasted image 20241001214115.png]]

*"Una colección de un solo elemento por si sola, ya se encuentra ordenada"*

