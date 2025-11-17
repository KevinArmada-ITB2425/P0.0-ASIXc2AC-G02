# 🌐 Configuración del Servidor Web (Apache + PHP) – S1-N02 (DMZ)

## 🧾 Descripción General

El servidor **S1-N02**, ubicado en la red **DMZ (`192.168.2.0/24`)**, aloja el **servicio web principal del proyecto P0.0-ASIXc2gC-Gnn**.  
Proporciona acceso **HTTP (puerto 80)** y **HTTPS (puerto 443)**, ejecutando aplicaciones en **PHP** que se conectan a la base de datos alojada en la **Intranet (S2-N02)**.

> ⚠️ La **DMZ (Zona Desmilitarizada)** es una red intermedia entre Internet y la Intranet, utilizada para alojar servicios públicos como web, FTP, DNS o correo, accesibles desde el exterior sin comprometer la red interna.

---

## ⚙️ 1️⃣ Resumen de la Instalación

| Componente | Versión / Detalle |
|------------|------------------|
| **Sistema Operativo** | Ubuntu Server 22.04 LTS |
| **Servidor Web** | Apache2 |
| **Lenguaje** | PHP 8.1 |
| **Rol** | Web server (Frontend + Backend PHP) |
| **Red** | DMZ – 192.168.2.0/24 |
| **IP del servidor** | 192.168.2.10 |
| **Puertos** | 80 (HTTP), 443 (HTTPS) |

---

## 🧩 2️⃣ Pasos de Instalación

| Paso | Comando | Descripción |
|------|---------|-------------|
| 1 | `sudo apt update && sudo apt upgrade -y` | Actualiza el sistema antes de instalar. |
| 2 | `sudo apt install apache2 -y` | Instala el servidor web Apache. |
| 3 | `sudo apt install php libapache2-mod-php -y` | Instala PHP y el módulo necesario para Apache. |
| 4 | `sudo apt install php-mysql php-cli php-mbstring -y` | Instala módulos PHP adicionales, incluyendo el conector MySQL. |
| 5 | `sudo systemctl restart apache2` | Reinicia el servicio Apache para aplicar cambios. |

---

---

### 🔍 Verificación rápida

![Verificación Apache y PHP funcionando](/imagenes/versiones_php_apache2.png)

![Verificación Apache y PHP funcionando](/imagenes/apache_status.png)

