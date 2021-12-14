# How to run a mysql container using docker?

## CLI
```
docker run -e MYSQL_ROOT_PASSWORD=root --name mysql-docker -d -p 3306:3306 mysql:5.7
```

```
docker exec -it <container_id> bash
```

```
mysql -u root -p
```

```
create database example
```

```
show databases;
```

```
use example;
```

## Compose
Create a docker-compose.yaml file
```
version: '3.6'

services: 
    db:
        image: mysql:5.7
        command: --default-authentication-plugin=mysql_native_password
        restart: always
        environment: 
            MYSQL_ROOT_PASSWORD: root
            MYSQL_DATABASE: example_db
    
        volumes: 
            - ./ddl:/docker-entrypoint-initdb.d
        networks:
            - example_net    
networks:
  example_net:
```

Type on terminal
```
docker-compose up
```
