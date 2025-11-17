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
* Monitor de redes
* SSH
* Base de datos (MySQL)
* DHCP
* DNS
* FTP

El objetivo principal es **simular un entorno real de empresa**, aplicando buenas prácticas de segmentación de redes, seguridad y disponibilidad de servicios.

---

## 👥 Equipo

* **Miembro 1:** Kevin – Scrum Master  
* **Miembro 2:** Jan – Product Owner  
* **Miembro 3:** Adriano – Scrum Master secundario  

---

## 🏗️ Arquitectura y Justificación

La infraestructura se ha diseñado con **tres redes segmentadas** conectadas a través de un router central (R-N02):

* **DMZ (Zona Desmilitarizada)** – Red intermedia para servidores accesibles desde Internet, como web, FTP y correo.  
* **Intranet (Red Interna)** – Red privada para servicios críticos internos, como bases de datos, DNS y DHCP.  
* **Clientes / NAT** – Red de usuarios finales que obtienen IP dinámica y acceso controlado.

### 🔹 Justificación de la Arquitectura

1. **Seguridad**: La DMZ aísla los servicios públicos del resto de la red, evitando que un ataque externo comprometa la Intranet.  
2. **Escalabilidad**: Separar clientes y servidores internos permite añadir más servicios sin afectar la seguridad ni la disponibilidad.  
3. **Control y monitorización**: El router R-N02 permite aplicar políticas de firewall, NAT y enrutamiento entre subredes.  
4. **Realismo empresarial**: Esta arquitectura refleja la práctica habitual en entornos de producción donde se separan redes externas de internas.

> ⚠️ Elegimos esta arquitectura y no otra (por ejemplo, una red plana) porque **permite simular correctamente la interacción de servicios públicos y privados** con políticas de seguridad reales, y facilita la práctica de administración y monitorización de tráfico.

---

## 🖼️ Diagrama de la Topología

El diagrama refleja la arquitectura seleccionada:

* Router R-N02 conectando DMZ, Intranet y Clientes  
* Servidores ubicados según su rol (Web/FTP en DMZ, DB/DHCP/DNS en Intranet)  
* Clientes conectados a la red de usuarios con IP dinámica  

> Este diagrama es **representativo y no redundante**, simplificando la comprensión sin perder detalle de la segmentación de redes y servicios críticos.

---

## 🪪 Credenciales

Usuario para comprobación en todos los sistemas:

* **Usuario:** bchecker  
* **Contraseña:** bchecker121  

---

## 📂 Estructura del Repositorio

* `/docs/` – Documentación del proyecto  
* `/scripts/` – Scripts de automatización  
* `/app/` – Aplicación web  
* `/data/` – Datos y copias de seguridad  
* `/configs/` – Archivos de configuración y aplicación  

---

## 🚀 Sprints

* **Sprint 1:** Planificación de la infraestructura base  
* **Sprint 2:** Servicios de infraestructura  
* **Sprint 3:** Integración y aplicación  

---

## 📚 Documentación

Ver la carpeta `/docs/` para la documentación detallada de cada componente y su configuración.
