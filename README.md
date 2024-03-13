# Development environment
Docker environment required to run php web application.

![GitHub Release](https://img.shields.io/github/v/release/lukaspia/docker-apache-php-mysql)
![GitHub License](https://img.shields.io/github/license/lukaspia/docker-apache-php-mysql)

[Source](https://github.com/lukaspia/docker-apache-php-mysql.git)

## Requirements
* Docker
* Docker compose

## Stack
* PHP 
* Apache
* MySQL
* phpMyAdmin
* Mailpit
* Composer
* Node.js
* Npm
* Git

## Configuration and installation
1. Copy .env.dist to .env file
    ```bash
    cp .env.dist .env
    ```
2. Edit entries of .env
   - CONTAINER_NAME_PREFIX - prefix for containers <span style="color: red">*</span>
   - MYSQL_VERSION - version of mysql (def: latest)
   - ROOT_PASSWORD - password for database user: root
   - DB_NAME - name of database <span style="color: red">*</span>
   - DB_USER - user for database <span style="color: red">*</span>
   - DB_PASSWORD - password for database <span style="color: red">*</span>
   - PHPMYADMIN_VERSION - version of phpmyadmin (def: latest)
   - WEB_PORT_HTTP - port for web http (def: 80)
   - WEB_PORT_HTTPS - port for web https (def: 443)
   - PATH_TO_PROJECT - path to project (def: ./app)
   - PATH_TO_DB_DATA - path to database data (def: ./var/db_data)
3. Edit docker-compose.yml
   - networks: - value from .env CONTAINER_NAME_PREFIX <span style="color: red">*</span>
4. Edit docker/Dockerfile
   - FROM php:[version] - set php version (def: apache - last version)
5. Edit docker/000-default.conf <span style="color: red">*</span>
   - DocumentRoot - path to project index file (def: /var/www/html/, example: /var/www/html/[app-name]/public)
   - Directory - same as DocumentRoot
6. Start compose and environment
   ```bash
    docker-compose up -d
   ```
7. Start working inside container
   ```bash
   docker exec -it ${CONTAINER_NAME_PREFIX}-php-apache bash
   ```

## Constants
* MySQL host: mysql
* MySQL port: 3306:3306
* Phpadmin port: 8080:80 [http://localhost:8080](http://localhost:8080)
* Mailpit web ui port: 8025:8025 [http://localhost:8025](http://localhost:8025)
* Mailpit smtp server port: 1025:1025

## License
[MIT](https://github.com/lukaspia/docker-apache-php-mysql/blob/main/LICENSE)