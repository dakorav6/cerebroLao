
# Resetear estilo en el navegador "normalize.css"

normalize.css es un archivo CSS que se usa para hacer que los estilos predeterminados de los navegadores sean más consistentes entre sí.

por que se usa normalize.css?
Los navegadores (Chrome, Firefox, Safari, Edge, etc.) aplican **estilos por defecto** a los elementos HTML. Por ejemplo: `<h1>` tiene distinto tamaño en cada navegador , `<button>` puede tener diferentes bordes o sombras e `<input>` puede verse diferente.
Esto hace que un mismo diseño se vea **ligeramente distinto** según el navegador.






----

#  Variables de color 

```


:root {

  --color-primario: #8a1919;

  --color-secundario: #555;

  --color-blanco: #fff;

  --color-texto: #333;

  --color-fondo: #f5f5f5;

}

```

- `:root` es un **selector especial en CSS** que apunta al elemento raíz del documento HTML, o sea, al `<html>`, Se usa normalmente para declarar **variables globales** que podés reutilizar en cualquier parte de tu CSS.
- ¿Por qué `--nombre-variable`? CSS utiliza dos guiones (--) al inicio del nombre de las variables para que el navegador las reconozca como "Custom Properties" o propiedades personalizadas. Es una convención definida, si es obligatorio y en caso de no ponerla CSS lo va a ignorar por que no reconoceria la custom property
- ejemplo de uso:  `button { background-color: var(--color-boton);}`
- 🧩 ¿Por qué es útil?
	- Más limpio: no tenés que escribir #8a1919 por todos lados.
	- Más fácil de mantener: si cambiás el color en :root, se cambia en todo el sitio.
	- Más organizado: podés tener un esquema de colores o diseño centralizado.



----
# BOX-SIZING 

- se usa para que el modelo de caja sea mas predecible. 
- se usa para cambiar el modelo de dimencionar la caja para que el ancho/width y alto/height de un elemento incluya el padding y el border
- es decir que si defines el ancho y luego agregar padding o border el total seguira siendo de 100px en lugar de crecer
 
```
*,
*::before,
*::after {
  box-sizing: border-box;
}
```


----
# Body y layout para footer fijo

configura el diseño base de toda la página (html y body)
- Crear un layout flexible en columna que ocupe toda la altura de la pantalla (100vh).
- Asegurar que el footer se mantenga en la parte inferior incluso si hay poco contenido.
- Aplicar un fondo de pantalla completo.
- Establecer estilos básicos como márgenes, fuente y color de texto.



```
html, body {

  height: 100%;

  margin: 0;

  font-family: 'Roboto', Arial, sans-serif;

  background-image: url('imagenes/Autoacelerandofondo.webp');

  background-repeat: no-repeat;

  background-position: center center;

  background-size: cover;

  color: var(--color-texto);

  background-attachment: fixed;

  display: flex;

  flex-direction: column;

  min-height: 100vh;

}

```


----
# Contenedor común para borde con sombra y padding 

Esta clase se puede aplicar a cualquier elemento HTML (por ejemplo, un `<div>`) para aplicar los estilos que vienen a continuación.

```
.contenedor-de-borde {

  background-color: var(--color-blanco);

  padding: 25px 30px;

  border-radius: 12px;

  box-shadow: 0 6px 15px rgba(0,0,0,0.1);

  max-width: 600px;

  margin: 30px auto;

}
```

---

# navegacion principal


```
.nav-principal ul {

  list-style: none;

  display: flex;

  justify-content: center;

  padding: 0;

  margin: 10px 0 0 0;

  gap: 25px;

  flex-wrap: nowrap;

}
```


---

# Enlaces del menú de navegación

```

.nav-principal a {

  color: var(--color-blanco);

  text-decoration: none;

  font-weight: 600;

  font-size: 1.1rem;

  padding: 6px 12px;

  border-radius: 6px;

  transition: background-color 0.3s ease, box-shadow 0.3s ease;

  display: flex;

  align-items: center;

}
```


---
# Efecto hover 

es el evento que ocurre cuando pasamos el cursor sobre algo y este cambia o realiza una acción

```
.nav-principal a:hover {
  background-color: #6f1212;
  box-shadow: 0 4px 8px rgba(138, 25, 25, 0.7);
}
```


----
#  Área principal del contenido sin sombra ni fondo

```


#contenido {

  flex: 1 0 auto;

  max-width: 900px;

  margin: 30px auto;

  padding: 0;

  background: none;

  box-shadow: none;

}
```


----
# Evita duplicar bordes o estilos en los elementos internos

```
#contenido article,

.form,

.registro-contenedor,

.form-registro {

  background: none !important;

  box-shadow: none !important;

  border: none !important;

  padding: 0 !important;

  max-width: 100% !important;

  margin: 0 !important;

}
```
- El `!important` se usa aquí para **sobrescribir otros estilos que podrían venir de otro archivo CSS, una librería, o estilos embebidos**. Es una forma fuerte de asegurar que estos estilos realmente se apliquen
- Este bloque:
	- **Limpia el estilo** visual de ciertos elementos internos.
	- Los deja “en blanco” visualmente (sin fondo, sin bordes, sin sombra, sin espaciado).
	- Es útil cuando quieres evitar que estilos anteriores afecten el diseño limpio de formularios o contenedores internos.



----

```
/* Centra las imágenes del contenido y les da sombra */

#contenido img {

  display: block;

  margin: 20px auto;

  max-width: 90%;

  height: auto;

  border-radius: 8px;

  box-shadow: 0 4px 8px rgba(138, 25, 25, 0.3);

}
```


----
# Efecto visual cuando el campo tiene el foco

```


.form-registro input:focus,

.form input:focus,

.form-registro textarea:focus,

.form textarea:focus {

  border-color: var(--color-primario);

  box-shadow: 0 0 5px var(--color-primario);

}
```

----
# Efecto Responsive Estilos adaptables a pantallas pequeñas 
```
/* Estilos adaptables a pantallas pequeñas (responsive) */

@media (max-width: 768px) {

  /* Navegación en columna en vez de fila */

  .nav-principal ul {

    flex-direction: column;

    gap: 12px;

    align-items: center;

  /* La galería de imágenes se acomoda verticalmente */

  .gallery {

    flex-direction: column;

  }
  }
```

----
