# 🧭 Configuración del Router R-N02

## 🧩 1. Descripción General

El **Router R-N02** actúa como punto de conexión entre las tres redes principales del entorno de laboratorio:

| Interfaz | Red | Descripción |
|-----------|-----|-------------|
| **enp2s0** | DMZ | Red intermedia para servidores públicos (Web, FTP).           |
| **enp3s0** | Intranet | Red interna para equipos clientes                        |

El router se encarga de:
- Distribuir tráfico entre redes.
- Filtrar paquetes mediante **iptables**.
- Encaminamiento entre las dos redes.

---

## ⚙️ 2. Configuración de Red (Netplan)

📄 **Archivo:** `/etc/netplan/00-installer-config.yaml`

![Netplan de R-02](/imagenes/Netplan_R-02.webp)


## 3. Comandos Utilizados (IP Tables)

![Syslog.conf R-02](/imagenes/R-02_syslog.conf.png)

Al habilitar el reenvío de IP, le indicas al sistema operativo que debe aceptar paquetes que no están destinados a sí mismo y que, en su lugar, debe reenviarlos a la red de destino apropiada.

![ip_tables](/imagenes/ip_tables.png)

Este comando muestra las reglas que controlan el tráfico que intenta pasar a través de este servidor (reenvío de paquetes)

![Netplan de R-02](/imagenes/netfilter_R-02.webp)

Lo que hace el comando es para guardar las reglas actuales para que sean persistentes
