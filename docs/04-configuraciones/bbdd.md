# 📚 Documentación: Implementación de MySQL en Ubuntu Server

Este documento detalla el proceso para configurar una base de datos MySQL en un **Ubuntu Server** (`192.168.20.5`) y asegurar el acceso remoto al usuario **`bchecker`** desde la máquina del compañero (`192.168.20.2`).

---

## 1. 💾 Instalación de MySQL Server

Ejecuta estos comandos en tu servidor Ubuntu:

```bash
## 1. Actualizar la lista de paquetes
sudo apt update

## 2. Instalar MySQL Server
sudo apt install mysql-server

```
![Status Mysql](/imagenes/SystemctlMysql.png)



---

## 2. 🛡️ Configuración del Firewall (UFW)

Es esencial configurar UFW para proteger el servidor en la DMZ. Solo permitiremos el acceso SSH y el acceso a MySQL (`3306`) *únicamente desde la IP del compañero*.

### A. Políticas por defecto

```bash
## Denegar todo el tráfico entrante por defecto
sudo ufw default deny incoming
sudo ufw default allow outgoing

![Firewall](/imagenes/UfwDefault.png)

```

### B. Reglas de acceso

```bash
## Permitir SSH (puerto 22) para la administración
sudo ufw allow ssh

## Permitir MySQL (puerto 3306) solo a la IP del compañero
sudo ufw allow from 192.168.20.2 to any port 3306

## Activar UFW
sudo ufw enable

## Verificar el estado
sudo ufw status numbered

![ufw status](/imagenes/UfwStatus.png)

```

---

## 3. 🧑‍💻 Configuración de Usuarios y Permisos en MySQL

Usuario **`bchecker`** con permisos sobre la base de datos `datos_bcn_educacio`.

### A. Acceso a la consola de MySQL

```bash
sudo mysql -u root -p
```

### B. Creación del usuario `bchecker`


```sql
CREATE USER 'bchecker'@'192.168.20.2' IDENTIFIED BY 'bchecker121';
```

### C. Concesión de permisos

```sql
GRANT ALL PRIVILEGES ON datos_bcn_educacio.* TO 'bchecker'@'192.168.20.2';
```

### D. Aplicar cambios y salir

```sql
FLUSH PRIVILEGES;
EXIT;
```
![usuarios](/imagenes/usuarios_bbdd.webp)
---

## 4. 🚀 Conexión Remota del Compañero

(`192.168.20.2`) tiene que usar la IP del servidor (`192.168.20.5`) para conectarse con el usuario `bchecker`.

### A. Comando de conexión

```bash
mysql -h 192.168.20.5 -P 3306 -u bchecker -p
```
![login](/imagenes/LOGIN_bbdd.png)
Se solicitará la contraseña.

### B. Uso de la base de datos

```sql
## Seleccionar la base de datos
USE datos_bcn_educacio;

## Mostrar las tablas
SHOW TABLES;

## Consultar una tabla
SELECT * FROM equipaments_educacio LIMIT 10;
```
![show tables](/imagenes/mostrar_tablas.png)
---
