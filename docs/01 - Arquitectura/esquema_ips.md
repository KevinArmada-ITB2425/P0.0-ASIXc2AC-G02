# 📘 Tabla de Direccionamiento IP  
**Proyecto:** P0.0-ASIXc2A-G02  
**Equipo:** R-N02  
**Arquitectura:** 2 Servidores (DMZ + Intranet)  
**Fecha de creación:** 14/10/25  
**Última actualización:** 14/10/25  

---

## 1️⃣ Rangos de red definidos

| Red        | Rango de Red   | Máscara        | Gateway      |
|------------|----------------|----------------|--------------|
| DMZ        | 192.168.20.0    | 255.255.255.0 | 192.168.20.1 |
| Intranet   | 192.168.120.0   | 255.255.255.0 | 192.168.120.1 |

---

## 2️⃣ IP fijas asignadas a Router y Servidores

| Red        | Hostname / Equipo          | IP / Máscara                | Gateway       | Tipo IP | Servicios / Observaciones                     |
|------------|----------------------------|-----------------------------|---------------|---------|-----------------------------------------------|
| DMZ        | R-N02 (Router)             | 192.168.20.1/24             | –             | Fija    | DNS, DHCP                                     |
|            | S1-N02 (Servidor Público)  | 192.168.20.2/24             | 192.168.20.1  | Fija    | HTTP/HTTPS, FTP, SSH                          |
| BBDD       | S2-N02 (Servidor Interno)  | 192.168.20.5/24             | 192.168.20.1  | Fija    | MySQL, Monitor                                |
| Intranet   | R-N02 (Router)             | 192.168.120.100 - 200/24    | 192.168.120.1 | Dinamica|                                               |

---

## 3️⃣ Configuración DHCP para Clientes

| Red      | Equipo       | Rango IP                   | Máscara       | Tipo  | Gateway       |
|----------|--------------|----------------------------|---------------|-------|---------------|
| Clientes | PC-Windows   | 192.168.120.100-200        | 255.255.255.0 | DHCP  | 192.168.120.1 |
| Clientes | PC-Linux     | 192.168.120.100-200        | 255.255.255.0 | DHCP  | 192.168.120.1 |

**Servidor DHCP:** S2-N02 (192.168.20.2)  
**DNS proporcionado por DHCP:** 192.168.20.2  

---

## 4️⃣ Tabla de direccionamiento general

| Red        | Hostname / Equipo      | IP               | Máscara        | Gateway      | Tipo IP   | Servicios / Observaciones                 |
|------------|-------------------------|------------------|----------------|--------------|-----------|--------------------------------------------|
| DMZ        | R-N02 (Router)          | 192.168.2.1      | 255.255.255.0 | –            | Fija      | Gateway DMZ                                 |
|            | S1-N02 (Web Server)     | 192.168.2.2      | 255.255.255.0 | 192.168.2.1  | Fija      | Web, FTP, SSH                               |
| Intranet   | R-N02 (Router)          | 192.168.20.1     | 255.255.255.0 | –            | Fija      | Gateway Intranet                            |
|            | S2-N02 (DB/DNS/DHCP)    | 192.168.20.2     | 255.255.255.0 | 192.168.20.1 | Fija      | MySQL, DNS, DHCP, Monitor                   |
| Clientes   | R-N02 (Router)          | 10.0.0.1         | 255.255.255.0 | –            | Fija      | Gateway Clientes                            |
|            | PC-Windows              | DHCP             | 255.255.255.0 | 10.0.0.1     | Dinámica  | Rango 10.0.0.100–10.0.0.200                 |
|            | PC-Linux                | DHCP             | 255.255.255.0 | 10.0.0.1     | Dinámica  | Rango 10.0.0.100–10.0.0.200                 |

---