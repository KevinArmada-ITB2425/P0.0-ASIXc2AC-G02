# Documentación de Backups - S1-N02

## 📦 ¿Qué se respalda?

1. Configuraciones de red (`/etc/netplan`)
2. Configuraciones de servicios (Apache, PHP, FTP, SSH, UFW)
3. Archivos web (`/var/www/html`)
4. Archivos FTP (`/home/bchecker/ftp`)
5. Home del usuario bchecker
6. Lista de paquetes instalados
7. Información del sistema

## ⏰ Programación

- **Diario:** 2:00 AM (todos los días)
- **Semanal:** 3:00 AM (domingos)

## 📁 Ubicación de Backups

- **Diarios:** `/backup/daily/`
- **Semanales:** `/backup/weekly/`
- **Log:** `/backup/backup.log`

## 🔄 Retención

- **Backups diarios:** 7 días
- **Backups semanales:** 4 semanas (28 días)

## 🛠️ Scripts Disponibles

| Script | Ubicación | Función |
|--------|-----------|---------|
| backup_s1n02.sh | `/usr/local/bin/` | Realiza backup |
| restore_s1n02.sh | `/usr/local/bin/` | Restaura backup |
| check_backups.sh | `/usr/local/bin/` | Verifica estado |

## 📝 Comandos Útiles

### Ejecutar backup manual:
```bash
sudo /usr/local/bin/backup_s1n02.sh
```

### Ver estado de backups:
```bash
sudo /usr/local/bin/check_backups.sh
```

### Ver log:
```bash
tail -f /backup/backup.log
```

### Listar backups:
```bash
ls -lh /backup/daily/
ls -lh /backup/weekly/
```

### Restaurar backup:
```bash
sudo /usr/local/bin/restore_s1n02.sh
```

## 🔍 Verificar CRON
```bash
sudo crontab -l
sudo systemctl status cron
```

## 🧪 Prueba de Restauración

1. Identificar archivo de backup:
```bash
ls -lh /backup/daily/
```

2. Extraer en directorio temporal:
```bash
mkdir /tmp/test_restore
tar -xzf /backup/daily/ARCHIVO.tar.gz -C /tmp/test_restore
```

3. Verificar contenido:
```bash
ls -lR /tmp/test_restore
```

## ⚠️ Notas Importantes

- Los backups se comprimen con gzip (.tar.gz)
- Los backups antiguos se eliminan automáticamente
- Verificar espacio en disco regularmente
- Probar restauración periódicamente

**Última actualización:** [Fecha]