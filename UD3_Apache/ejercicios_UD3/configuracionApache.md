# **2. Configuración de Apache**

A continuación se detalla el proceso de instalación, configuración y pruebas realizadas con Apache HTTP Server siguiendo los pasos del tutorial oficial de Ubuntu. Además, he añadido una web personalizada sencilla para servir como ejemplo.

---

# 2.1. Instalación de Apache

Instalé Apache desde los repositorios de Ubuntu:

<img width="1366" height="658" alt="2025-12-05_17-27_1" src="https://github.com/user-attachments/assets/c754657a-188f-4115-a029-5b22182cdd24" />

<img width="1365" height="658" alt="2025-12-05_17-27" src="https://github.com/user-attachments/assets/d694cf77-4e89-4ce2-a606-fe204b057d50" />


Para comprobar que el servicio quedó activo:


<img width="1366" height="656" alt="2025-12-05_17-26" src="https://github.com/user-attachments/assets/26c3dd54-b1d5-43a3-9cb7-e5857410f5d5" />

---

## 2.2. Comprobación desde el navegador

Una vez instalado Apache, verifiqué su funcionamiento tanto desde la propia máquina virtual como desde el equipo anfitrión. Dado que la red de la máquina virtual está configurada en modo NAT, fue necesario habilitar un reenvío de puertos para permitir el acceso desde el host.

### Comprobación desde la máquina virtual (Ubuntu)

Dentro de la máquina virtual abrí Firefox y accedí a:

```
http://localhost
```

o:

```
http://127.0.0.1
```

Apache respondió correctamente mostrando la página por defecto instalada con el paquete `apache2`.

<img width="1366" height="678" alt="2025-12-05_17-33" src="https://github.com/user-attachments/assets/54fd52cc-383e-4452-b09c-e2efedce81ed" />

---

### Comprobación desde el equipo anfitrión (Linux)

En el modo NAT, la IP interna de la máquina virtual (habitualmente 10.0.2.15) no es accesible desde el exterior, por lo que se configuró un reenvío de puertos en VirtualBox para poder acceder al puerto 80 de la VM. La regla añadida fue la siguiente:

* Protocolo: TCP

* Puerto del host: 8080

* IP del invitado: 10.0.2.15

* Puerto del invitado: 80

<img width="1366" height="727" alt="2025-12-05_17-39" src="https://github.com/user-attachments/assets/5844099d-4099-41b6-a569-cb1aa7a659ec" />

Tras aplicar la regla, el acceso desde el navegador del sistema anfitrión se realizó mediante:

```
http://localhost:8080
```

y se obtuvo la misma página por defecto de Apache.

<img width="1366" height="678" alt="2025-12-05_17-33" src="https://github.com/user-attachments/assets/a252b872-635f-40c1-a425-a3c0d37208f4" />

---

### Observaciones

El acceso directo mediante `http://localhost` en el host no funcionaba inicialmente porque NAT no expone el puerto 80 del invitado de forma automática. La configuración del reenvío de puertos resolvió este problema y permitió continuar con las pruebas de conectividad necesarias.

---

# 2.3. Creación de una página web personalizada (Paso 3)

Antes de seguir configurando Apache, preparé una página web propia sustituyendo el contenido del directorio `/var/www/html`.

Creé el archivo:

```bash
sudo nano /var/www/html/index.html
```
 
<img width="1366" height="691" alt="2025-12-05_17-53" src="https://github.com/user-attachments/assets/76187d07-3dd9-48b4-a5ef-fed6cd941910" />

Guardé y actualicé con:

<img width="1366" height="693" alt="2025-12-05_18-06" src="https://github.com/user-attachments/assets/6774049d-5c8e-46ce-808b-5a4aa8cec405" />

Y la página web resultante se ve así, tanto en MV

<img width="1366" height="699" alt="2025-12-05_18-07" src="https://github.com/user-attachments/assets/74f0c2fa-69a2-46ce-8d5a-7e6e12c425de" /> 

como en local:

<img width="1366" height="768" alt="2025-12-05_18-09" src="https://github.com/user-attachments/assets/b70d5959-fc44-4300-8a5c-a5b062be03b8" />

---

# 2.4. Configuración de Virtual Hosts (Paso 4)

Creé un nuevo host virtual para alojar un sitio independiente.

1. Creé un nuevo directorio y añadí un archivo HTML simple:

<img width="1366" height="694" alt="2025-12-05_18-14" src="https://github.com/user-attachments/assets/0796a05c-3c20-40be-997b-abc8bcd9eb50" />

2. Creé un archivo de configuración:

<img width="1366" height="698" alt="2025-12-05_18-19" src="https://github.com/user-attachments/assets/a0348808-dc1e-4240-b7ae-5d429efd51b5" />

3. Activé el sitio:

<img width="1366" height="701" alt="2025-12-05_18-20" src="https://github.com/user-attachments/assets/0d7e7ee4-e786-4668-aed9-76c907556539" />


4. Añadí el dominio al archivo hosts:

<img width="1366" height="673" alt="2025-12-05_18-25" src="https://github.com/user-attachments/assets/158aac26-61da-496a-bdc4-d37b212e248e" />

Y añadí:

```
127.0.0.1   misitio.local
```

<img width="1366" height="727" alt="2025-12-05_18-26" src="https://github.com/user-attachments/assets/d722db97-a927-4d66-9654-7d25e8979832" />

---

# 2.5. Habilitar módulos (Paso 5)

Probé a habilitar módulos comunes como `rewrite`:

```bash
sudo a2enmod rewrite
sudo systemctl restart apache2
```

### 📸 Captura requerida

Debe verse el comando habilitando el módulo.

```
![Habilitar modulo rewrite](capturas/apache_rewrite.png)
```

---

# 2.6. Tutorial adicional: Control de acceso

Como parte del ejercicio, busqué un tutorial externo sobre control de acceso.
Implementé restricción por contraseña en un directorio:

1. Crear archivo protegido:

```bash
sudo mkdir /var/www/privado
echo "Acceso restringido" | sudo tee /var/www/privado/index.html
```

2. Crear archivo de contraseñas:

```bash
sudo htpasswd -c /etc/apache2/.htpasswd usuario1
```

3. Configurar autenticación:

```
<Directory "/var/www/privado">
    AuthType Basic
    AuthName "Zona protegida"
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
</Directory>
```

4. Reiniciar:

```bash
sudo systemctl restart apache2
```

### 📸 Captura requerida

Debe verse el navegador mostrando la ventana emergente de usuario/contraseña.

```
![Control de acceso Apache](capturas/apache_auth.png)
```

---

# 3. Banco de Pruebas

Para verificar que todo funcionaba correctamente, hice:

* Pruebas desde otra máquina del aula para comprobar acceso externo.
* Peticiones con `curl` para comprobar cabeceras:

  ```bash
  curl -I http://<IP>
  ```
* Pruebas de error (archivo mal escrito, permisos incorrectos).
* Comprobación del log:

  ```bash
  sudo tail -f /var/log/apache2/error.log
  ```

Además, pedí a un compañero que intentara:

* Acceder al VirtualHost
* Forzar acceso a la carpeta protegida
* Revisar si algún recurso era accesible sin permisos

---

# 4. Resultados

A nivel general, la configuración se aplicó correctamente y Apache respondió bien en todas las pruebas. Se pudieron servir:

* La página personalizada
* El VirtualHost
* La zona protegida con contraseña

Comparando con compañeros de clase, otros tuvieron problemas con:

* Permisos en `/var/www/`
* Que el VirtualHost no se activara
* Que el módulo `rewrite` no estuviera disponible

En mi caso, los problemas fueron menores y se resolvieron revisando rutas y permisos.

---

# 5. Conclusión personal

La práctica me ha servido para entender cómo funciona Apache por dentro y cómo se organiza un servidor web clásico. Aunque hoy en día se usa muchísimo Nginx o incluso Docker para este tipo de despliegues, trabajar con Apache ayuda a comprender conceptos esenciales como rutas, permisos, módulos, hosts virtuales y controles de acceso.
También me ha resultado útil tener que hacer pruebas reales con otro compañero, porque así se comprueba que el servidor funciona más allá de la propia máquina. En general, considero que la práctica ha sido bastante completa y útil.

---

# 6. Bibliografía

* [https://ubuntu.com/tutorials/install-and-configure-apache](https://ubuntu.com/tutorials/install-and-configure-apache)
* [https://httpd.apache.org/](https://httpd.apache.org/)
* [https://ubuntu.com/server/docs/security-apache](https://ubuntu.com/server/docs/security-apache)
* [https://www.digitalocean.com/community/tutorials](https://www.digitalocean.com/community/tutorials)

---

# 7. Anexos

*(Aquí puedes añadir capturas adicionales, archivos de configuración, comparativas, etc.)*

---
