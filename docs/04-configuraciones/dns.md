# 🌐 Configuración del Servidor DNS (Bind9) – Router R-N02

## 🧭 1. Descripción General

El **Router R-N02**, además de gestionar el enrutamiento entre DMZ y Intranet , actúa como:

- **Servidor DNS para toda la red interna**
- **Servidor DHCP para la red de Clientes**

Este DNS permite:
- Resolver nombres internos del proyecto.
- Resolver dominios externos vía forwarders.
- Integrar DHCP + DNS en el mismo equipo.

| Elemento    | Detalle                      |
|-------------|------------------------------|
| Dispositivo | Router R-N02 (Ubuntu Server) |
| Servicio | Bind9                           |
| IP DNS (Intranet) | **192.168.120.0**      |
| IP DNS (DMZ) | **192.168.20.0**            |
| Redes atendidas | DMZ – Intranet           |
| Zonas | `G2.cat` |

---

## ⚙️ 2. Instalación de Bind9

```bash
sudo apt update
sudo apt install bind9 bind9-utils bind9-dnsutils -y

## ⚙️ 3. Instalación de Bind9