```
#!/bin/bash

CONTAINER="wp_db"
USER="root"
PASS="rootpassword"
DB="wordpress"

DESTINO="/mnt/copiaswp"
FECHA=$(date +"%Y-%m-%d_%H%M")
FILE_NAME="db_wp_$FECHA.sql.gz"
LOG="/home/cullera/backup_wp.log"

echo "[$(date)] --- Inicio de Backup ---" >> "$LOG"

if ! mountpoint -q "$DESTINO"; then
    echo "[$(date)] ERROR: TrueNAS no se encuentra montado en $DESTINO." >> "$LOG"
    exit 1
fi

docker exec $CONTAINER mysqldump -u $USER -p$PASS $DB | gzip > "$DESTINO/$FILE_NAME"

if [ ${PIPESTATUS[0]} -eq 0 ]; then
    echo "[$(date)] Copia almacenada en $DESTINO/$FILE_NAME" >> "$LOG"
    find "$DESTINO" -name "db_wp*.sql.gz" -mtime +30 -delete
    echo "[$(date)] Limpieza de archivos antiguos completada." >> "$LOG"

else

    echo "[$(date)] ERROR: Falló el mysqldump del contenedor $CONTAINER" >> "$LOG"
    rm -f "$DESTINO/$FILE_NAME"
fi

echo "[$(date)] --- Fin del Proceso ---" >> "$LOG"
```
