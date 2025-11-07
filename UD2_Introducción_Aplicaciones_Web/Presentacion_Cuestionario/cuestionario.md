Cuestionario presentación	
2º DAW - Desarrollo aplicaciones Web 			Beatriz Gutiérrez Escudero

1. ¿Qué significa las siglas HTTP y para qué se utiliza?

HTTP, de sus siglas en inglés: "Hypertext Transfer Protocol", es el nombre de un protocolo el cual nos permite realizar una petición de datos y recursos, como pueden ser documentos HTML. Es la base de cualquier intercambio de datos en la Web, y un protocolo de estructura cliente-servidor, esto quiere decir que una petición de datos es iniciada por el elemento que recibirá los datos (el cliente), normalmente un navegador Web. 

Clientes y servidores se comunican intercambiando mensajes individuales (en contraposición a las comunicaciones que utilizan flujos continuos de datos). Los mensajes que envía el cliente, normalmente un navegador Web, se llaman peticiones, y los mensajes enviados por el servidor se llaman respuestas.

La característica del protocolo HTTP de ser ampliable, ha permitido que durante su desarrollo se hayan implementado más funciones de control y funcionalidad sobre la Web. Se presenta a continuación una lista con los elementos que se pueden controlar con el protocolo HTTP:
Caché: El cómo se almacenan los documentos en la caché, puede ser especificado por HTTP. 
Flexibilidad del requisito de origen: Para prevenir invasiones de la privacidad de los usuarios, los navegadores Web, solamente permiten a páginas del mismo origen, compartir la información o datos. 
Autentificación: Hay páginas Web, que pueden estar protegidas, de manera que solo los usuarios autorizados puedan acceder. 
Proxies y tunneling: Servidores y/o clientes pueden estar en intranets y esconder así su verdadera dirección IP a otros.
Sesiones: El uso de HTTP cookies permite relacionar peticiones con el estado del servidor.

2. ¿En qué puerto funciona normalmente el protocolo HTTP?

El puerto 80 es la puerta de entrada a la comunicación web no cifrada, y sirve como puerto por defecto para HTTP (Protocolo de Transferencia de Hipertexto). Introducido en los primeros días de Internet, HTTP se convirtió en la columna vertebral del tráfico web, permitiendo a los navegadores solicitar y recuperar recursos como HTML, CSS, imágenes y páginas web de los servidores. Esta comunicación se basa en un modelo de solicitud-respuesta, en el que el navegador inicia una consulta y el servidor responde con los datos solicitados.

3. ¿Cuál es la diferencia principal entre HTTP y HTTPS?

Los puertos 80 y 443 sirven para fines similares al facilitar el tráfico web, pero difieren significativamente en términos de seguridad, funcionalidad y confianza del usuario. A continuación, una comparación detallada de sus características clave:
Función
Puerto 80 (HTTP)
Puerto 443 (HTTPS)
Cifrado
Ninguno; los datos se transmiten en texto plano
Encriptación completa mediante SSL/TLS
Seguridad
Vulnerable a ataques de sniffing e inyección de datos
Protege contra ataques de intermediario, manipulación
Casos prácticos
Datos no sensibles (por ejemplo, contenido público)
Datos sensibles (por ejemplo, pagos, información personal)
Indicadores del navegador
Muestra advertencias «No seguro» en los navegadores modernos
Muestra el icono del candado; genera confianza en el usuario
Protocolo
Utiliza HTTP
Utiliza HTTPS
Aplicación
Requiere una configuración mínima
Requiere certificado SSL/TLS

Aunque el puerto 80 sentó las bases de la World Wide Web, su comunicación no cifrada lo convierte en un objetivo para los ciberdelincuentes. Los datos que viajan a través de HTTP pueden ser interceptados o modificados, lo que supone un riesgo para los usuarios. Por ejemplo, las redes Wi-Fi públicas son puntos calientes para los actores maliciosos que explotan las vulnerabilidades de HTTP.
En cambio, el puerto 443 protege los datos sensibles del usuario cifrándolos durante la transmisión, lo que garantiza que permanezcan seguros dentro de una red protegida. Este canal seguro se consigue mediante protocolos como TLS, que utilizan claves criptográficas para garantizar la privacidad de la información. HTTPS también autentifica las identidades de los servidores mediante certificados digitales emitidos por autoridades de confianza, lo que aumenta aún más la seguridad.

4. ¿Qué función cumple el servidor web Apache dentro de una arquitectura web?

El servidor web Apache está construido para facilitar la comunicación entre un navegador web (comúnmente conocido como "cliente") y el servidor donde se guardan los archivos de un sitio web. Su propósito fundamental es procesar las solicitudes de contenido mediante la entrega de páginas web, HTML, CSS y más a través de un navegador web. Esencialmente, el software que sustenta Apache actúa como intermediario, escuchando constantemente las peticiones de los usuarios y respondiendo con contenidos.

5. ¿Cómo puedes comprobar si el servicio de Apache está activo en un sistema Ubuntu?

Se utiliza el gestor del sistema systemd para comprobar si el servicio Apache está activo.

6. Explica brevemente en qué consiste una arquitectura cliente-servidor.
El modelo cliente-servidor, también conocido como “principio cliente-servidor”, es un modelo de comunicación que permite la distribución de tareas dentro de una red de ordenadores.
Un servidor es un hardware que proporciona los recursos necesarios para otros ordenadores o programas, pero un servidor también puede ser un programa informático que se comunica con los clientes. Un servidor acepta las peticiones del cliente, las procesa y proporciona la respuesta solicitada. También existen diferentes tipos de clientes. Un ordenador o un programa informático se comunica con el servidor, envía solicitudes y recibe respuestas del servidor. 

7. ¿Qué diferencia hay entre una arquitectura de dos capas y una de tres capas en entornos web?

La diferencia principal entre una arquitectura de dos capas y una de tres capas en entornos web es la separación de la lógica de negocio. En la arquitectura de dos capas, el cliente se comunica directamente con la base de datos y la lógica de negocio está mezclada o en la misma capa de presentación o datos. En cambio, en la arquitectura de tres capas, existe una capa intermedia que gestiona la lógica de negocio entre la presentación y la base de datos, lo que mejora la modularidad, seguridad, escalabilidad y mantenimiento, aunque con mayor complejidad y demanda de recursos.
8. ¿Qué es el protocolo FTP y para qué se usa?
Las siglas de FTP significan File Transfer Protocol, que se traduce como Protocolo de Transferencia de Archivos. Como su nombre indica, se trata de un protocolo que permite transferir archivos directamente de un dispositivo a otro.
Este protocolo funciona entre ordenadores que estén conectados a una red TCP, que significa Transmission Control Protocol o Protocolo de control de transmisión. Este protocolo TCP da soporte a muchas tecnologías, entre ellas a Internet. Para que te hagas a la idea, la familia de protocolos que forman Internet se llama TCP/IP.
El funcionamiento de este protocolo es bastante sencillo. Simplemente, un ordenador A se conecta directamente a un ordenador B, y podrá ver los archivos que tiene disponible para compartir. Al verlos, simplemente podrá descargarlos directamente en el equipo que se ha conectado al otro.
Las conexiones FTP tienen una relación de cliente y servidor. Esto quiere decir que un ordenador tiene que estar configurado como servidor FTP, ese en el que se aloja el contenido, y luego tú te conectas a él como un cliente. En los ordenadores, los datos del protocolo FTP se envían a través de los puertos 20 y 21, que son los que están asignados en todos los equipos para llevar a cabo sus transferencias de archivos.

9. Menciona un ejemplo de cliente FTP y un ejemplo de servidor FTP.

Un ejemplo de cliente FTP es FileZilla, un programa gratuito y de código abierto que permite transferir archivos entre tu computadora y un servidor FTP. Es compatible con Windows, macOS y Linux, y ofrece una interfaz gráfica fácil de usar. 
Por otra parte, un ejemplo reconocido de servidor FTP es ProFTPD. Es un software libre y de código abierto, ampliamente utilizado en sistemas operativos tipo Unix, como Linux y macOS. ProFTPD destaca por su alta configurabilidad y seguridad, siendo una opción popular en entornos profesionales y servidores web .

10. ¿Qué diferencia existe entre FTP y SFTP?
Con FTP y SFTP, los archivos pueden cargarse y descargarse en el servidor. La mayoría de los clientes FTP, como FileZilla, admiten ambos protocolos.
FTP utiliza dos canales: un canal de comandos y un canal de datos. Esto corresponde a los puertos TCP 20 y 21. Sin embargo, su conexión no está cifrada. Por el contrario, SFTP con el puerto TCP 22 ofrece un único canal para la transmisión de datos, que también está protegido criptográficamente por SSH.
Otra diferencia es el tamaño de archivo permitido para las transferencias. Es de 4 GB para FTP y de 16 GB para SFTP.
En general, SFTP es el protocolo más seguro para la transferencia de datos entre un cliente y un servidor. Esto significa que la información sensible, como los archivos de configuración, también puede transferirse de forma cifrada. En cambio, con FTP, los hackers tienen la posibilidad de interceptar los datos en texto plano.
SFTP también admite la autenticación de clave pública, que ofrece un nivel de protección mayor que las contraseñas. Además, la resolución de problemas y la configuración del cliente y del servidor son más sencillas con SFTP.
11. Indica tres tipos de alojamiento web y explica brevemente en qué se diferencian.

Alojamiento compartido: En este tipo de hosting, varios sitios web comparten los mismos recursos de un servidor, como espacio de almacenamiento, memoria RAM y CPU. Es una opción económica y fácil de gestionar, ideal para sitios pequeños o personales que no requieren configuraciones avanzadas. Sin embargo, el rendimiento puede verse afectado si otros sitios en el mismo servidor consumen muchos recursos. Hostinger


Alojamiento VPS (Servidor Privado Virtual): Aunque varios usuarios comparten el mismo servidor físico, cada uno tiene su propio espacio virtualizado con recursos dedicados. Ofrece mayor control, personalización y rendimiento que el alojamiento compartido, siendo adecuado para sitios con mayor tráfico o necesidades específicas. Requiere conocimientos técnicos para su gestión. Hostinger


Alojamiento en la nube: Utiliza una red de servidores interconectados para alojar sitios web. Ofrece alta disponibilidad y escalabilidad, ya que si un servidor falla, otro puede asumir su carga. Es ideal para sitios con tráfico variable o que necesitan recursos flexibles. Hostinger


12. ¿Qué ventajas ofrece un servidor VPS frente a un alojamiento compartido?

Un servidor VPS (Servidor Privado Virtual) ofrece varias ventajas sobre el alojamiento compartido, especialmente para usuarios que requieren mayor control, rendimiento y escalabilidad. Según el artículo de Hostinger, las principales ventajas de un VPS frente a un hosting compartido son:
Acceso root completo: A diferencia del hosting compartido, donde el acceso al servidor está restringido, un VPS te otorga acceso total al sistema operativo. Esto te permite instalar y configurar cualquier software compatible, como servidores web personalizados, bases de datos o herramientas de desarrollo específicas Hostinger Help Center.


Recursos dedicados y rendimiento mejorado: En un VPS, aunque compartes un servidor físico con otros usuarios, cada uno dispone de una partición virtual con recursos asignados (CPU, RAM, almacenamiento). Esto garantiza un rendimiento más estable y predecible, incluso si otros sitios en el mismo servidor experimentan picos de tráfico Hostinger.


Mayor estabilidad y escalabilidad: El alojamiento VPS es más estable y rápido que el hosting compartido, ya que los recursos son dedicados y no se ven afectados por el tráfico de otros sitios. Además, es fácilmente escalable, lo que significa que puedes aumentar los recursos de tu servidor a medida que tu sitio web crece Hostinger.
Estas ventajas hacen que el VPS sea una opción ideal para sitios web con tráfico moderado a alto, aplicaciones personalizadas o proyectos que requieren un mayor nivel de control y flexibilidad.

13. Describe brevemente los componentes principales de una arquitectura web moderna.
Servidor
Es la máquina (física o virtual) que atiende las solicitudes de los clientes. Puede haber diferentes tipos: servidor web, de bases de datos, de correo, de archivos, etc. En arquitectura moderna muchos servidores son máquinas virtuales o contenedores en la nube.


Cliente
El equipo o sistema que pide servicios al servidor: un navegador web, una app móvil, etc. Puede ser “delgado” (que depende bastante del servidor, como una SPA) o “grueso” (que ejecuta lógica localmente).


Microservicios
En vez de tener una aplicación monolítica grande, se divide en servicios pequeños, independientes y débilmente acoplados, cada uno con su responsabilidad específica. Por ejemplo, un servicio para autenticación, otro para pagos, otro para generación de informes, etc.


Función en la nube (Serverless / Funciones sin servidor)
Permiten ejecutar fragmentos de lógica (“funciones”) sin gestionar servidores completos. Se activan en respuesta a eventos, lo que puede hacer que la arquitectura sea más eficiente y escalable.


Equilibrador de carga (Load Balancer)
Distribuye el tráfico entre múltiples servidores o instancias para mejorar rendimiento, escalabilidad y tolerancia a fallos. Puede ser hardware dedicado o basado en software; los “load balancers” en la nube son comunes.


API Gateway
Puerta de entrada unificada para las APIs del sistema. Gestiona rutas hacia diferentes servicios, controla versiones, aplica límites de tasa (rate limiting), monitoriza, autentica solicitudes, etc.


Cola de mensajes (Message Queue)
Componente para comunicación asincrónica entre microservicios. Permite desacoplar componentes, manejar fallos, procesar tareas en segundo plano y garantizar que los mensajes no se pierdan si un servicio receptor no está disponible momentáneamente.


CDN (Content Delivery Network)
Red de servidores geográficamente distribuidos que almacenan cachés de contenido estático (imágenes, estilos, scripts…) para servirlo lo más cerca posible del cliente, reduciendo latencia. También contribuye a la seguridad (por ejemplo mitigando ataques DDoS)


Base de datos
Componente donde se guarda la información persistente: usuarios, contenidos, sesiones, etc. Se puede usar distintos tipos dependiendo del uso: bases de datos SQL, NoSQL, clave‑valor, documentales, gráficas, etc.


Servicios auxiliares
Incluyen todas las funcionalidades que apoyan a la aplicación pero que no son la lógica de negocio central: autenticación, envío de correo, sistemas de monitorización, pipelines de integración/entrega continua (CI/CD), servicios de pago, búsqueda/indexación, etc. Pueden venir de terceros o estar construidos dentro de la infraestructura.

14. ¿Qué papel cumple el servidor de aplicaciones dentro de dicha arquitectura?
El servidor de aplicaciones es un componente clave dentro de una arquitectura web moderna. Su función principal es ejecutar la lógica del negocio de una aplicación y actuar como intermediario entre el cliente (por ejemplo, un navegador o app móvil) y otros componentes del sistema como bases de datos, APIs o servicios externos.
Funciones principales del servidor de aplicaciones:
Procesamiento de solicitudes del cliente: recibe las peticiones (por ejemplo, al hacer login o ver un producto), las interpreta y responde con los datos solicitados.
Ejecución de lógica del negocio: aplica reglas, condiciones y flujos que definen cómo funciona el sistema (por ejemplo, calcular descuentos, validar usuarios, etc.).
Interacción con la base de datos: accede, consulta, modifica o elimina datos almacenados.
Comunicación con otros servicios: puede consumir APIs, enviar mensajes a colas, invocar funciones en la nube, etc.


Gestión de sesiones, seguridad y autenticación: controla quién accede, mantiene la sesión activa y protege los datos del sistema.
15. ¿Qué software o paquete puedes usar para instalar Apache fácilmente en Windows?

Puedes usar paquetes o entornos tipo XAMPP o WampServer, que incluyen Apache junto con PHP, MySQL, etc., para instalar Apache fácilmente en Windows. 

16. ¿Qué carpeta suele contener los archivos del sitio web en una instalación de Apache en Windows (por ejemplo, con XAMPP)?

En una instalación de Apache en Windows, utilizando un paquete como XAMPP, la carpeta que suele contener los archivos del sitio web es htdocs. Esta carpeta se encuentra dentro del directorio de instalación de XAMPP, cuya ruta habitual es:

C:\xampp\htdocs
Dentro de esta carpeta se deben colocar los archivos del sitio web, como páginas HTML, scripts PHP, hojas de estilo CSS, imágenes, entre otros. Por ejemplo, si se crea una subcarpeta llamada misitio dentro de htdocs, el contenido será accesible desde el navegador mediante la siguiente dirección:
http://localhost/misitio
Esta carpeta actúa como el directorio raíz del servidor web Apache, es decir, el punto de inicio desde el cual se sirven los contenidos al navegador.
En caso de que se desee cambiar esta ubicación por otra carpeta personalizada, es posible modificar el archivo de configuración de Apache (httpd.conf), ubicado en:
C:\xampp\apache\conf\httpd.conf
Dentro de este archivo se deben actualizar las líneas correspondientes a DocumentRoot y <Directory> con la nueva ruta deseada.

17. Escribe el comando para instalar Apache en Ubuntu desde la terminal.

18. ¿Qué comando se usa para iniciar el servicio Apache en Ubuntu?


19. ¿En qué ruta se almacena normalmente la página web por defecto de Apache en Ubuntu?

20. ¿Qué es el protocolo SSH y cuál es su propósito principal?

SSH o Secure Shell, es un protocolo de administración remota que le permite a los usuarios controlar y modificar sus servidores remotos a través de Internet a través de un mecanismo de autenticación.
Proporciona un mecanismo para autenticar un usuario remoto, transferir entradas desde el cliente al host y retransmitir la salida de vuelta al cliente. El servicio se creó como un reemplazo seguro para el Telnet sin cifrar y utiliza técnicas criptográficas para garantizar que todas las comunicaciones hacia y desde el servidor remoto sucedan de manera encriptada.
21. ¿Qué comando se usa para conectarse a un servidor remoto mediante SSH?


22. Menciona una ventaja de usar autenticación mediante claves SSH frente a contraseñas

Una ventaja de usar autenticación mediante claves SSH frente a usar contraseñas es que las claves SSH son mucho más resistentes ante ataques de fuerza bruta e intercepción.
En otras palabras: es mucho más difícil (prácticamente inviable) que un atacante adivine o descifre tu clave privada mediante ataques automatizados, comparado con una contraseña que se puede probar repetidamente. 

