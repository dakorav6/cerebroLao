#frontend/css


# Conceptos 
- CSS :: significa hojas de estilo en cascada nos permite controlar el aspecto visual de una pagina web (diseño)
<!--SR:!2025-05-22,7,250-->

# Puntos clave

- efecto casaca en css :: la cascada sigue el conjunto de reglas de prioridad pero cuando varias reglas apuntan al mismo elemento, se aplicara la mas fuerte, 
- Las etiquetas tienen su jerarquía al momento de aplicar cambios o estilo 
		etiqueta (1) , clases y pseudoclases(10) , id (100) , estilos en linea (1000) y por ultimo el !import(gana a todos.)
- usamos id cuando queremos alterar comportamiento y usamos clases cuando queremos alterar estilos eso como buena practica???
- ``/*Esto es un comentario*/``
- el uso de rem como medida en lugar de px es lo recomendado
- padding es lo qe esta dentro del borde y margin es lo que esta fuera del borde
- para mostrar el borde tenemos que poner solid ejemplo: ` border : 10 px solid black`
- clave: inherit, con esto toma el valor del padre un ejemplo de aplicacion seria color:inherit 
# Galería de componentes de diseño

- https://uiverse.io/ 
- https://codemyui.com/
- https://www.wickedblocks.dev/
- 



----

# Aplicación de estilos
?
css maneja una estructura de clave:valor
![[Pasted image 20250512231114.png]]
1. asociar una hoja de estilo externa 
` <link rel = "stylesheet" href="nombreArchivoDiseño.css">`
2. en linea dentro de una etiqueta
`<p style= "color:blue"> parrafo </p>`
3. en el head `<style> codigo css </style>`
``
----

## Selectores 

1. **Selectores ID:**
?
Aplica estilos a un único elemento con un atributo `id`.
```
css
#titulo-principal {
  text-align: center;
}
html
<h1 id="titulo-principal">Bienvenido</h1>

```
<!--SR:!2025-05-18,3,252-->

2. **Selector de etiquetas
?
selecciona elementos HTML
`h2 {color: gray}`
<!--SR:!2025-05-18,3,252-->

3. **Agrupación de selectores** 
?
queremos en distintos elementos tengan un mismo estilo
`h2, p{ color:gray}`
<!--SR:!2025-05-18,3,252-->

4. **Selector Universal**
?
El selector universal ``(*) ``selecciona todos los elementos html
`*{ margin : o ;   }`
<!--SR:!2025-06-29,11,270-->

5. **Selector de clase ( .nombreClase)**
?
Es la forma mas común de aplicar estilos.
		html
			`<p class='cosito'> Estamos aprendiendo CSS </p>`
			`<h2 class='cosito'> Podemos usar la clase en varios elementos </h2>  `
		css
			`.cosito { color:pink ; font-size:20px; }`
<!--SR:!2025-05-24,9,252-->

6. **Selector multiple**
?
nav ,select , foder{  }
<!--SR:!2025-05-18,3,252-->

7. Selector de id 
solo se usa en un unico elemento
html: `<h1 id="cualNom">   </h1>`
css: ` #caulNom{      } `

8. **Selector descendente o en cascada**
?
podemos modificar una etiqueta que esta dentro de otra etiqueta para referenciar ese tipo de combinación sin alterar las otras etiquetas. 
ejemplo1: nav ul li{ clackground-color: azul ; }`
ejemplo2: ` form input , form texttarea{  /*codigo css*/  }`


9. **selector por atributo** 
Selecciona todos los elementos que **tienen ese atributo**, sin importar el valor.
```
[input] {
  border: 1px solid gray;
}
```
nota: aqui podemos aplicar operadores de logica matematica en los atributos

-----
# Cajas

*"En la web todo son cajas"*



- Existen 2 tipo de cajas :: elementos en linea(solo ocupa su contenido y no se puede modifiar su ancho y alto ejem: <a>)  y elementos en bloque (ocupa el ancho disponible )
- 