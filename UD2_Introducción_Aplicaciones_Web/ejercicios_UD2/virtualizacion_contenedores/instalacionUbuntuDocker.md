# Informe Técnico – Virtualización y Contenedores

**Módulo:** Despliegue de Aplicaciones Web
**Curso:** 2º DAW

---

# 1. Instalación de Ubuntu en VirtualBox

En esta parte de la práctica he instalado **Ubuntu 24.04.3 LTS** dentro de una máquina virtual creada con VirtualBox. A continuación explico los pasos que he seguido.

---

## 1.1. Creación de la máquina virtual

Primero creé una nueva máquina virtual con estos parámetros:

* **Nombre:** Ubuntu-DAW2DAW
* **Tipo:** Linux
* **Versión:** Ubuntu (64-bit)
* **RAM:** 4096 MB
* **Disco:** 50 GB (VDI, expansión dinámica)
* **Red:** NAT


<img width="1366" height="724" alt="1" src="https://github.com/user-attachments/assets/a44bb54d-7ee6-4b12-a41e-9a9b9b6c4017" />

<img width="1366" height="727" alt="2" src="https://github.com/user-attachments/assets/0fb1e9c5-8070-4701-8ed7-c3a53c78326f" />

---

## 1.2. Configuración de recursos de hardware

Ajusté la memoria RAM, los procesadores, el almacenamiento y la red antes de iniciar la instalación.

<img width="1366" height="730" alt="3" src="https://github.com/user-attachments/assets/1553c0e2-dd78-4847-89bc-09dfe81672ab" />

<img width="1366" height="728" alt="4" src="https://github.com/user-attachments/assets/adab767f-4dae-49f0-86bf-db4afa795c15" />

---

## 1.3. Instalación de Ubuntu

Arranqué la máquina con la ISO de **Ubuntu 24.04.3 LTS** y seguí el asistente de instalación hasta completarla.

<img width="1366" height="729" alt="5" src="https://github.com/user-attachments/assets/cbaf8726-bc9d-4656-ad20-33df84a26133" />

<img width="1366" height="726" alt="7" src="https://github.com/user-attachments/assets/67450778-0355-412e-9b95-c778e11d2f4a" />

---

## 1.4. Escritorio tras la instalación

Cuando terminó la instalación y reinicié la máquina, comprobé que Ubuntu arrancaba correctamente.

<img width="1366" height="728" alt="10" src="https://github.com/user-attachments/assets/723f8ffe-6597-448e-aae2-b7729a77fe7c" />

---

# 2. Instalación de Docker en Ubuntu

Después instalé Docker Desktop dentro de Ubuntu para poder trabajar con contenedores.

## 2.1. Actualizar paquetes del sistema

```bash
sudo apt update && sudo apt upgrade -y
```

## 2.2. Instalar dependencias necesarias

```bash
sudo apt install ca-certificates curl gnupg -y
```

## 2.3. Instalar Docker usando el script oficial

```bash
curl -fsSL https://get.docker.com | sudo sh
sudo apt install docker-desktop -y
```

---

## 2.4. Comprobación del funcionamiento

### Versión de Docker

```bash
docker --version
```

### 📸 Captura necesaria

Debe verse el comando y la versión instalada de Docker.

```
![Docker versión](capturas/05_docker_version.png)
```

### Contenedor de prueba

```bash
docker run hello-world
```

### 📸 Captura necesaria

Debe verse el mensaje “Hello from Docker!”.

```
![Hello world Docker](capturas/06_docker_hello_world.png)
```

---

# 3. Creación y ejecución de contenedores

## 3.1. Servidor web con Nginx

Comando:

```bash
docker run -d -p 8080:80 --name webserver nginx
```

Acceso desde el navegador:
**[http://localhost:8080](http://localhost:8080)**

### 📸 Captura necesaria

Debe verse la página de bienvenida de Nginx.

```
![Nginx funcionando](capturas/08_nginx_navegador.png)
```

---

## 3.2. Servidor de aplicaciones con Tomcat

Comando:

```bash
docker run -d -p 8081:8080 --name appserver tomcat
```

Acceso desde el navegador:
**[http://localhost:8081](http://localhost:8081)**

### 📸 Captura necesaria

Debe verse la página inicial de Tomcat con el logo del gato.

```
![Tomcat funcionando](capturas/09_tomcat_navegador.png)
```

---

## 3.3. Verificar contenedores activos

Comando:

```bash
docker ps
```

### 📸 Captura necesaria

Debe verse que están corriendo los contenedores:

* `webserver` (nginx)
* `appserver` (tomcat)

```
![docker ps](capturas/07_docker_ps.png)
```

---

# 4. Requerimientos mínimos para desplegar una aplicación web

A partir de lo trabajado en la práctica, estos serían los requisitos básicos para montar una aplicación web usando este tipo de entorno.

## 4.1. Requisitos de hardware

* CPU: mínimo 2 núcleos
* RAM: mínimo 4 GB
* Disco: 50 GB
* Virtualización habilitada (BIOS/UEFI)

## 4.2. Requisitos de software

* VirtualBox
* Ubuntu 24.04.3 LTS
* Docker Desktop
* Imágenes oficiales: Nginx y Tomcat

## 4.3. Infraestructura de red

* La VM funciona con NAT
* Puertos expuestos:

  * 8080 para Nginx
  * 8081 para Tomcat

## 4.4. Configuración del entorno

* Nginx sirve contenido web estático
* Tomcat ejecuta aplicaciones Java
* Cada servicio va en su propio contenedor

## 4.5. Seguridad y mantenimiento

* Usar imágenes oficiales y actualizadas
* Actualizar el sistema periódicamente
* Mantener los contenedores aislados
* No abrir puertos innecesarios

---

# 5. Conclusión

En esta práctica he podido instalar Ubuntu 24.04.3 LTS en una máquina virtual, instalar Docker dentro del sistema y poner en marcha dos servicios diferentes (Nginx y Tomcat) mediante contenedores. Ambos funcionaron correctamente y pude acceder a ellos desde el navegador del host. La práctica me ha servido para entender mejor cómo funciona la virtualización y cómo facilita Docker el despliegue de servicios.