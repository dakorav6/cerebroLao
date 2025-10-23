- A cada función que se encuentra dentro del archivo views.py se lo denomina vista. 
- cada vista tiene que estar enlazada a una URL 


Creación de la primera pagina con Django 
1. creamos un archivo con el nombre `view.py` en la misma carpeta del ``_init_.py``
2. importar en view.py : 
	1. `from django.http import HttpResponse`
3. Creamos una funcion/vista
	1. cuando una pagina es requerida o solicitada django crea un objeto HttpRequest, lo que hace django es pasar HttpRequest como primer argumento de la funcion, cada vista es responsable de devolver un objeto HttpResponse.
```
def saludo (request):

    return HttpResponse ("Hola Jordan esta es la primera vista ")	
```
4. Enlazar la vista a el urls.py 
	1. importar la función(vista) del views.py
		1. `from nombreCarpetaProyecto.views import nombreFuncion, nomOtraFun ` 
	2. añadir al path
```
urlpatterns = [

    path('admin/', admin.site.urls),

    path('Saludo/', saludo ),
	path('cualquierNom/', nomFuncion),

]
```
	
----
# Paso de parámetros por la URL

- en la vista el paso de parámetros llega como String
```
def calculaEdad(request, agno): # aqui pasamos el parametro por URL

    parametro=int(agno)-2025+29   # aqui hacemos al conversion 

    documento=f'Tu edad actual es:{parametro}'

    return HttpResponse(documento)
```

- urls.py 
	- ` path('calcularEdad/<agno>',calculaEdad),`
	- el parametro va entre <> 
	- y en el URL del navegador pasaría así: `http://127.0.0.1:8000/calcularEdad/2100`

- En caso de ser 2 o mas parametros es igual:
```
def calculaEdad(request, agno, dia,hora)

path('calcularEdad/<agno>/<dia>/<hora>',calculaEdad),

```

----
