# Tabla de direcciones IP
**Proyecto:** P0.0-ASIXc2A-G02
**Equipo:** R-N02
**Arquitectura:** 2 Servidoress (DMZ + Intranet)
**Fecha de creacion:** 14/10/25
**Fecha actualizacion:** 14/10/25

---

## 1️⃣ Definir rangos de IP para cada red

| Red       | Rango de Red   | Máscara        | Gateway       | Servicios / Propósito                  |
|-----------|---------------|----------------|---------------|---------------------------------------|
| DMZ       | 192.168.2.0   | 255.255.255.0  | 192.168.2.1   | Web Server, FTP, SSH                   |
| Intranet  | 192.168.20.0   | 255.255.255.0  | 192.168.20.1   | MySQL, DNS, DHCP, Monitor de red       |
| Clientes  | 10.0.0.0      | 255.255.255.0  | 10.0.0.1      | Red de usuarios                        |

---

## 2️⃣ Asignar IP fijas a cada servidor y Router

| Red       | Hostname / Equipo      | IP / Máscara     | Gateway       | Tipo IP | Servicios / Observaciones               |
|-----------|----------------------|-----------------|---------------|---------|----------------------------------------|
| DMZ       | R-N02 (Router)       | 192.168.2.1/24  | –             | Fija    | Gateway DMZ                             |
|           | S1-N02 (Servidor Público) | 192.168.2.2/24 | 192.168.2.1  | Fija    | Web Server (HTTP/HTTPS), FTP, SSH      |
| Intranet  | R-N02 (Router)       | 192.168.20.1/24  | –             | Fija    | Gateway Intranet                        |
|           | S2-N02 (Servidor Interno) | 192.168.20.1/24 | 192.168.20.1  | Fija    | MySQL, DNS, DHCP, Monitor               |

## 3️⃣ Definir rango DHCP para clientes

| Red       | Equipo       | Rango IP         | Máscara        | Tipo  | Gateway   |
|-----------|-------------|-----------------|----------------|-------|-----------|
| Clientes  | PC-Windows  | 10.0.0.100-10.0.0.200 | 255.255.255.0 | DHCP  | 10.0.0.1 |
| Clientes  | PC-Linux    | 10.0.0.100-10.0.0.200 | 255.255.255.0 | DHCP  | 10.0.0.1 |

**Servidor DHCP:** S2-N02 (192.168.20.2)  
**DNS proporcionado por DHCP:** 192.168.20.2  


---

## 4️⃣ Tabla de direccionamiento completa

| Red       | Hostname / Equipo      | IP           | Máscara        | Gateway       | Tipo IP | Servicios / Observaciones               |
|-----------|----------------------|--------------|----------------|---------------|---------|----------------------------------------|
| DMZ       | R-N02 (Router)       | 192.168.2.1  | 255.255.255.0  | –             | Fija    | Gateway DMZ                             |
|           | S1-N02               | 192.168.2.2 | 255.255.255.0  | 192.168.2.1   | Fija    | Web, FTP, SSH                           |
| Intranet  | R-N02 (Router)       | 192.168.20.1  | 255.255.255.0  | –             | Fija    | Gateway Intranet                        |
|           | S2-N02               | 192.168.20.2 | 255.255.255.0  | 192.168.20.1   | Fija    | MySQL, DNS, DHCP, Monitor               |
| Clientes  | R-N02 (Router)       | 10.0.0.1     | 255.255.255.0  | –             | Fija    | Gateway Clientes                         |
|           | PC-Windows           | DHCP         | 255.255.255.0  | 10.0.0.1      | Dinámica | Cliente Windows                         |
|           | PC-Linux             | DHCP         | 255.255.255.0  | 10.0.0.1      | Dinámica | Cliente Linux                            |

---