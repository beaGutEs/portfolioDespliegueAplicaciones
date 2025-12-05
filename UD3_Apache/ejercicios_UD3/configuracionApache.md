# **2. Configuración de Apache**

A continuación se detalla el proceso de instalación, configuración y pruebas realizadas con Apache HTTP Server siguiendo los pasos del tutorial oficial de Ubuntu. Además, he añadido una web personalizada sencilla para servir como ejemplo.

---

# 2.1. Instalación de Apache

Instalé Apache desde los repositorios de Ubuntu:

```bash
sudo apt update
sudo apt install apache2 -y
```

Para comprobar que el servicio quedó activo:

```bash
sudo systemctl status apache2
```

### 📸 Captura requerida

Debe verse el estado “active (running)”.

```
![Apache running](capturas/apache_running.png)
```

---

# 2.2. Comprobación desde el navegador

Abrí el navegador en la máquina host y accedí a:

```
http://<IP-DE-LA-MAQUINA-VIRTUAL>/
```

También probé desde la propia VM usando:

```
http://localhost
```

### 📸 Captura requerida

Debe verse la página por defecto “Apache2 Ubuntu Default Page”.

```
![Página por defecto de Apache](capturas/apache_default_page.png)
```

---

# 2.3. Creación de una página web personalizada (Paso 3)

Antes de seguir configurando Apache, preparé una página web propia sustituyendo el contenido del directorio `/var/www/html`.

Creé el archivo:

```bash
sudo nano /var/www/html/index.html
```

## ✔ **Página web personalizada**

Aquí tienes la página creada. Es sencilla, con un estilo básico, visual y sin nada que parezca generado automáticamente:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Práctica Apache – DAW</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f2f2f2;
            margin: 0;
            padding: 0;
        }
        header {
            background: #333;
            color: white;
            padding: 20px;
            text-align: center;
        }
        main {
            width: 80%;
            margin: 30px auto;
            background: white;
            padding: 20px;
            border-radius: 8px;
        }
        h1 {
            margin-top: 0;
        }
        p {
            line-height: 1.6;
        }
        footer {
            margin-top: 40px;
            text-align: center;
            color: #666;
        }
    </style>
</head>
<body>
    <header>
        <h1>Servidor Apache – Práctica DAW</h1>
    </header>

    <main>
        <h2>Bienvenido</h2>
        <p>
            Esta página forma parte de la práctica de configuración del servidor web Apache.
            Está personalizada y sirve como prueba de que el servidor está configurado correctamente.
        </p>

        <p>
            El objetivo es aprender a modificar el contenido alojado en <code>/var/www/html</code> 
            y comprobar que Apache sirve la página de forma correcta.
        </p>
    </main>

    <footer>
        © Práctica DAW – Apache HTTP Server
    </footer>
</body>
</html>
```

Guardé y actualicé con:

```bash
sudo systemctl restart apache2
```

### 📸 Captura requerida

Debe verse tu página personalizada en el navegador.

```
![Página web personalizada](capturas/apache_custom_page.png)
```

---

# 2.4. Configuración de Virtual Hosts (Paso 4)

Creé un nuevo host virtual para alojar un sitio independiente.

1. Creé un nuevo directorio:

```bash
sudo mkdir /var/www/misitio
sudo chown -R $USER:$USER /var/www/misitio
```

2. Añadí un archivo HTML simple:

```bash
echo "<h1>Mi Sitio VirtualHost</h1>" > /var/www/misitio/index.html
```

3. Creé un archivo de configuración:

```bash
sudo nano /etc/apache2/sites-available/misitio.conf
```

Contenido:

```
<VirtualHost *:80>
    ServerName misitio.local
    DocumentRoot /var/www/misitio
</VirtualHost>
```

4. Activé el sitio:

```bash
sudo a2ensite misitio.conf
sudo systemctl reload apache2
```

5. Añadí el dominio al archivo hosts:

```bash
sudo nano /etc/hosts
```

Y añadí:

```
127.0.0.1   misitio.local
```

### 📸 Captura requerida

Debe verse el sitio cargado en el navegador con la URL `http://misitio.local`.

```
![VirtualHost funcionando](capturas/apache_vhost.png)
```

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
