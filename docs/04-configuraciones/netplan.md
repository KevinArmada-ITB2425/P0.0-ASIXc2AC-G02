# 🌐 Configuración de Red y Conectividad (Netplan) – S1-N02 (DMZ)

## 🧩 1️⃣ Resumen de la Configuración

El servidor **S1-N02**, ubicado en la **DMZ (`192.168.2.0/24`)**, utiliza **Netplan** para definir su conectividad de red.  
Dispone de **dos interfaces** configuradas de forma estática:

| Interfaz | Red | Dirección IP | Gateway | Propósito |
|-----------|-----|---------------|---------|------------|
| **enp0s2** | DMZ (`192.168.2.0/24`) | 192.168.2.10/24 | 192.168.2.1 | Servicios públicos (Web, FTP) |
| **enp0s3** | Intranet (`192.168.20.0/24`) | 192.168.20.10/24 | — | Red interna / Acceso a S2-N02 |

### 🔧 Parámetros Adicionales

| Parámetro | Valor |
|-----------|-------|
| **DNS Principal** | 8.8.8.8 |
| **DNS Secundario** | 8.8.4.4 |
| **Ruta por defecto** | A través de la interfaz DMZ (`enp0s2`) |

> ⚠️ **Nota sobre rutas:**  
> La puerta de enlace (`gateway`) de `enp0s2` apunta a `192.168.2.1`, que corresponde con la IP del router en la DMZ.  
> Esto asegura que el tráfico público salga correctamente hacia Internet y hacia otras redes segmentadas.

---

## 🗂️ 2️⃣ Archivo de Configuración Netplan

📄 **Ubicación:** `/etc/netplan/00-installer-config.yaml`

El siguiente archivo YAML define interfaces, IPs estáticas, rutas y servidores DNS:

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s2:  # Interfaz DMZ (Servicios Públicos)
      dhcp4: no
      addresses:
        - 192.168.2.10/24
      routes:
        - to: default
          via: 192.168.2.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4

    enp0s3:  # Interfaz Intranet / Acceso a S2-N02
      dhcp4: no
      addresses:
        - 192.168.20.10/24
      nameservers:
        addresses:
          - 8.8.8.8
