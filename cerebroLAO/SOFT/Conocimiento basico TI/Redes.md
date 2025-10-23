- Una red es un grupo de dispositivos conectados 
- Los dispositivos de una red pueden comunicarse entre si a traves de cables de red o conexiones inalámbricas 
- Estos dispositivos utilizan direcciones únicas o identificadores para localizarse entre si(``Direccion IP y MAC``)
- Los dispositivos pueden comunicarse en dos tipos de redes:
	- - **LAN (Local Area Network)**: Redes de área local que conectan dispositivos cercanos (ejemplo: en una casa o edificio).
	- **WAN (Wide Area Network)**: Redes de área amplia que conectan diferentes ubicaciones geográficas.
	- **WLAN (Wireless LAN)**: Redes LAN inalámbricas que permiten conectar dispositivos sin cables (ejemplo: WiFi).


Dispositivos que componen una red:
![[Pasted image 20241011170902.png]]
- **Switches**: Dispositivos que conectan múltiples dispositivos dentro de la misma red local (LAN).El switch, si tienes **muchos dispositivos** conectados por cables, se encarga de facilitar la comunicación interna entre los dispositivos, sin necesidad de interferir en cómo te conectas a Internet.
- **Routers**: Dispositivos que conectan diferentes redes entre sí (por ejemplo, la red local a Internet). El router distribuye esa conexión a diferentes dispositivos dentro de la casa y gestiona la comunicación con el mundo exterior.
- **Firewalls**: Herramientas de seguridad que controlan el tráfico de red y previenen accesos no autorizados.
- Modem: Su función principal es conectar una red local (como la de tu casa u oficina) a una red externa, como el **Internet**. El módem trae Internet a la casa.
	- El módem es esencial para que puedas conectar tu red local al proveedor de servicios de Internet (ISP), permitiendo que accedas a la web. A menudo, los módems se combinan con routers para formar dispositivos que proporcionan conectividad tanto por cable como inalámbrica (WiFi).

---
Red en la nube 

Una red en la nube es un conjunto de servidores u ordenadores que almacenan recursos y datos en un centro de datos remoto al que se puede acceder a través de Internet. 
Debido a que las empresas no alojan los servidores en su ubicación física, 
se dice que estos servidores están "en la nube".


----
# Protocolos de comunicación 

son un conjunto de reglas que permiten que los dispositivos se comuniquen entre sí dentro de una red. Es como un idioma común que todos los dispositivos en una red deben entender para poder intercambiar datos de manera eficiente. Garantizan que los datos enviados a través de la red lleguen al lugar correcto.



---


# Modelo TCP/IP
es un modelo estándar utilizado para la comunicación en red. Es como una forma de hacer las cosas, para enviar datos.(También se lo considera un framework por ser un conjunto de reglas)
- **TCP (Transmission Control Protocol)**: permite a dos dispositivos formar una conexión y transmitir datos. El protocolo incluye un conjunto de instrucciones para organizar los datos antes de ser enviados a través de una red y establece una conexión antes de enviar datos.
-  **IP (Internet Protocol)**:  es una cadena unica de caracteres, se encarga de dirigir los paquetes de datos entre dispositivos en diferentes redes, proporcionando direcciones IP a cada dispositivo. 
	- las ip pueden ser publicas y privadas 
		-  **IP Privada:** Solo es válida dentro de una red local y no puede ser utilizada para comunicarte directamente en Internet.
		- **IP Pública:** Se usa para la comunicación en Internet, y cualquier dispositivo en la red pública puede acceder a ella.
	- Hay dos versiones importantes:
	    - **IPv4**: La versión más común, utiliza direcciones de 32 bits (como 192.168.1.1).
	    - **IPv6**: Una versión más nueva que utiliza direcciones de 128 bits y 32 caracteres  para soportar más dispositivos (como 2001:0db8:85a3:0000:0000:8a2e:0370:7334).

#nota:La **dirección MAC** (Media Access Control) es un identificador único asignado a cada dispositivo (en la tarjeta de red) y no cambia, lo que la hace única para cada dispositivo.

## tienes 4 capas que acceso a la red 

- **Capa de Enlace o acceso a la red**: maneja cómo los paquetes de datos se transmiten por la red física. Esto incluye los dispositivos de hardware conectados a cables físicos y conmutadores que dirigen los datos a su destino.
- **Capa de Internet**: es donde se adjuntan las direcciones IP a los paquetes de datos para indicar la ubicación del emisor y el receptor.
-  **Capa de Transporte**:  incluye protocolos para controlar el flujo de tráfico a través de una red. Garantiza que los datos lleguen de manera fiable o no fiable, dependiendo del protocolo. El TCP y UDP son los dos protocolos de transporte que se dan en esta capa.
	- UDP: Lo utilizan aplicaciones a las que no les preocupa la fiabilidad de la transmisión. Dado que UDP no establece conexiones de red, se utiliza sobre todo para aplicaciones sensibles al rendimiento que funcionan en tiempo real, como la transmisión de vídeo.
	- **TCP** : es un protocolo de comunicación de Internet que permite que dos dispositivos formen una conexión y transmitan datos. Garantiza que los Datos se transmitan de forma fiable al servicio de destino
- **Capa de Aplicación**:  Los protocolos como **HTTP**, **FTP**, y **DNS** operan aquí. en la capa de aplicación, los protocolos determinan cómo los paquetes de datos interactuarán con los dispositivos receptores.

----
# Modelo OSI 
es otro modelo o forma en que se nos muestra la conexion a la red y envio de datos pero es mas teórica o detallada por lo que usa 7 capas. **Modelo TCP/IP** es práctico y es el que realmente se utiliza en Internet. 


---

# Puertos
Cuando se envían y reciben paquetes de datos a través de una red, 
se les asigna un puerto. Cada protocolo tiene un número de **puerto** asociado, que es como una “puerta” por la que el protocolo puede enviar o recibir datos. Ejemplos de puertos comunes son:
- **HTTP**: Usa el puerto 80.(para tráfico web).
- **HTTPS** (versión segura de HTTP): Usa el puerto 443.(para tráfico web seguro).
- **FTP**: Usa el puerto 20 y  21 .(para transferencia de archivos de gran tamaño).
- **DNS**: Usa el puerto 53.(traducir los nombres de dominio (como `www.google.com`))
- **SMTP**: Usa el puerto 25.(para envío de correo electrónico).

