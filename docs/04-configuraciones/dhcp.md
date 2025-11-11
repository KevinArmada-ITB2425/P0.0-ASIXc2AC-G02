, he instalado isc-dhcp-server -y, luego lo he modificado con el comando sudo nano /etc/default/isc-dhcp-server y hemos cambiado la interfaz INTERFACESV4="enp2s0" para indicar que interfaz va a dar servicio dhcp
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


