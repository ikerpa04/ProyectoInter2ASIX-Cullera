```
services:
  db:
    image: mariadb:10.11
    container_name: wp_db
    restart: always
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wpuser
      MYSQL_PASSWORD: wppassword
      MYSQL_ROOT_PASSWORD: rootpassword
    volumes:
      - db_data:/var/lib/mysql

  wordpress:
    image: wordpress:6.4-php8.1-apache
    container_name: wp_app
    restart: always
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DB_USER: wpuser
      WORDPRESS_DB_PASSWORD: wppassword
    volumes:
      - wp_data:/var/www/html
    depends_on:
      - db

  phpmyadmin:
    image: phpmyadmin:5.2
    container_name: wp_phpmyadmin
    restart: always
    ports:
      - "8081:80"
    environment:
      PMA_HOST: db
      PMA_PORT: 3306
      PMA_USER: root
      PMA_PASSWORD: rootpassword
    depends_on:
      - db

volumes:
  db_data:
  wp_data:
```
