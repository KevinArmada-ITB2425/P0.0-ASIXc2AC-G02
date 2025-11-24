# 📝 Descripción de la Topología  
# Topología de Red - Proyecto P0.0  
**Proyecto:** P0.0-ASIXc2g2-G02  
**Router:** R-N02  
**Fecha:** 10/11/2025  

---

## 🏗️ Arquitectura General

El proyecto implementa una arquitectura de red **segmentada en 3 zonas independientes** para mejorar la seguridad, la escalabilidad y el control del tráfico:

1. **DMZ (Zona Desmilitarizada)** – `192.168.20.0/24`  
   - Aloja servicios públicos accesibles desde el exterior (HTTP/HTTPS, FTP, SSH, Monitorizacoin y MySQL).  
   - El router actúa como gateway con la IP **192.168.20.1**.

2. **Intranet (Red Interna)** – `192.168.120.0/24`  
   - Contiene los servicios internos críticos: DNS y DHCP.  
   - Su gateway es el router con la IP **192.168.120.1**.

Todas las redes convergen en el **Router R-N02**, que actúa como:  
- **Punto de enrutamiento centralizado**  
- **Controlador del tráfico inter-redes**  
- **Gestor de accesos entre clientes, servidores y DMZ**

---

## 🌐 Topología Física

La infraestructura está organizada de la siguiente manera:

- **Router R-N02**  
  - Interconecta las dos redes: DMZ y Intranet.  
  - Tiene una interfaz por cada segmento:  
    - `192.168.20.1` (DMZ)  
    - `192.168.120.1` (Intranet)  

- **Servidor Público (S1-N02)**  
  - Ubicado en la **DMZ** (`192.168.20.2`)  
  - Ejecuta servicios expuestos al exterior: web, FTP y SSH.

- **Servidor Base de Datos (S2-N02)**  
  - Ubicado en la **DMZ** (`192.168.20.5`)  
  - Provee servicios esenciales internos:  
    - Monitoraje  
    - MySQL

- **Routert (R-02)**  
  - Ubicado en la **Intranet** (`192.168.20.1 - 192.168.120.1`)  
  - Provee servicios esenciales internos:  
    - DHCP  
    - DNS