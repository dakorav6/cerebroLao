
- son cadenas de textos como HTML
- sirven para separar la parte lógica de la parte visual de un documento web
- hay muchas formas de usar plantillas
- por lo general un proyecto tiene varias plantillas y para ser mas ordenados podriamos crear una carpeta para eso. 

---

# Cargadores de plantillas (Loaders y render)

Usar `render()` hace que el código sea más corto, más legible y más fácil de mantener. Solo deberías usar `loader.get_template()` si necesitas personalizar el sistema de plantillas de manera avanzada.

## render()

**settings.py**
- en el bloque de TEMPLATES/DIRS: aqui va la URL de la direccion de la carpeta con los templates que vamos a crear.
**views.py **
* Importamos
	* `from django.shortcuts import render`
* definimos la vista:
```
def saludo (request,nombre):

     return render(request, 'Hola.html',{'nombre':nombre})
```
**urls.py**
- añadimos el path para la vista creada 
	- `path('Saludo/<nombre>/', saludo ),`
**html**
- donde queramos poner  el paso de parametros lo aremos con: {{}}
- ` <h1>Hola a todos, soy {{nombre}} {{apellido}}  esta en mi primera plantilla</h1>`

## Loaders()

Se hace exactamente lo mismo que el render() solo cambia en el views.py 

- ``from django.template import loader``

```
def saludo (request,nombre,apellido):

     plantilla=loader.get_template('hola.html') #cargamos la plantilla

     contexto={'nombre':nombre , 'apellido':apellido } #creamos el diccionario de contexto

     return HttpResponse(plantilla.render(contexto,request))
```

mis conclusiones:
- este metodo van mas lineas de codigo definiendo 2 elementos principales 
	- plantilla (cargamos el html)
	- contexto (diccionario)

----
# HTML (control, bucles, filtros)
- https://docs.djangoproject.com/en/5.1/ref/templates/builtins/
- arriba puedes consultar el carajal de filtros y tambien sobre mas estructuras de control
- no es recomendable abusar de estructuras de control de flujo en el html, es limitados los casos en los que se puede hacer eso ten en cuenta esto.
- podemos acceder a un elemento de la lista con la nomeclatura del punto en lugar de la forma tradicional de python ``mi_lista[1]`` 
	-  ``<li>{{list_games.1}}</li>``
	
	Podemos acceder a muchas cosas con Django desde la plantilla HTML y se maneja bajo un orden jerárquico de llamada 
	- Diccionario
	- Atributos
	- Metodos
	- indice de lista


## **Bucles y Condicionales**
- Podemos usar bucles, condicionales desde la plantilla HTML 
```
 <ul>

        {% for game in list_games %}

            <li><p> {{game}}<br> </p> </li>

        {% endfor%}

    </ul>

```
Ejemplo 2: uso de if para mostrar algo cuando la lista esta vacía. 

```
 {% if list_games %}

            {% for game in list_games %}

                <li><p> {{game}}<br> </p> </li>

            {% endfor%}

        {% else %}

            <p>NO hay elementos que mostrar</p>

        {% endif %}
```

## **Operadores de comparación**

```
 {% if nombre_persona == "Jordan" %} 

         <p>Si el nombre que ingresaste es del programador</p>

        {% else %}

          <p>NO, el nombre que ingresaste no es el del programador</p>

    {% endif %}
```

#nota ojo aqui no tienes que volver a poner el {{}} para llamar a un atributo del view 

**Comentarios**
```
{% coment %}
	ESTO ES UN COMENTARIO de 2 o mas lineas 
	 EN EL HTML POR DJANGO
		:D
{% endcoment %}

{#ESTO ES UN COMENTARIO DE UNA SOLA LINEA DE CODIGO #}

```

## Filtro en la plantilla

Es lo mismo que los métodos especiales que se usan en los String  como el upper(convertir en mayuscula) pero su sintaxis cambia y hay multitud de Filtros.
sintaxis tradicional: `nombre_persona.upper`
sintaxis: `<p>  nombre_pesona|upper </p> `

**Encadenar filtros**
poner solo la primer letra y cambiarlo a minuscula (aqui aplicaremos 2 fitros encaenados)
``<li>{{el_tema|first|lower}} </li>`

#nota existe un carajal de filtros podemos consultar aqui: https://docs.djangoproject.com/en/5.1/ref/templates/builtins/


---
## Plantillas incrustadas 

una pagina web en un html esta compuesto por otros html 

