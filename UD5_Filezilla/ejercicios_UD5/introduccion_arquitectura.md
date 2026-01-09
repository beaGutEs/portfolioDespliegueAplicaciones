# Actividad 1: Introducción y arquitectura de FileZilla Server

## 1) FTP vs FTPS vs SFTP (conceptual)

| Protocolo | ¿Qué es? | Cifrado | Puerto típico | Nota clave |
|---|---|---|---:|---|
| **FTP** | Protocolo clásico de transferencia de archivos | No | **21** (control) | Usa **dos canales**: control y datos |
| **FTPS** | **FTP + TLS/SSL** (capa de seguridad) | Sí (TLS) | **21** (explícito) / **990** (implícito) | Es “FTP seguro”, no es SSH |
| **SFTP** | Transferencia de archivos sobre **SSH** (subsystem) | Sí (SSH) | **22** | No es FTP: comandos y funcionamiento distintos |

> En la práctica: **FileZilla Server** se usa sobre todo para **FTP/FTPS**.  
> **SFTP** normalmente se ofrece con un **servidor SSH** (p. ej. OpenSSH).

---

## 2) Arquitectura cliente–servidor (modelo FTP/FTPS)

En FTP/FTPS siempre hay:

- **Cliente FTP** (FileZilla Client, WinSCP, etc.)
- **Servidor FTP** (FileZilla Server)
- **Dos conexiones TCP distintas**:
  - **Canal de control**: se mantiene abierto durante la sesión (login, comandos).
  - **Canal de datos**: se abre y se cierra para cada transferencia/listado.

### ¿Qué hace cada canal?

- **Control (comandos)**
  - Autenticación: `USER`, `PASS`
  - Navegación: `CWD`, `PWD`
  - Operaciones: `LIST`, `RETR`, `STOR`, `DELE`
- **Datos (contenido)**
  - Listado de carpetas (`LIST`)
  - Descargar (`RETR`)
  - Subir (`STOR`)

---

## 3) Puertos implicados

### FTP / FTPS (explícito)
- **Puerto 21/TCP** → **Control**
- **Datos**
  - **Modo activo**: el servidor inicia la conexión de datos **desde el puerto 20/TCP** hacia el cliente.
  - **Modo pasivo**: el servidor “ofrece” un **puerto del rango pasivo** y el cliente se conecta a él.

### Rango pasivo (PASV)
- Es un **rango configurable** en el servidor (ejemplo típico: `50000–51000`).
- En escenarios con NAT/firewall es lo más común, porque **el cliente siempre inicia las conexiones**.

---

## 4) Esquema del flujo de conexión (control + datos)

### 4.1. Flujo general (idea base)

1. **Control**: Cliente → Servidor (TCP **21**).
2. Negociación del modo de datos: `PORT` (activo) o `PASV` (pasivo).
3. **Datos**: se abre una 2ª conexión TCP para `LIST/RETR/STOR`.
4. Se cierra la conexión de datos; el control puede seguir abierto.

---

## 4.2. Modo activo (ACTIVE)

**Resumen**:  
El cliente abre el canal de control al servidor, pero el servidor inicia la conexión de **datos hacia el cliente**.

- Control: Cliente → Servidor **21**
- Datos: Servidor (desde **20**) → Cliente (puerto que el cliente “escucha”)

```mermaid
sequenceDiagram
    participant C as Cliente FTP
    participant S as Servidor FTP (FileZilla Server)

    C->>S: TCP Control a puerto 21
    C->>S: USER/PASS (comandos)
    C->>S: PORT <IP_cliente:puerto_cliente> (cliente queda "a la escucha")
    C->>S: LIST / RETR / STOR
    S->>C: TCP Datos desde puerto 20 -> puerto_cliente
    S-->>C: Envío/recepción de datos (listado/archivo)
    S->>C: Cierra canal de datos (al terminar)
    C->>S: QUIT (opcional)
