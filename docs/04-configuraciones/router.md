# 🧭 Configuración del Router R-N02

## 🧩 1. Descripción General

El **Router R-N02** actúa como punto de conexión entre las tres redes principales del entorno de laboratorio:

| Interfaz | Red | Descripción |
|-----------|-----|-------------|
| **enp1s0** | WAN | Conexión hacia Internet o red externa. |
| **enp2s0** | DMZ | Red intermedia para servidores públicos (Web, FTP). |
| **enp3s0** | Clientes / Intranet | Red interna para equipos del aula o usuarios. |

El router se encarga de:
- Distribuir tráfico entre redes.
- Filtrar paquetes mediante **iptables**.
- Aplicar **NAT (enmascaramiento)** para permitir salida a Internet.
- Encaminamiento entre las tres subredes.

---

## ⚙️ 2. Configuración de Red (Netplan)

📄 **Archivo:** `/etc/netplan/00-installer-config.yaml`

![Netplan de R-02](/imagenes/Netplan_R-02.webp)