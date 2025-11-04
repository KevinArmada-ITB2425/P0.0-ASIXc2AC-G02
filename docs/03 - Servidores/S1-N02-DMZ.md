# 📄 Documentación Servidor S1-N02 (DMZ)

**Proyecto:** P0.0-ASIXc2AC-G02  
**Fecha:** 27 de octubre de 2025  
**Autor:** [Kevin Armada / Grupo 2]

---

## 🧭 Resumen y Rol

El servidor **S1-N02** está ubicado en la zona **DMZ** y actúa como servidor de acceso público. Aloja la aplicación web (Apache/PHP) y permite la gestión remota vía SSH y FTP.

## 📊 Información del Servidor

| Parámetro | Valor |
| :--- | :--- |
| **Hostname** | S1-N02 |
| **Sistema Operativo** | Ubuntu Server 22.04 LTS |
| **Red** | DMZ (192.168.120.0/24) |
| **IP** | 192.168.120.2/24 |
| **DNS** | 8.8.8.8, 8.8.4.4 |

---

## 🛠️ Servicios Instalados y Configuraciones Asociadas

La configuración detallada de cada servicio se encuentra en la carpeta **`configuraciones/`**.

### 1. Servidor Web (Apache + PHP)
- **Puertos:** 80 (HTTP), 443 (HTTPS)
- **DocumentRoot:** `/var/www/html`
- **Módulos PHP clave:** `php-mysql`, `libapache2-mod-php`
- **Documentación específica:** [Ver `configuraciones/web.md`](../04-configuraciones/web.md)

### 2. Servidor FTP (vsftpd)
- **Puertos:** 21 (Control), 20 (Data)
- **Puertos Pasivos:** 10000-10100
- **Modo:** `chroot` habilitado
- **Documentación específica:** [Ver `configuraciones/ftp.md`](../04-configuraciones/ftp.md)

### 3. Acceso Remoto (SSH)
- **Puerto:** 22
- **Documentación específica:** [Ver `configuraciones/router.md`](../04-configuraciones/router.md)

### 4. Conectividad y Red
- **Archivo de Configuración:** `/etc/netplan/00-installer-config.yaml`
- **Documentación específica:** [Ver `configuraciones/router.md`]()

---

## 🔥 Configuración de Firewall (UFW)

El firewall está configurado para permitir solo el tráfico esencial hacia la DMZ.

### Reglas Activas: