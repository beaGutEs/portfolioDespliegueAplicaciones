# **Memoria del Proyecto: Introducción a Apache HTTP Server**

*(2º DAW – Despliegue de Aplicaciones Web)*

---

## **Resumen**

Este documento recoge la introducción y el análisis inicial sobre el uso del servidor web Apache dentro del módulo de Despliegue de Aplicaciones Web. El objetivo es comprender su función dentro de un entorno de desarrollo, revisar sus características principales y situarlo dentro del ecosistema actual de servidores web. Además, se explican las motivaciones que han llevado a utilizar Apache como punto de partida para las prácticas de la unidad.
*(Este resumen se completará y ajustará al finalizar toda la memoria.)*

---

## **Palabras clave**

Apache, Servidor Web, HTTP, Hosting, Virtual Hosts, Linux, Despliegue Web

---

## **Índice**

1. Introducción
   1.1 Contexto
   1.2 ¿Qué es Apache?
   1.3 Alternativas a Apache
   1.4 Motivación del proyecto

---

# 1. Introducción

## 1.1. Contexto

Este trabajo forma parte del módulo **Despliegue de Aplicaciones Web** del ciclo formativo de 2º DAW. El objetivo general es aprender a instalar, configurar y analizar diferentes tecnologías de servidor que se utilizan en entornos reales de desarrollo.
Las prácticas se realizan en un entorno controlado, normalmente sobre máquinas virtuales Linux o entornos preparados en clase, donde podemos experimentar con configuraciones sin afectar a sistemas de producción.

En esta primera parte, se ha seleccionado **Apache HTTP Server**, ya que es uno de los servidores web más utilizados y una referencia histórica dentro del despliegue de aplicaciones.

---

## 1.2. ¿Qué es Apache?

**Apache HTTP Server** es un servidor web de código abierto que permite publicar páginas web y gestionar peticiones HTTP de forma estable y segura. Fue creado a mediados de los 90, y durante muchos años ha sido el servidor más utilizado en Internet.
Aunque hoy existen alternativas más ligeras o más orientadas a microservicios, Apache sigue siendo muy común en entornos corporativos y educativos gracias a:

* Su alta estabilidad
* La gran cantidad de módulos disponibles
* Facilidad para configurar sitios y permisos
* Amplia documentación
* Funcionamiento multiplataforma

En esta práctica lo utilizaremos como punto de partida para entender cómo funciona un servidor web tradicional y cómo se configuran sus componentes básicos.

---

## 1.3. Alternativas a Apache

Aunque Apache sigue siendo muy utilizado, hoy en día existen otras herramientas que compiten en este ámbito. Algunas de las más conocidas son:

### **Nginx**

Un servidor web ligero y muy rápido, especialmente eficiente para servir contenido estático y gestionar muchas conexiones simultáneas. Es muy usado en servicios modernos y también como *reverse proxy*.

### **LiteSpeed**

Servidor web comercial con versión gratuita. Muy centrado en alto rendimiento y optimización para hosting compartido.

### **Caddy**

Servidor moderno con configuración minimalista y soporte automático de HTTPS mediante Let's Encrypt.

### **IIS (Internet Information Services)**

Servidor web integrado en Windows Server, usado principalmente en entornos corporativos con tecnologías de Microsoft.

---

## 1.4. Motivación del proyecto

El motivo de utilizar Apache en esta unidad es que permite comprender de forma clara cómo funciona un servidor web clásico y cómo se estructura un entorno de despliegue. Además:

* Es un estándar muy utilizado en hosting tradicional.
* Permite familiarizarse con conceptos como **document root**, **módulos**, **logs** y **virtual hosts**.
* Ofrece suficientes opciones de configuración para practicar, pero sin ser tan complejo como otros servidores orientados a alto rendimiento.
* Es adecuado para empezar antes de pasar a tecnologías más modernas como Nginx o contenedores Docker.

El objetivo final es que sepamos:

* Instalar un servidor Apache
* Habilitar módulos
* Configurar sitios virtuales
* Interpretar logs y errores
* Entender cómo se despliega una aplicación web en un servidor real

---

## Bibliografía (inicial)


* [https://httpd.apache.org/](https://httpd.apache.org/)
* [https://ubuntu.com/server/docs/web-servers-apache](https://ubuntu.com/server/docs/web-servers-apache)
* [https://www.nginx.com/](https://www.nginx.com/)
* [https://caddyserver.com/](https://caddyserver.com/)

