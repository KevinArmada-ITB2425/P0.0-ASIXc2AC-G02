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

sudo apt update
sudo apt install bind9 bind9-utils bind9-dnsutils -y

## ⚙️ 3. Configuracion de reenvio (Forwarders)
Primero editamos el archivo `/etc/bind/named.conf.options`

![archivo_named.conf](/imagenes/bind_named.conf.options.png)

El servidor BIND permite la traducción de nombres para que ese tráfico se dirija al lugar correcto (función de servicio). Ambos son necesarios para una navegación web funcional.

## ⚙️ 4. Zona Interna G2

Primero editamos el fichero `/etc/bind/named.conf.local`

![archivo_.conf_local](/imagenes/bind_named_conf_local.png)

se ha creado esta zona para gestionar localmente los nombres de dominio de tu laboratorio/entorno y asociarlos con las direcciones IP internas de tus servidores y equipos

Creacion de Zona:

![archivo_.conf_local](/imagenes/db_G2_cat.png)

Este servidor DNS (BIND) está configurado para resolver nombres de dominio internos (como web.G2.cat) y, al mismo tiempo, actúa como un servidor de reenvío que envía todas las consultas externas a Google DNS (8.8.8.8)

## ⚙️ 5. Comprobacion de Zona

![archivo_.conf_local](/imagenes/db_G2_cat.png)

El router permite el tráfico bidireccional entre las redes internas (DMZ y Intranet) usando iptables, mientras que el DNS resuelve nombres de host internos (G2.cat)

## ⚙️ 6. Pruebas Funcionamiento

![funcionamiento_dig](/imagenes/funcionamiento_dig.png)

R-02 está lista para traducir nombres de dominio internos a IPs y encaminar el tráfico entre tus dos subredes de laboratorio.

Nslookup en el cliente

![nslookup](/imagenes/nslookup_cliente.png)

