```
#!/bin/bash

CONTAINER="wp_db"
USER="root"
PASS="rootpassword"
DB="wordpress"

DESTINO="/mnt/copiaswp/incrementales"
BASE="/mnt/copiaswp"
FECHA=$(date +"%Y-%m-%d_%H%M")
FILE_NAME="inc_wp_$FECHA.sql.gz"
LOG="/home/cullera/backup_wp.log"

POS_FILE="$DESTINO/last_pos.txt"

echo "[$(date)] --- Inicio Backup Incremental ---" >> "$LOG"

if ! mountpoint -q "$BASE"; then
    echo "[$(date)] ERROR: TrueNAS no montado en $BASE." >> "$LOG"
    exit 1
fi

mkdir -p "$DESTINO"

STATUS=$(docker exec $CONTAINER mysql -u $USER -p$PASS -e "SHOW MASTER STATUS\G")
LOG_ACTUAL=$(echo "$STATUS" | grep File: | awk '{print $2}')
POS_ACTUAL=$(echo "$STATUS" | grep Position: | awk '{print $2}')

if [ ! -f "$POS_FILE" ]; then
    echo "$LOG_ACTUAL $POS_ACTUAL" > "$POS_FILE"
    echo "[$(date)] Inicializando control de incrementales." >> "$LOG"
    exit 0
fi

read LOG_ANT POS_ANT < "$POS_FILE"

docker exec $CONTAINER mysqlbinlog \
    --start-position=$POS_ANT \
    /var/lib/mysql/$LOG_ACTUAL | gzip > "$DESTINO/$FILE_NAME"

if [ ${PIPESTATUS[0]} -eq 0 ]; then
    echo "$LOG_ACTUAL $POS_ACTUAL" > "$POS_FILE"
    echo "[$(date)] Incremental guardado en $DESTINO/$FILE_NAME" >> "$LOG"
    find "$DESTINO" -name "inc_wp*.sql.gz" -mtime +15 -delete
else
    echo "[$(date)] ERROR en incremental." >> "$LOG"
    rm -f "$DESTINO/$FILE_NAME"
fi

echo "[$(date)] --- Fin Backup Incremental ---" >> "$LOG"
```
