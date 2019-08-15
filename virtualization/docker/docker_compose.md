# Docker Compose

## Installation

## Nutzung


## Komponenten


## Beispiel
##### docker-compose-Manifest
```
version: '3.3'
services:
  db:
    image: mysql:5.7.9
    hostname: mysqlserver
    restart: always
    container_name: db-server
    environment:
      MYSQL_ROOT_PASSWORD: root.12345
      MYSQL_DATABASE: testdb
      MYSQL_USER: dbuser
      MYSQL_PASSWORD: dbuser.12345
    volumes:
      - ./data/db:/var/lib/mysql
  web:
    build: ./
    image: php:1812291120
    restart: always
    container_name: web-server
    volumes:
      - ./data/web:/var/www/html
    ports:
      - 8181:80 
```

##### dockerfile
```
FROM php:7.3.0-apache

RUN docker-php-ext-install mysqli
```
