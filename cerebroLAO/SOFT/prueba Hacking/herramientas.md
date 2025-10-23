

- **Repetidor**: Sirve para tomar una solicitud HTTP y enviarla repetidamente al servidor, modificándola para probar distintas entradas (parámetros, datos de formulario, etc.). Ideal para pruebas de vulnerabilidades como SQL Injection, donde puedes modificar inputs para observar el comportamiento del servidor.
- **Decodificador**: Se usa para convertir datos en distintos formatos (URL encoding, base64, etc.) a un formato legible o para codificar inputs. Esto es útil cuando te encuentras con datos encriptados o codificados que necesitas decodificar para analizarlos o modificar datos para enviar en una prueba.
- **Proxy:** es un servidor que actúa como intermediario entre un cliente (como tu navegador) y un servidor de destino. En términos simples, cuando usas un proxy, en lugar de que tu navegador se comunique directamente con el servidor de la web, las solicitudes primero pasan por el proxy, que luego las redirige al servidor final.
	- ¿Para qué se usa un proxy?
		1. **Anonimato**: Los proxies pueden ocultar tu dirección IP real, lo que te permite navegar de forma más anónima.
		2. **Filtrado de contenido**: Algunas organizaciones o redes usan proxies para bloquear o restringir acceso a ciertos sitios web.
		3. **Mejorar la seguridad**: Un proxy puede filtrar el tráfico y bloquear contenido malicioso antes de que llegue al usuario.
		4. **Optimización del tráfico**: Algunos proxies pueden almacenar en caché (guardar temporalmente) las respuestas de sitios web, reduciendo la necesidad de realizar la misma solicitud repetidamente, lo que ahorra ancho de banda.
		5. **Inspección de tráfico**: En ciberseguridad, un proxy puede interceptar, monitorear y modificar el tráfico para analizar vulnerabilidades. Por ejemplo, puedes interceptar una solicitud a un servidor, modificarla y luego reenviarla para ver cómo responde el servidor.
