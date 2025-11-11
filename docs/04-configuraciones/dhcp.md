
luego hemos modificado sudo nano /etc/dhcp/dhcpd.conf
hemos añadidos en option domain-name-server 192.168.120.1;
y luego hemos creado un rango para que la interfaz enp2s0 al cliente le de una ip de ese rango
hemos hecho un sudo systemctl restar isc-dhcp-server y hemos comprobado el status 
y en el cliente podemos ver como le ha dado la ip 192.168.120.100

#  Configuración del Servidor DHCP (isc-dhcp-server)

##  1. Descripción General

El servicio **DHCP** (Dynamic Host Configuration Protocol) del **Router R-N02** se encarga de asignar direcciones IP dinámicas a los clientes conectados en la red **DMZ (192.168.120.0/24)**.

| Elemento | Valor |
|-----------|--------|
| Servicio | isc-dhcp-server |
| Red atendida | DMZ – 192.168.120.0/24 |
| Interfaz | enp2s0 |
| Rango de IPs asignadas | 192.168.120.100 – 192.168.120.200 |
| Servidor DNS | 192.168.120.1 |
| Gateway | 192.168.120.1 |

---

##  2. Instalación del Servicio

Actualizar el sistema y paquetes antes de instalar:


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