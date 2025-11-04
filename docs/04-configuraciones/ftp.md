# 📁 Configuración del Servidor FTP (vsftpd) - S1-N02 (DMZ)

## 🧩 1. Resumen y Propósito

El servidor **S1-N02**, ubicado en la red **DMZ (192.168.2.0/24)**, ejecuta el servicio **vsftpd (Very Secure FTP Daemon)**.  
Este servicio permite la **transferencia segura de archivos** hacia el servidor web para gestionar la aplicación y otros contenidos del proyecto.

| Parámetro | Valor |
|------------|--------|
| Servicio | vsftpd |
| Rol | Transferencia de archivos (gestión de contenidos web) |
| Puerto de Control | TCP/21 |
| Puerto de Datos | TCP/20 (activo) |
| Puertos Pasivos | TCP/10000–10100 |
| Usuario local | `bchecker` |
| IP Servidor | `192.168.2.10` |

---

## ⚙️ 2. Pasos de Instalación
![Instalacion servicio vsftpd](/imagenes/instalar_vsftpd.png)
### Actualizar el sistema
```bash
sudo apt update
sudo apt upgrade -y
