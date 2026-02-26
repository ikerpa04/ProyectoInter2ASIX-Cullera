```
services:
  zabbix-db:
    image: mysql:8.0
    container_name: zabbix_db
    restart: always
    command: --default-authentication-plugin=mysql_native_password
    environment:
      MYSQL_DATABASE: zabbix
      MYSQL_USER: zabbix
      MYSQL_PASSWORD: zabbixpass
      MYSQL_ROOT_PASSWORD: rootpassword
    volumes:
      - zabbix_db_data:/var/lib/mysql
    healthcheck:
      test: ["CMD", "mysqladmin", "ping", "-h", "localhost"]
      interval: 10s
      timeout: 5s
      retries: 15

  zabbix-server:
    image: zabbix/zabbix-server-mysql:latest
    container_name: zabbix_server
    restart: always
    ports:
      - "10051:10051"
    environment:
      DB_SERVER_HOST: zabbix-db
      MYSQL_DATABASE: zabbix
      MYSQL_USER: zabbix
      MYSQL_PASSWORD: zabbixpass
    depends_on:
      zabbix-db:
        condition: service_healthy

  zabbix-web:
    image: zabbix/zabbix-web-nginx-mysql:latest
    container_name: zabbix_web
    restart: always
    ports:
      - "8082:8080"
    environment:
      DB_SERVER_HOST: zabbix-db
      MYSQL_DATABASE: zabbix
      MYSQL_USER: zabbix
      MYSQL_PASSWORD: zabbixpass
      ZBX_SERVER_HOST: zabbix-server
    depends_on:
      zabbix-server:
        condition: service_started

  zabbix-agent:
    image: zabbix/zabbix-agent:latest
    container_name: zabbix_agent
    restart: always
    environment:
      ZBX_SERVER_HOST: zabbix-server
    depends_on:
      - zabbix-server

volumes:
  zabbix_db_data:
```
