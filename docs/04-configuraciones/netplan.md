# 🌐 Configuración de Red y Conectividad (Netplan) - S1-N02 (DMZ)

## 🧩 1. Resumen de la Configuración

El servidor **S1-N02**, ubicado en la **DMZ (192.168.120.0/24)**, utiliza **Netplan** para definir su conectividad de red.  
Dispone de **dos interfaces** configuradas manualmente: una para la red **DMZ** (servicios públicos) y otra para la red **compartida/interna** del grupo.

| Interfaz | Red | Dirección IP | Gateway | Propósito |
|-----------|-----|---------------|----------|------------|
| **enp0s2** | DMZ (192.168.120.0/24) | 192.168.120.10/24 | 192.168.2.1 ⚠️ | Servicios públicos (Web, FTP) |
| **enp0s3** | Compartida (192.168.20.0/24) | 192.168.20.1/24 | — | Red interna / Intranet (Acceso a S2-N02) |

| Parámetro | Valor |
|------------|--------|
| **DNS Principal** | 8.8.8.8 |
| **DNS Secundario** | 8.8.4.4 |
| **Ruta por defecto** | A través de la interfaz DMZ (enp0s2) |

> ⚠️ **Nota sobre rutas:**  
> En la configuración actual, la puerta de enlace (`gateway`) de `enp0s2` apunta a `192.168.2.1`, lo cual no corresponde con la subred `192.168.120.0/24`.  
> Esta configuración se mantiene provisionalmente hasta que el router **R-N02** se configure correctamente con la IP `192.168.120.1`.

---

## 🗂️ 2. Archivo de Configuración  
📄 **Ubicación:** `/etc/netplan/00-installer-config.yaml`

El siguiente archivo YAML define las interfaces, direcciones estáticas, rutas y servidores DNS.  
Se ha corregido la indentación y los valores booleanos (`true/false` o `yes/no` válidos para YAML).

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s2:  # Interfaz DMZ (Servicios Públicos)
      dhcp4: no
      addresses:
        - 192.168.120.10/24
      routes:
        - to: default
          via: 192.168.2.1  # ⚠️ Ajustar a 192.168.120.1 cuando esté disponible
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4

    enp0s3:  # Interfaz Compartida / Intranet
      dhcp4: no
      addresses:
        - 192.168.20.1/24
      nameservers:
        addresses:
          - 8.8.8.8
