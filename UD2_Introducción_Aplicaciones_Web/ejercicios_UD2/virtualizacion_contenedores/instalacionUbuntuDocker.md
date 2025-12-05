# Informe Técnico – Virtualización y Contenedores

**Módulo:** Despliegue de Aplicaciones Web
**Curso:** 2º DAW

---

# 1. Instalación de Ubuntu en VirtualBox

En esta parte de la práctica he instalado **Ubuntu 24.04.3 LTS** dentro de una máquina virtual creada con VirtualBox. A continuación explico los pasos que he seguido.

---

## 1.1. Creación de la máquina virtual

Primero creé una nueva máquina virtual con estos parámetros mínimos, yo los he adaptado a mis necesidades:

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

<img width="1366" height="726" alt="11" src="https://github.com/user-attachments/assets/035249e0-66a5-4a14-98b1-2d8af9b7ef45" />

<img width="1366" height="729" alt="12" src="https://github.com/user-attachments/assets/5fce348a-c638-4e1b-9a37-630740befd3d" />

<img width="1366" height="727" alt="13" src="https://github.com/user-attachments/assets/5b2b6aa2-5dab-4524-8f2a-13f3effbf3fe" />

<img width="1366" height="707" alt="14" src="https://github.com/user-attachments/assets/9764f9b9-8009-4485-93e8-537a7a2f22a0" />

<img width="1366" height="727" alt="15" src="https://github.com/user-attachments/assets/19b87ed4-f881-453e-b3d5-4046e4282a02" />

<img width="932" height="319" alt="15_2" src="https://github.com/user-attachments/assets/7f40c940-d219-45fe-8b0c-e01fc9081503" />

<img width="1366" height="729" alt="16" src="https://github.com/user-attachments/assets/75238fa4-c310-4145-994a-01012ddb23b8" />

## 2.2. Instalar dependencias necesarias

<img width="1366" height="731" alt="17" src="https://github.com/user-attachments/assets/fc2656a8-b971-4395-b75a-4885728b4a1d" />

<img width="1366" height="730" alt="18" src="https://github.com/user-attachments/assets/65120391-200b-4ad2-8fef-fd219eed495c" />

<img width="1366" height="726" alt="19" src="https://github.com/user-attachments/assets/bf8ed04a-af03-451b-b196-9c9c2aad3496" />

## 2.3. Instalar Docker usando el script oficial

<img width="1366" height="730" alt="20" src="https://github.com/user-attachments/assets/64e741c0-28e6-469d-a0ff-e9ea98b218ba" />

<img width="1366" height="732" alt="21" src="https://github.com/user-attachments/assets/fe10175f-00e2-40f6-86f4-88088c44f160" />

## 2.4. Comprobación del funcionamiento

<img width="1366" height="730" alt="22" src="https://github.com/user-attachments/assets/2872a726-be41-43a9-862c-f445dcc3ba62" />

---

# 3. Creación y ejecución de contenedores

## 3.1. Servidor web con Nginx

<img width="1218" height="628" alt="24" src="https://github.com/user-attachments/assets/7e46551f-a5c4-4567-919f-5d3d9d792600" />

## 3.2. Servidor de aplicaciones con Tomcat

<img width="1077" height="625" alt="26" src="https://github.com/user-attachments/assets/9af2cefd-b4ed-4980-8ab3-5851d3d274c5" />

## 3.3. Verificar contenedores activos

<img width="1366" height="731" alt="27" src="https://github.com/user-attachments/assets/41fc4284-42e0-4016-8573-e935b052bb35" />

<img width="1366" height="262" alt="28" src="https://github.com/user-attachments/assets/d71684e6-fb94-4cf9-b5d5-7f6b2122cf5c" />

<img width="1366" height="727" alt="29" src="https://github.com/user-attachments/assets/d155b184-d52d-4c9c-aec6-9948b9318c14" />

<img width="1366" height="730" alt="30" src="https://github.com/user-attachments/assets/cd173bc4-d76c-4d0d-9ea1-5c918b206ff2" />

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
