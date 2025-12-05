# **Informe Técnico – Virtualización y Contenedores**

**Módulo:** Despliegue de Aplicaciones Web
**Curso:** 2º DAW

---

# 1. Instalación de Ubuntu en VirtualBox

A continuación se describen los pasos realizados para instalar Ubuntu 24.04 LTS en una máquina virtual con VirtualBox.

## 1.1. Creación de la máquina virtual

Se creó una nueva máquina virtual con los parámetros recomendados:

* **Nombre:** Ubuntu-DAW2DAW
* **RAM:** 4096 MB
* **Disco virtual:** 50 GB (VDI, crecimiento dinámico)
* **Red:** NAT

<img width="1366" height="724" alt="1" src="https://github.com/user-attachments/assets/a44bb54d-7ee6-4b12-a41e-9a9b9b6c4017" />

<img width="1366" height="727" alt="2" src="https://github.com/user-attachments/assets/0fb1e9c5-8070-4701-8ed7-c3a53c78326f" />

## 1.2. Configuración de recursos de hardware

Se asignó memoria RAM, CPU y tamaño del disco virtual según los requisitos de la práctica.

<img width="1366" height="730" alt="3" src="https://github.com/user-attachments/assets/1553c0e2-dd78-4847-89bc-09dfe81672ab" />

<img width="1366" height="728" alt="4" src="https://github.com/user-attachments/assets/adab767f-4dae-49f0-86bf-db4afa795c15" />

---

## 1.3. Instalación del sistema operativo Ubuntu

Se inició la máquina utilizando la ISO oficial de Ubuntu 24.04 LTS y se completó el asistente de instalación gráfica.

<img width="1366" height="729" alt="5" src="https://github.com/user-attachments/assets/cbaf8726-bc9d-4656-ad20-33df84a26133" />

<img width="1366" height="726" alt="7" src="https://github.com/user-attachments/assets/67450778-0355-412e-9b95-c778e11d2f4a" />

## 1.4. Escritorio de Ubuntu después de la instalación

Una vez instalado Ubuntu, se accedió al escritorio para comprobar su funcionamiento.

<img width="1366" height="728" alt="10" src="https://github.com/user-attachments/assets/723f8ffe-6597-448e-aae2-b7729a77fe7c" />

---

# 2. Instalación de Docker en Ubuntu

## 2.1. Actualización del sistema

```bash
sudo apt update && sudo apt upgrade -y
```

## 2.2. Instalación de dependencias necesarias

```bash
sudo apt install ca-certificates curl gnupg -y
```

## 2.3. Instalación de Docker Desktop mediante script oficial

```bash
curl -fsSL https://get.docker.com | sudo sh
sudo apt install docker-desktop -y
```

## 2.4. Verificación de la instalación

### Comprobar versión:

```bash
docker --version
```

**Captura:**
![docker version](capturas/05_docker_version.png)

### Ejecutar contenedor de prueba:

```bash
docker run hello-world
```

**Captura:**
![hello world docker](capturas/06_docker_hello_world.png)

---

# 3. Contenedores Docker

## 3.1. Servidor web Nginx

Comando ejecutado:

```bash
docker run -d -p 8080:80 --name webserver nginx
```

Acceso en el navegador:
**[http://localhost:8080](http://localhost:8080)**

**Captura:**
![Nginx funcionando](capturas/08_nginx_navegador.png)

---

## 3.2. Servidor de aplicaciones Tomcat

Comando ejecutado:

```bash
docker run -d -p 8081:8080 --name appserver tomcat
```

Acceso en el navegador:
**[http://localhost:8081](http://localhost:8081)**

**Captura:**
![Tomcat funcionando](capturas/09_tomcat_navegador.png)

---

## 3.3. Verificación de contenedores activos

```bash
docker ps
```

**Captura:**
![docker ps](capturas/07_docker_ps.png)

---

# 4. Requerimientos mínimos para implantar una aplicación web

## 4.1. Requisitos de hardware

* CPU: 2 núcleos
* Memoria RAM: 4 GB mín.
* Almacenamiento: 50 GB
* Virtualización activada en BIOS

## 4.2. Requisitos de software

* VirtualBox
* Ubuntu 24.04
* Docker y contenedores Nginx/Tomcat

## 4.3. Infraestructura de red

* Modo NAT en la máquina virtual
* Puertos expuestos:

  * 8080 → Nginx
  * 8081 → Tomcat
* Acceso desde navegador del host

## 4.4. Configuración del servidor web y de aplicaciones

* **Nginx:** atiende peticiones HTTP y sirve contenido web.
* **Tomcat:** ejecuta aplicaciones Java y servlets.
* Ambos desplegados como contenedores Docker independientes.

## 4.5. Seguridad y mantenimiento

* Uso de imágenes oficiales desde Docker Hub
* Actualizaciones regulares:

  ```bash
  sudo apt update
  docker pull nginx
  docker pull tomcat
  ```
* Contenedores aislados sin privilegios extra
* No exponer puertos innecesarios

---

# 5. Conclusión

En esta práctica se ha realizado la instalación completa de un entorno virtualizado con Ubuntu y la configuración de Docker para desplegar un servidor web (Nginx) y un servidor de aplicaciones (Tomcat). Se han comprobado su funcionamiento mediante accesos desde el navegador y se han documentado los comandos y capturas correspondientes.
