#frontend/html

---
NOTAS:
- nav ?
- el ceo en el head?
- h1 se recomienda usar solo una ves por pagina



----




html es
?
- Es un lenguaje de marcado , no de  programación, por que no tiene entrada de datos ni flujo de datos
- Es un lenguaje de marcado de hipertexto
- extensión del documento es:  .html
<!--SR:!2025-06-19,1,228-->


- Estructura de la pagina: 
#nota se puede aprovechar el autocompletado para escribir html5 y generar el cuerpo o estructura de la pagina.
```
<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Document</title>

</head>

<body>

</body>

</html>
```
-  `charset="UTF-8"` => es un conjunto de caracteres que admiten acentos 
- title => el nombre del documento o pagina

Icono de la pestaña de la pagina
- `<head> <Link rel = "icon" href = "URL">  </head>`
	- rel = "icon" => establece la relacion entre el documento y el archivo que queremos usar 
	- href => nos permite enlazar un archivo por medio de un url. 

---
### Cuerpo del documento (``<Body >``)

![[Pasted image 20240830110207.png]]
- **`<header>`**:  
    El encabezado de la página contiene el título principal del sitio o el logo y, generalmente, la barra de navegación (`<nav>`). La navegación ayuda a los usuarios a moverse entre las diferentes secciones del sitio web.
    
- **`<main>`**:  
    El contenedor principal del contenido de la página. Utiliza el elemento `<main>` para encerrar la parte principal del contenido de tu página. Dentro de `<main>`, se pueden utilizar varios elementos `<section>` para dividir el contenido en secciones lógicas y semánticas.
    
    - **`<section>`**:  
        Utilizado para agrupar contenido relacionado temáticamente. Cada sección debe tener un título con `<h2>` o`<h3>`, etc., y contenido como párrafos, listas, imágenes, etc.
    -  `<article>`  El elemento `<article>` se utiliza para contenido que es independiente y autónomo, lo que significa que tiene sentido por sí mismo y podría distribuirse o reutilizarse de manera independiente del resto del contenido de la página. Esto podría incluir artículos de blog, noticias, publicaciones en redes sociales, comentarios de usuarios, widgets, etc.
- **`<aside>`** (opcional):  
    El elemento `<aside>` se utiliza para contener contenido relacionado o complementario, como barras laterales, citas, enlaces a artículos relacionados o noticias recientes. Generalmente se sitúa a un lado del contenido principal.
    
- **`<footer>`**:  
    El pie de página contiene información sobre el sitio web, como derechos de autor, enlaces a términos y condiciones, política de privacidad, y cualquier otra información relevante. También puede contener otra barra de navegación o información de contacto.
	- `<address>` se utiliza para definir la información de contacto de una persona o una organización, Esta etiqueta suele colocarse en el pie de página de un sitio web o cerca del contenido que el autor ha publicado, para indicar quién es el autor o el propietario del sitio.
    
- **`<script>`**:  
    Los scripts de JavaScript se incluyen al final del `<body>` para asegurar que todo el contenido del DOM se cargue antes de que el script se ejecute, mejorando el rendimiento y la experiencia del usuario.

```
<body>
1. Encabezado de la página
  <header>
    <h1>Título de la Página</h1>
    <nav>
      <ul>
        <li><a href="#home">Inicio</a></li>
        <li><a href="#about">Acerca de</a></li>
        <li><a href="#services">Servicios</a></li>
        <li><a href="#contact">Contacto</a></li>
      </ul>
    </nav>
  </header>

  <!-- 2. Sección principal del contenido -->
  <main>
    <!-- 2.1 Sección de bienvenida o introducción -->
    <section id="home">
      <h2>Bienvenido</h2>
      <p>Texto introductorio sobre el propósito del sitio web.</p>
    </section>

	    <!-- 2.2 Sección de artículos o publicaciones -->
    <section id="articles">
      <h2>Artículos Recientes</h2>
      
      <!-- Artículo 1 -->
      <article>
        <header>
          <h3>Título del Artículo 1</h3>
          <p>Publicado el 30 de Agosto, 2024 por Autor 1</p>
        </header>
        <p>Contenido del artículo 1. Este contenido es independiente y puede ser distribuido de forma separada.</p>
        <footer>
          <p>Etiquetas: <a href="#tag1">HTML</a>, <a href="#tag2">CSS</a></p>
        </footer>
      </article>

      <!-- Artículo 2 -->
      <article>
        <header>
          <h3>Título del Artículo 2</h3>
          <p>Publicado el 29 de Agosto, 2024 por Autor 2</p>
        </header>
        <p>Contenido del artículo 2. Este es otro ejemplo de contenido independiente dentro de un elemento `<article>`.</p>
        <footer>
          <p>Etiquetas: <a href="#tag3">JavaScript</a>, <a href="#tag4">Web Development</a></p>
        </footer>
      </article>
      
    </section>



    <!-- 2.3 Sección de información -->
    <section id="about">
      <h2>Acerca de Nosotros</h2>
      <p>Descripción de la empresa, misión, visión, etc.</p>
    </section>

    <!-- 2.4 Sección de servicios -->
    <section id="services">
      <h2>Servicios</h2>
      <ul>
        <li>Servicio 1</li>
        <li>Servicio 2</li>
        <li>Servicio 3</li>
      </ul>
    </section>
  </main>

  <!-- 3. Barra lateral (opcional) -->
  <aside>
    <h2>Noticias Recientes</h2>
    <p>Breve descripción de las noticias recientes o enlaces a contenido adicional.</p>
  </aside>

  <!-- 4. Pie de página -->
  <footer>
    <p>&copy; 2024 Tu Empresa. Todos los derechos reservados.</p>
    <nav>
      <ul>
        <li><a href="#privacy">Política de Privacidad</a></li>
        <li><a href="#terms">Términos de Servicio</a></li>
      </ul>
    </nav>
  </footer>

  <!-- 5. Scripts opcionales -->
  <script src="script.js"></script>
</body>

```

---
# Etiquetas para mostrar contenido

## Encabezados 
Los encabezados se utilizan para definir la jerarquía del contenido en una página. Van desde `<h1>` hasta `<h6>`, donde `<h1>` es el nivel más alto y `<h6>` el más bajo.

- **`<h1>`**: El encabezado principal, generalmente utilizado para el título principal de la página.
- **`<h2>`**: Encabezado de segundo nivel, utilizado para subtítulos.
- **`<hgroup>`** : agrupar un conjunto de elementos de encabezado (`<h1>` a `<h6>`) cuando un encabezado principal está acompañado de uno o más subencabezados.

## Párrafos: 
- **`<p>`**: Define un párrafo. Los párrafos se separan automáticamente con un espacio antes y después del texto.
- `<pre>`  muestra textos preformateado ósea que se muestra tal cual se escribe, con los espacios en blanco , saltos de linea  y tabulaciones. 
- **`<br>`**: Inserta un salto de línea.
- **`<hr>`**: Inserta una línea horizontal que se usa para separar contenido.

## Enlaces 
- **`<a href="https://www.example.com" target="_blank">`**
	- Define un enlace que apunta a "[https://www.example.com](https://www.example.com)". El atributo `target="_blank"` hace que el enlace se abra en una nueva pestaña del navegador.
- **`<img src="https://via.placeholder.com/150" alt="Imagen de ejemplo" />`**
	- Inserta una imagen. El atributo `src` especifica la URL de la imagen, mientras que el atributo `alt` proporciona un texto alternativo que describe la imagen para accesibilidad y en caso de que la imagen no se cargue.

Botones 
- `<button>Haz clic aquí</button>`


----
### Etiquetas de agrupación


- `<div>` no representa nada, solo agrupa contenido relacionado 

----
# Dar información al navegador con `<meta>`
```
<head>
    <meta charset="UTF-8">
    <meta name="description" content="Una descripción breve de la página para SEO.">
    <meta name="keywords" content="HTML, CSS, diseño web">
    <meta name="author" content="Tu Nombre">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    
    <title>Mi Página Web</title>
    
    <link rel="stylesheet" href="styles.css">
    <link rel="icon" href="favicon.ico" type="image/x-icon">
    
    <script src="script.js"></script>
</head>

```
- **`<meta charset="UTF-8">`**: Define la codificación de caracteres utilizada en la página, asegurando que el texto se muestre correctamente.
    
- **`<meta name="description" content="...">`**: Proporciona una breve descripción del contenido de la página, utilizada por motores de búsqueda en los resultados.
    
- **`<meta name="keywords" content="...">`**: Especifica palabras clave relacionadas con el contenido de la página para ayudar en la indexación por motores de búsqueda (menos relevante hoy en día).
    
- **`<meta name="author" content="...">`**: Indica el autor de la página web.
    
- **`<meta name="viewport" content="...">`**: Configura cómo se debe mostrar la página en dispositivos móviles, controlando el ancho y la escala de la ventana de visualización.



---
# Listas 

## Lista ordenada  
```
		 <ol>
				 <li>Primero</li>
				 <li>Segundo</li>
		        <li>Tercero</li>
        </ol>
```

## Lista desordenada 
```
	  <ul>
        <li>Elemento A</li>
        <li>Elemento B</li>
        <li>Elemento C</li>
    </ul>
```

## Lista de definiciones  

```
 <dl>
        <dt>HTML</dt>
        <dd>Lenguaje de marcado para crear páginas web.</dd>
        
        <dt>CSS</dt>
        <dd>Lenguaje de estilo HTML.</dd>
        
        <dt>JavaScript</dt>
        <dd>Lenguaje de programación</dd>
    </dl>
```

## Contenido Desplegable 

- `<details>`: Define el contenedor para el contenido que se puede expandir o contraer.
 - `<summary>`: Proporciona un título o encabezado que el usuario puede hacer clic para mostrar u ocultar el contenido de `<details>`.

```
  <h1>Información Expandible</h1>

    <details>
        <summary>Sección 1: Historia</summary>
        <p>La historia es el estudio de los eventos pasados, especialmente aquellos que afectan a la humanidad. Incluye el análisis de documentos, artefactos y testimonios.</p>
    </details>

    <details>
        <summary>Sección 2: Ciencia</summary>
        <p>La ciencia es un conjunto de conocimientos sistemáticos que explican fenómenos naturales. Se basa en la observación, experimentación y el análisis.</p>
    </details>

    <details>
        <summary>Sección 3: Tecnología</summary>
        <p>La tecnología implica la aplicación de conocimientos científicos para resolver problemas prácticos. Incluye herramientas, técnicas y sistemas desarrollados para mejorar la vida humana.</p>
    </details>
```
![[Pasted image 20240829202926.png||400]]



---
#  iframe (videos y mapas)
Muestra contenido de otra fuente como videos o mapa para lograr esto se debe copiar el código ifraim que va la pagina fuente. 
`<iframe src="URL" width="ancho" height="alto"></iframe>>`


---
# Identificadores
 es un atributo que nos permite identificar uno o mas etiquetas 
`etiqueta atributo="valor> </etiqueta>"`

- id = "cualNom" => son identificadores unicos que no se pueden repetir 
	- CSS    `#cualNom{ aquivaElCodigo  }`
- class="cualNom"  => se usa mucho en CSS 
	- CSS   ` .cualNom{ aqui va el codigo   } `  `

---
# Ventanas modales o emergentes 

Se debe de configurar el clic del evento para mostrar la ventana debemos de investigar mas sobre esto ... 

```
   <button id="openDialog">Abrir Diálogo</button>

  

    <!-- El diálogo -->

    <dialog id="myDialog">

        <p>Este es el contenido del diálogo.</p>

        <button id="closeDialog">Cerrar</button>

    </dialog>
```

---
# Enlace de ruta

La etiqueta `<a>` (ancla) se utiliza para crear hipervínculos que permiten a los usuarios navegar a otras páginas o recursos.

```
<a href="URL">Texto del enlace</a>

```

**Usos comunes del `href` en `<a>`:**

- **Enlaces a otras páginas web**: `href="https://www.ejemplo.com"`
- **Enlaces a secciones dentro de la misma página**: `href="#seccion"`

---
# Tablas

![[Pasted image 20240829205914.png]]

```
<h1>Ejemplo de Tabla HTML</h1>

<table>
    <caption>Lista de Empleados</caption>
    <thead>
        <tr>
            <th>Nombre</th>
            <th>Puesto</th>
            <th>Salario</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Ana Pérez</td>
            <td>Desarrolladora</td>
            <td>$3000</td>
        </tr>
        <tr>
            <td>Luis Gómez</td>
            <td>Diseñador</td>
            <td>$2800</td>
        </tr>
        <tr>
            <td>María Fernández</td>
            <td>Gerente</td>
            <td>$3500</td>
        </tr>
    </tbody>
</table>

```

---
# Formularios
Un formulario en HTML se define con la etiqueta `<form>`, y dentro de él se pueden incluir una variedad de elementos para recoger datos del usuario. Aquí está la estructura básica:

```
<form action="URL" method="metodo">    

<!-- ******Elementos del formulario********* -->

</form>
```
- **`action`**: Especifica la URL a la que se enviarán los datos del formulario cuando se envíen o a que servidor va a ir a parar toda la informacion.
- **`method`**: Define el método HTTP que se utilizará para enviar los datos (`GET` o `POST`).

## Elementos del formulario 

1. **Campos de Texto**
- **`<input type="text">`**: Campo de texto para ingresar información.
```
<label for="name">Nombre:</label>
<input type="text" id="name" name="name">

```
- **`<textarea>`**: Área de texto de varias líneas.
```
<label for="message">Mensaje:</label>
<textarea id="message" name="message" rows="4" cols="50"></textarea>

```

- `<label>` se utiliza para definir una relación entre una etiqueta de texto y un elemento de formulario, como un campo de entrada (`<input>`), una lista desplegable (`<select>`), un área de texto (`<textarea>`), entre otros.
- ` for`  El atributo for en una etiqueta `<label>` debe coincidir con el valor del atributo `id` del elemento de formulario que se está etiquetando. Esto establece una relación entre la etiqueta y el campo de entrada, facilitando la interacción con el formulario.
- `name` El servidor usa el valor de `name` para procesar y almacenar los datos del formulario. No es posible usar el id para esta relacion. 

2. **Campos de Selección**

- **`<select>`**: Menú desplegable para seleccionar una opción de una lista.
```
<label for="color">Color favorito:</label>
<select id="color" name="color">
    <option value="rojo">Rojo</option>
    <option value="verde">Verde</option>
    <option value="azul">Azul</option>
</select>

```

- **`<datalist>`**: Lista de opciones predefinidas para un campo de entrada.
```
<label for="fruit">Fruta:</label>
<input list="fruits" id="fruit" name="fruit">
<datalist id="fruits">
    <option value="Manzana">
    <option value="Banana">
    <option value="Cereza">
</datalist>

```

3. **Botones**

- **`<button>`**: Botón que puede tener diferentes tipos (`submit`, `reset`, `button`).
```
<button type="submit">Enviar</button>
<button type="reset">Restablecer</button>

```
- **`<input type="submit">`**: Botón para enviar el formulario.
```
<input type="submit" value="Enviar">

```

4. Casillas de Verificación y Botones de Radio
- **`<input type="checkbox">`**: Casilla de verificación que puede estar marcada o desmarcada.
```
<label for="subscribe">
    <input type="checkbox" id="subscribe" name="subscribe"> Suscribirse al boletín
</label>

```
- **`<input type="radio">`**: Botones de radio para seleccionar una opción de un grupo.
```
<label>
    <input type="radio" name="gender" value="male"> Hombre
</label>
<label>
    <input type="radio" name="gender" value="female"> Mujer
</label>

```
5. Campos de Archivo
- **`<input type="file">`**: Campo para seleccionar archivos.
```
<label for="file">Seleccionar archivo:</label>
<input type="file" id="file" name="file">

```
6. **Campo de Fecha y Hora**

- **`<input type="date">`**: Campo para seleccionar una fecha.
```
<label for="birthday">Fecha de nacimiento:</label>
<input type="date" id="birthday" name="birthday">

```
- **`<input type="time">`**: Campo para seleccionar una hora.

```
<label for="appointment">Hora de la cita:</label>
<input type="time" id="appointment" name="appointment">

```
7. Email  y otros elementos del formulario mas
```
<form action="/submit" method="POST">
    <label for="email">Correo Electrónico:</label>
    <input type="email" id="email" name="email" required>
    <br><br>
    
    <input type="submit" value="Suscribirse">
</form>
```
- **`<input type="text">`**: Campo de entrada de texto.
- **`<input type="password">`**: Campo de entrada para contraseñas.
- **`<input type="email">`**: Campo de entrada para correos electrónicos.
- **`<input type="number">`**: Campo de entrada para números.
- **`<input type="date">`**: Campo de entrada para seleccionar fechas.
- **`<input type="radio">`**: Botones de opción para selección única.
- **`<input type="checkbox">`**: Casillas de verificación para selección múltiple.
- **`<input type="file">`**: Campo de entrada para selección de archivos.
- **`<input type="submit">`**: Botón para enviar el formulario.
- **`<input type="reset">`**: Botón para restablecer el formulario.
- **`<input type="color">`**: Selector de color.
- **`<input type="range">`**: Control deslizante para seleccionar un valor en un rango.
- **`<textarea>`**: Campo de texto de varias líneas.
- **`<select>` y `<option>`**: Lista desplegable para seleccionar opciones.
- **`<button>`**: Botón para acciones personalizadas.
- **`<fieldset>`** y **`<legend>`**: Contenedor y título para agrupar elementos relacionados.
- **`<datalist>`**: Lista de opciones sugeridas para un campo de entrada.
- **`<output>`**: Contenedor para mostrar el resultado de cálculos o acciones.
- **`<label>`**: Etiqueta para describir elementos de formulario.

atributos 
- **`required`**: Indica que el campo debe completarse antes de enviar el formulario.
- `placeholder` :podemos poner en el input un modelo que muestre al usuario como lo queremos que llene el campo.
```
<input type="email" id= "correoEelectronico" required placeholder= "email@dominio.com">

<label for= "telefono"> TELEFONO </label>
<input type="tel" id="telefono" required placeholder="(XX) XXXX XXXX">

```
- **`readonly`**: Hace que el campo de entrada sea de solo lectura (no se puede modificar). Útil cuando se quiere mostrar un valor que no debe ser cambiado por el usuario.
- **`disabled`**: Deshabilita el campo de entrada (no se puede interactuar con él). Se usa cuando una entrada no debe estar disponible para la interacción del usuario.
- **`maxlength`**: Número máximo de caracteres permitidos en el campo de entrada. Es importante para limitar la longitud del texto que puede introducirse.
- **`min`** y **`max`**: Definen los valores mínimos y máximos permitidos para el campo de entrada (usado con tipos como "number", "date", etc.). Es esencial para la validación de rangos de entrada.
- **`checked`**: Indica que un campo de entrada de tipo "checkbox" o "radio" está seleccionado de forma predeterminada. Es necesario para establecer valores por defecto en opciones seleccionables.

ejemplo completo: 
```
<body>

  

    <h1>Formulario de Registro</h1>

  

    <form action="/submit" method="POST">

        <label for="name">Nombre:</label>

        <input type="text" id="name" name="name" required>

        <br><br>

        <label for="email">Correo electrónico:</label>

        <input type="email" id="email" name="email" required>

        <br><br>

        <label for="gender">Género:</label>

        <input type="radio" id="male" name="gender" value="male">

        <label for="male">Masculino</label>

        <input type="radio" id="female" name="gender" value="female">

        <label for="female">Femenino</label>

        <br><br>

        <label for="bio">Biografía:</label>

        <textarea id="bio" name="bio" rows="4" cols="50"></textarea>

        <br><br>

        <label for="country">País:</label>

        <select id="country" name="country">

            <option value="ecuador">Ecuador</option>

            <option value="colombia">Colombia</option>

            <option value="peru">Perú</option>

        </select>

        <br><br>

        <label for="subscribe">

            <input type="checkbox" id="subscribe" name="subscribe"> Suscribirse al boletín

        </label>

        <br><br>

        <label for="file">Seleccionar archivo:</label>

        <input type="file" id="file" name="file">

        <br><br>

        <input type="submit" value="Enviar">

    </form>

    </body>
```
![[Pasted image 20240830095614.png]]

---
# `<canvas>`
es un elemento que se utiliza para dibujar gráficos, animaciones, y otras representaciones visuales de manera dinámica mediante JavaScript. Es un espacio en blanco sobre el cual se puede "pintar" utilizando una serie de métodos y propiedades.
Por sí solo, el elemento `<canvas>` es simplemente un contenedor gráfico sin contenido visual hasta que se utiliza JavaScript para dibujar en él.

![[Pasted image 20240830164150.png||2000]]
---
# Etiquetas que creo que no son muy útiles 

- `<blockquote>` representa texto que cita de otra fuente, el texto se mostraria con cursiva 
- `<time>`  o `<datatime>`: publicar fecha o fecha y hora
- `<strong>`: marca las partes mas importantes de un texto “mucho enfasis osea con negrita”
- 


