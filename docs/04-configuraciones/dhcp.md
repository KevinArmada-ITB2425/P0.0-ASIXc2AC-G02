# 🖧 Configuración del Servidor DHCP (isc-dhcp-server)

## 1️⃣ Descripción General

El servicio **DHCP** instalado en el Router/Servidor **R-N02** es el encargado de proporcionar direcciones IP dinámicas a los clientes conectados a la red **DMZ**, cuyo rango es `192.168.120.0/24`.

Este servidor asigna automáticamente **IP, máscara, gateway y DNS** a los equipos cliente que utilicen DHCP.

### 🔧 Parámetros principales

| Elemento                | Valor                         |
|------------------------|-------------------------------|
| Servicio DHCP          | isc-dhcp-server               |
| Red atendida           | DMZ – `192.168.120.0/24`      |
| Interfaz utilizada     | `enp2s0`                      |
| Rango de IPs asignadas | `192.168.120.100 – 192.168.120.200` |
| Gateway                | `192.168.120.1`               |
| Servidor DNS           | `192.168.120.1`               |

---

## 2️⃣ Instalación del Servicio

Actualizar repositorios y paquetes:


```sudo apt update && sudo apt upgrade -y```



Instalar isc-dhcp-server -y:


```sudo apt install isc-dhcp-server -y```

![Configuracion /etc/default/isc-dhcp-server](/imagenes/isc-dhcp-server_R-02.webp)

luego hemos modificado con el comando sudo `nano /etc/default/isc-dhcp-server` y hemos cambiado la interfaz INTERFACESv4="" y hemos puesto la enp2s0 para indicar que interfaz va a dar servicio dhcp

![dhcpd.conf ](/imagenes/dhcpd.conf_R-02.webp)

Primero hemos modificado en el archivo `/etc/dhcp/dhcpd.conf` y hemos creado un rango de la `192.168.120.100 - 192.168.120.200` y que el gateway es la ip del router 192.168.120.1 y hemos añadidos en option domain-name-server 192.168.120.1 que seria la ip del router;
Y para comprobar el cliente con un ip a y netplan en dhcp tendria la siguiente ip

![Netplan Cliente ](/imagenes/netplan_cliente.webp)

![IP a Cliente ](/imagenes/ipa_cliente.webp)

##  3. Estado del Servicio

`sudo systemctl restart isc-dhcp-server`

`sudo systemctl status bind9`

![Status Bind9](/imagenes/status_bind9.webp)