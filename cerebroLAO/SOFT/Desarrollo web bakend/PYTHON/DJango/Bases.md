
----

* https://www.youtube.com/watch?v=T1intZyhXDU
* FUENTE OFICIAL : https://docs.djangoproject.com/en/5.1/
* Extenciones vsCode: Django "Baptiste Darhenay" / Beautiful syntax 



---

- Es un framework ( es un marco o entorno de trabajo )  es un conjunto de herramientas, librerías y buenas practicas
- Para que sirve Django? para crear sitios web (complejos) de forma rápida y sencilla
- Los proyectos en Django se dividen en distintas aplicaciones. 
- Trabaja con la filosofía  Modelo - vista - controlador :  
	- Modelo: gestiona los datos con la base de datos (en django es MODEL)
	- Vista :  interfaz con el usuario (django es TEMPLATE)
	- Controlador :  interacción vista - modelo (en django es VIEW )
- se puede hacer consultas a la BD solo con python pero en caso de requerir sentencia SQL tambien la podemos hacer

- **existen 2 tipos instalación**, en entorno virtual y entorno local, se recomienda la instalación virtual por que la local depende mucho de la versión que se instale en el ordenador y la virtual no, ya que cada cada entorno virtual se podrá instalar la versión que mas se ajuste a nuestra necesidades. 
---
Requisitos 
* tener instalado Python
* instalar django
* 

Bases de datos que soportan Django 
* SQLITE3 
* PostgreSQL
* MySQL
* Oracle
----
Comunicación entre MODELO -VISTA -CONTROLADOR

![[MTV.png]]


Request 
	para hacer la peticion
HttpResponse
	para enviar la respuesta



----
# Instalación Local

**PASO 1: Crear un proyecto**
1. en el cmd   
	1. `cd C:\Users\jorda\OneDrive\LAO\Conocimiento SOFTWARE\Python\Django\Django Local
	2. `django-admin startproject nombreDeNuestroProyecto ` nota: se genera una carpeta

Estructura de archivos 
* _init_.py => 
* settings.py => configuraciones del proyecto 
* url.py=> se almacena las url de nuestro proyecto 
* wsgi.py => servidor web de nuestro proyecto de django



**PASO 2: Ejecutar las migraciones para configurar la base de datos:**
* Esto creará automáticamente el archivo `db.sqlite3` (base de datos por defecto de Django) y configurará las tablas necesarias.

2. en el cmd en el url de la carpeta de nuestro proyecto 
	1. `python manage.py migrate`
**¿que es migrate?**
aplica cambios en la BD 

**PASO 3: Iniciar/arrancar  el servidor**
- Django viene con un servidor que para proyectos serios no permite hacer múltiples peticiones simultaneas, pero para nuestra educación si va a servir. 
- para ejecutar el servidor en el cmd:
	- `python manage.py runserver`
	- si todo va bien nos tiene que arrojar un url de nuestro servidor



---

# Instalación en virtual 

existen varios entornos virtuales que podemos trabajar como: Virtualenv , Venv (Integrado en Python) , Pipenv entre otras. 

**¿Cuál se recomienda trabajar?**
- **Para empezar**: Te recomendaría usar **`virtualenv` o `venv`**, ya que son sencillos, ligeros y funcionales para la mayoría de proyectos.
- **Para proyectos grandes o si necesitas gestionar muchas dependencias**: Considera **Pipenv** o **Poetry**. Estas herramientas son más avanzadas y útiles para gestionar proyectos con muchas dependencias y versiones.

## Crear un entorno virtual 
3. creamos una carpeta ingresamor el url de esa carpeta en el terminal con el comando `cd`
4. **Instalar `virtualenv`** (si no lo tienes): `pip install virtualenv`
5. **Crear un entorno virtual** en la carpeta de tu proyecto: `virtualenv venv`
	1. Esto crea un entorno virtual llamado `venv` (puedes llamarlo como quieras).
6. **Activar el entorno virtual**: `venv\Scripts\activate` (esto es para windows) 
	1. hay un archivo dentro del proyecto-Scripts-activate tenemos que llegar a ese por medio de la ruta eso es todo. (alt+92 para `\`)
7. **Instalar Django en el entorno virtual**: Una vez que el entorno está activado, puedes instalar Django solo para este proyecto: ``pip install django``
8. **Verificar la instalación**: Para comprobar que Django se ha instalado correctamente, puedes usar: `django-admin --version`
9. **Desactivar el entorno virtual**: Cuando termines de trabajar, puedes desactivar el entorno virtual con: `deactivate`

#nota La opción de instalar Django en un entorno virtual es la más segura y flexible para evitar futuros problemas con dependencias. A medida que trabajes en más proyectos, será esencial para mantener todo organizado.

- Si el entorno está correctamente activado, verás algo así en tu terminal: ejemplo:dakora
`(dakora) C:\Users\jorda\OneDrive\LAO\Conocimiento SOFTWARE\Python\proyecto Django>`

- como conclusión sabras que dentro de este entorno virtual tienes un python y un Django distinto al de tu ordenador, es un espacio de trabajo aparte. Si es verdad que no instalaste python esto se debe a que cuando creas un entorno virtual con virtualenv o venv ya utiliza la version de python que esta instalada en tu sistema duplicando el interprete de python que ya tenemos. 
- Al cerrar la ventana del terminal (o la pestaña del terminal en VS Code), el entorno virtual se desactiva automáticamente. No necesitas preocuparte por desactivarlo manualmente antes de cerrar el terminal.

---
## Crear un proyecto dentro del entorno virtual 

10. Trabajaremos directamente con el terminal de visual estudio code. Ctrl+ñ
11. Crear un nuevo proyecto escribimos en el terminal:  ``django-admin startproject mi_proyecto``
12. Ejecutar el servidor de desarrollo: 
	1. entramos a la carpeta de nuestro proyecto `cd nombreProyectoCreado`
	2. ejecutamos el comando: `python manage.py runserver`
	3. no importa si sale un mensaje en rojo, lo que nos interesa es el url de nuestro servidor de django (en caso de tener otros proyectos puede que te de el mismo link y ahi tendriamos que pedir otro)
	4. Al final podemos apreciar que se an creado una estructura  carpetas y archivos de nuestro proyecto incluido una base de datos `bd.sqlite3`. 
#nota en el archivo settings esta todas las configuraciones como por ejemplo a que base datos nos queremos conectar por defecto esta configurado a SQLite y otras configuraciones mas de forma general (BUSCA MAS INFORMACION como configrar esto.)
otras configuraciones: 
- lenguaje por defecto, horarios, 
- URL de archivos estáticos (html,css)
- 

## Crear aplicaciones 

Recuerda un proyecto en Django esta formado por aplicaciones 
13. tenemos que estar dentro del entorno virtual 
14. Crear proyecto (terminal): ``python manage.py startapp miPrimeraAppDj``
	1. Esto creará una nueva carpeta **miPrimeraAppDj** dentro de tu proyecto, con los archivos necesarios para gestionar la lógica de esa aplicación.
	2. en caso de no estar en la url de la carpeta que contiene `manage.py` movernos asi ojo con las comillas dobles en la URL: `cd "C:\Users\jorda\OneDrive\LAO\Conocimiento SOFTWARE\Python\proyecto Django"
	
15. **Incluir la aplicación en el proyecto**: Ahora, para que Django sepa que quieres usar esta nueva aplicación, debes registrarla en el archivo de configuración de tu proyecto. Ve al archivo **`settings.py`** dentro de la carpeta **mi_proyecto** y busca la lista llamada `INSTALLED_APPS`. Allí, añade el nombre de tu aplicación, **miPrimeraAppDj**
```
INSTALLED_APPS = [
    ...
    'mi_app',
]

```
### Estructura de archivos de la aplicación
- `views.py`:  lo que queremos que muestre en el navegador, aqui vamos enviar los html
- `__init__.py` : como sabras es solo para que la carpeta sea considerada un modulo
- `models.py`: para crear clases que al final se convertirán en tablas de SQL
- carpeta `migratios`: sirve para actualizar codigo de la base de datos.