# 📝 Descripción de la Topología  
# Topología de Red - Proyecto P0.0  
**Proyecto:** P0.0-ASIXc2g2-G02  
**Router:** R-N02  
**Fecha:** 10/11/2025  

---

## 🏗️ Arquitectura General

El proyecto implementa una arquitectura de red **segmentada en 3 zonas independientes** para mejorar la seguridad, la escalabilidad y el control del tráfico:

1. **DMZ (Zona Desmilitarizada)** – `192.168.2.0/24`  
   - Aloja servicios públicos accesibles desde el exterior (HTTP/HTTPS, FTP, SSH).  
   - El router actúa como gateway con la IP **192.168.2.1**.

2. **Intranet (Red Interna)** – `192.168.20.0/24`  
   - Contiene los servicios internos críticos: MySQL, DNS, DHCP y monitorización.  
   - Su gateway es el router con la IP **192.168.20.1**.

3. **Clientes (Red de Usuarios)** – `10.0.0.0/24`  
   - Red destinada a los equipos cliente Windows y Linux.  
   - Utiliza DHCP gestionado desde el servidor interno.  
   - Gateway: **10.0.0.1**.

Todas las redes convergen en el **Router R-N02**, que actúa como:  
- **Punto de enrutamiento centralizado**  
- **Controlador del tráfico inter-redes**  
- **Gestor de accesos entre clientes, servidores y DMZ**

---

## 🌐 Topología Física

La infraestructura está organizada de la siguiente manera:

- **Router R-N02**  
  - Interconecta las tres redes: DMZ, Intranet y Clientes.  
  - Tiene una interfaz por cada segmento:  
    - `192.168.2.1` (DMZ)  
    - `192.168.20.1` (Intranet)  
    - `10.0.0.1` (Clientes)

- **Servidor Público (S1-N02)**  
  - Ubicado en la **DMZ** (`192.168.2.2`)  
  - Ejecuta servicios expuestos al exterior: web, FTP y SSH.

- **Servidor Interno (S2-N02)**  
  - Ubicado en la **Intranet** (`192.168.20.2`)  
  - Provee servicios esenciales internos:  
    - DNS  
    - DHCP
