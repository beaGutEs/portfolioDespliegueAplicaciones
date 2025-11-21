# Política de seguridad del repositorio

## 1. Archivos excluidos del control de versiones

En este repositorio se utiliza un archivo `.gitignore` para evitar que determinados ficheros se suban al control de versiones. Los principales tipos de archivos excluidos son:

- **Entornos virtuales de Python (venv, .venv, env):** contienen dependencias y binarios específicos del entorno local. No deben compartirse porque:
  - Ocupan mucho espacio.
  - Cada desarrollador puede tener un entorno diferente y se debe reproducir a partir de `requirements.txt` o documentación, no versionarse directamente.

- **Archivos de configuración local y credenciales (`.env`, `*.secret`, `*.key`, `*.pem`, `config.local.*`):**
  - Pueden incluir contraseñas, tokens de acceso, claves privadas u otros datos sensibles.
  - Subir estos archivos a un repositorio público o compartido supone un riesgo de seguridad, ya que cualquiera con acceso al repositorio podría utilizar esa información de forma indebida.
  - La configuración sensible debe mantenerse en ficheros locales y gestionarse mediante variables de entorno o gestores de secretos.

- **Archivos generados automáticamente (carpeta `site/` de MkDocs, `dist/`, `build/`):**
  - Son artefactos de compilación o generación, que pueden reconstruirse en cualquier momento a partir del código fuente.
  - Versionarlos genera ruido en el historial de Git y aumenta innecesariamente el tamaño del repositorio.

- **Archivos temporales, de caché y de log (`__pycache__/`, `*.pyc`, `*.log`, `*.tmp`):**
  - No forman parte del código fuente ni de la documentación.
  - Su contenido no es relevante para el control de versiones y puede contener información de depuración que no debe compartirse.

- **Archivos del sistema y del entorno de desarrollo (`.DS_Store`, `Thumbs.db`, `.vscode/`, `.idea/`):**
  - Son específicos del sistema operativo o del editor/IDE utilizado.
  - No aportan valor al proyecto y pueden causar conflictos innecesarios entre desarrolladores.

En resumen, estos archivos se excluyen del control de versiones para proteger información sensible, reducir el tamaño del repositorio y evitar conflictos derivados de configuraciones locales.

## 2. Accesibilidad y permisos del repositorio

El repositorio está alojado en GitHub y puede compartirse con otros desarrolladores añadiéndolos como colaboradores. A nivel de permisos, se distinguen principalmente los siguientes niveles:

- **Solo lectura (Read):**
  - Permite clonar el repositorio y consultar el historial.
  - No permite realizar cambios directos sobre la rama principal ni hacer `push`.
  - Es adecuado para:
    - Usuarios que solo necesitan revisar el código o la documentación.
    - Perfiles de auditoría o supervisión.

- **Escritura (Write):**
  - Permite crear ramas, subir cambios (`push`) y abrir *pull requests*.
  - No debería permitir borrar el repositorio ni modificar su configuración principal.
  - Es el nivel de permiso recomendado para desarrolladores que participan activamente en el proyecto.

- **Administrador (Admin):**
  - Permite cambiar la configuración del repositorio, gestionar colaboradores y permisos, proteger ramas e incluso eliminar el repositorio.
  - Este nivel debe reservarse para:
    - El responsable del proyecto.
    - Miembros con funciones de coordinación o mantenimiento del repositorio.

En un equipo de desarrollo típico, lo más habitual es:
- Rol de desarrollador: permiso de **escritura**.
- Rol de responsable técnico o coordinador: permiso de **administrador**.
- Usuarios que solo consultan la documentación: permiso de **lectura**.

## 3. Buenas prácticas de seguridad

Para proteger la documentación y el código en este repositorio se recomienda seguir las siguientes medidas:

- **Uso de ramas protegidas:**
  - Proteger la rama principal (por ejemplo, `main`) para impedir que se hagan `push` directos sin revisión.
  - Requerir *pull requests* para incorporar cambios a la rama principal.

- **Revisión de *pull requests*:**
  - Establecer al menos una revisión obligatoria antes de aprobar un cambio.
  - Revisar especialmente modificaciones que afecten a configuración, dependencias o documentación sensible.

- **Gestión segura de credenciales:**
  - No almacenar contraseñas ni tokens en el repositorio.
  - Utilizar ficheros `.env` locales que no se suben a Git.
  - Emplear gestores de secretos o variables de entorno en entornos de producción.

- **Control de dependencias:**
  - Mantener actualizadas las dependencias del proyecto.
  - Revisar periódicamente posibles vulnerabilidades en librerías de terceros.

## 4. Recuperación del repositorio y copias de seguridad

Para garantizar la recuperación del proyecto en caso de pérdida de datos o errores graves se contemplan las siguientes medidas:

- **Uso de GitHub como copia remota:**
  - El repositorio remoto en GitHub actúa como copia de seguridad del repositorio local.
  - En caso de pérdida del entorno local, el proyecto puede recuperarse clonando de nuevo:
    ```bash
    git clone <url-del-repositorio>
    ```

- **Historial de cambios y reversión:**
  - Git conserva el historial completo de los *commits* realizados.
  - Si se introduce un error grave, es posible:
    - Volver a un *commit* anterior mediante `git checkout`.
    - Revertir cambios concretos utilizando `git revert`.

- **Uso de ramas para experimentación:**
  - Los cambios de prueba deben realizarse en ramas independientes.
  - Solo se integran en la rama principal una vez revisados y validados, reduciendo así el riesgo de romper la versión estable del proyecto.

- **Exportación y clonación adicional:**
  - Es posible mantener copias adicionales del repositorio en otras máquinas o dispositivos externos.
  - En proyectos críticos, puede ser recomendable disponer de copias fuera de GitHub (por ejemplo, en otro servidor o almacenamiento seguro).

Estas medidas, combinadas con el uso correcto de `.gitignore` y de los permisos en GitHub, ayudan a mantener el proyecto seguro, trazable y recuperable ante posibles incidencias.

## Accesibilidad del repositorio y niveles de permiso

El repositorio incluye un colaborador añadido a través de la sección “Manage access” de GitHub. En los repositorios personales, GitHub asigna automáticamente a los colaboradores el rol de “Collaborator”, que corresponde internamente a un permiso de escritura (“Write”). En esta modalidad, la interfaz no permite modificar los roles del colaborador ni asignar permisos de lectura o administración. Las únicas acciones disponibles desde la interfaz son añadir nuevos colaboradores o eliminarlos.

Aunque GitHub no muestre explícitamente el nivel de permiso asignado, la documentación oficial indica que el rol “Collaborator” en repositorios personales implica acceso de escritura. Por tanto, el colaborador puede realizar acciones como clonar el repositorio, crear nuevas ramas y subir cambios mediante `git push`, siempre que no se modifique la configuración del repositorio o las reglas de protección de ramas.

Para otros niveles de permiso (Read, Maintain, Admin), GitHub requiere organizaciones o repositorios con funcionalidades avanzadas, por lo que dichos roles no están disponibles en este tipo de repositorio personal. Aun así, se ha revisado la estructura de permisos desde la interfaz de GitHub y se ha documentado su significado a nivel teórico, con el fin de comprender qué nivel de permiso sería adecuado para cada tipo de rol dentro de un equipo de desarrollo.
