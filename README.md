# P0.0-ASIXC2aC-G02

**Proyecto de Administración de Sistemas Informáticos en Red**

---

## ℹ️ Información del Proyecto

* **Módulo:** M0379  
* **Grupo:** ASIXC2aC-G02  
* **Duración:** 6 semanas (hasta el 18/11)  
* **Sprints:** 3 sprints de 10h cada uno  

---

## 🎯 Objetivo

Desplegar una infraestructura completa con aplicación multicapa que incluya:

* Servidor web
* Router
* SSH
* Base de datos (MySQL)
* DHCP
* DNS
* FTP

El objetivo principal es **simular un entorno real de empresa**, aplicando buenas prácticas de segmentación de redes y disponibilidad de servicios.

---

## 👥 Equipo

* **Miembro 1:** Kevin – Scrum Master  
* **Miembro 2:** Jan – Product Owner  
* **Miembro 3:** Adriano – Scrum Master secundario  

---

## 🏗️ Arquitectura y Justificación

La infraestructura se ha diseñado con **dos redes segmentadas** conectadas a través de un router central (R-N02):

* **DMZ (Zona Desmilitarizada)** – Red intermedia para servidores accesibles desde Internet, como web, FTP y BBDD.  
* **Intranet (Red Interna)** – Red privada para servicios a los clientes.  

### 🔹 Justificación de la Arquitectura

1. **Seguridad**: La DMZ aísla los servicios públicos del resto de la red, evitando un ataque externo.  
2. **Escalabilidad**: Separar clientes y servidores internos permite añadir más servicios sin afectar la seguridad ni la disponibilidad.  
3. **Control**: El router R-N02 permite aplicar políticas de firewall, NAT y enrutamiento entre subredes.  

> ⚠️ Elegimos esta arquitectura y no otra (por ejemplo, una red plana) porque **permite simular correctamente la interacción de servicios públicos y privados** con políticas de seguridad reales, y facilita la práctica de administración.

---

## 🖼️ Diagrama de la Topología

El diagrama refleja la arquitectura seleccionada:

* Router R-N02 conectando DMZ, Intranet
* Servidores ubicados según su rol (Web/FTP/SSH en DMZ, DHCP y DNS en el Router y MySQL en Servidor base de datos)  
* Clientes conectados a la red de usuarios con IP dinámica  

> Este diagrama es **representativo y no redundante**, simplificando la comprensión sin perder detalle de la segmentación de redes y servicios críticos.

---

## 🪪 Credenciales

Usuario para comprobación en todos los sistemas:

* **Usuario:** bchecker  
* **Contraseña:** bchecker121  

---

## 📂 Estructura del Repositorio

---

### **📁 /docs/**
Contiene toda la documentación técnica del proyecto.

#### **01 - Arquitectura**
- `Diagrama_P0.0.drawio` → Diagrama general del sistema  
- `esquema_ips.md` → Asignación completa de IPs  
- `topologia.md` → Descripción de la topología lógica y física  

#### **03 - Servidores**
- `S1-N02-DMZ.md` → Documentación del servidor DMZ  
- `S1-N02-INTRANET.md` → Documentación del servidor Intranet  

#### **04 - configuraciones**
Documentación detallada de cada servicio instalado:

- `backups.md` → Sistema de copias de seguridad  
- `bbdd.md` → Motor de bases de datos  
- `dhcp.md` → Configuración del servidor DHCP (Router)  
- `dns.md` → Configuración del servidor DNS (Router)  
- `ftp.md` → Configuración del servidor FTP en DMZ  
- `router.md` → NAT, forwarding e iptables del Router  
- `web.md` → Servicio web en la DMZ (Apache/PHP)  

#### **05 - bbdd**
- `esquema_tablas.md` → Esquema relacional  

---

### **📁 /data/**
Almacena datos y recursos del proyecto:

- `/csv/` → Datos en formato CSV  
- `equipamientos_educativos.csv` → Datos de ejemplo usados para poblar la base  

---

### **📁 /imagenes/**
Imágenes utilizadas en la documentación (capturas, diagramas, etc.)

---

## 🚀 Sprints

* **Sprint 1:** Planificación de la infraestructura base  
* **Sprint 2:** Servicios de infraestructura  
* **Sprint 3:** Integración y aplicación  

---