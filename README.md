# docker-compose-lamp

Docker con MySQL, PHPMyAdmin y PHP+Apache. 

🛠️ Se empleó la herramienta **docker-compose** para orquestar los diferentes contenedores. 

## Sobre su uso ⚙️
- _Codigo relacionado con el servicio Apache debe incluirse en el fichero **`www/`**_
- _Scripts para crear BDD deben incluirse en el fichero **`dump/`**_; serán ejecutados a través de volumes-entrypoint
- _Variables de entorno pueden ser modificadas desde el archivo **`.yml`**_
- _Para manipular los contenedores es necesario ingresar los **comandos** desde la terminal, ubicandose dentro del fichero que contiene el archivo **`.yml`**_

## Pasos 📌

### 1. Crear un archivo Dockerfile dentro del fichero donde se alojarán proyectos.

### 2. Editar el archivo Dockerfile:
```
FROM php:8.0.0-apache
ARG DEBIAN_FRONTEND=noninteractive
(opcionalmente instalar complementos con comando RUN)
RUN a2enmod rewrite
```

### 3. Crear y editar archivo docker-compose.yml. Ejemplo:
```
- Version: "3.1"
- Services:
    - db:
        - image: // De donde se obtendrá la imagen
        - ports: // Puertos
        - command: // Comando a ejecutar
        - volumes:  // Persistencia de datos, configuración y punto de entrada (entrypoint)
        - environment: // Variables de entorno
```

### 4. Crear e iniciar los contenedores

```
docker-compose up 
```

### 5. Abrir phpMyAdmin 
Desde el navegador ingresando [http://127.0.0.1:8000](http://127.0.0.1:8000) 



### 6. Incluir proyecto
Clonar NombreProyecto en `www/` y abrir [http://127.0.0.1/NombreProyecto](http://127.0.0.1/NombreProyecto)



### 7. Correr cliente MYSQL
....



## Otros comandos 📄

### - Ejecutar un comando en un contenedor particular, por ejemplo mysql.
```
docker-compose exec db mysql -u root -p
```

### - Parar ejecución de contenedores.
```
docker-compose stop
```

### - Reanudar ejecución de contenedores.
```
docker-compose start
```

### - Parar y remover contenedores, imagenes, networks y volumes.
```
docker-compose down
```
