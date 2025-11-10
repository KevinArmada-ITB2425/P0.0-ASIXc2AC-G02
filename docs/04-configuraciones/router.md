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


## 3. Comandos Utilizados (IP Tables)
![Netplan de R-02](/imagenes/netfilter_R-02.webp)

Lo que hace el comando es para guardar las reglas actuales de el firewall para que sean persistentes

![Syslog.conf R-02](/imagenes/R-02_syslog.conf.png)

el comando para entrar al fichero es `sudo nano /etc/sysctl.conf` y veremos que estaria comentado `net.ipv4.ip_forward=1` y lo tenemos que descomentar

![ip tables R-02](/imagenes/iptables_R-02.webp)

este comando configura la traducción de direcciones de red (NAT) en tu router para dar salida a Internet a tus redes privadas