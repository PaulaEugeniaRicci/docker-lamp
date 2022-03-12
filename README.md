# docker-compose-lamp

Docker con Apache, MySQL, PHPMyAdmin y PHP. 

## 🛠️
Se uso la herramienta **docker-compose** para orquestar los diferentes contenedores. 

## Sobre su uso:
_- Codigo relacionado con el servicio Apache debe incluirse en el fichero **"www"**_
_- Scripts para crear BDD debe incluirse en el fichero **"dump"**_
_- Variables de entorno pueden ser modificadas desde el **"archivo .yml"**_
_-Para manipular los contenedores es necesario ngresar los siguientes **"comandos"** desde la terminal, ubicandose dentro del fichero que contiene el **"archivo .yml"**_

### 1. Crear e iniciar los contenedores.

```
docker-compose up 
```

### 2. Ejecutar un comando en un contenedor particular, por ejemplo mysql.
```
docker-compose exec db mysql -u root -p
```

### 3. Parar ejecución de contenedores.
```
docker-compose stop
```

### 4. Reanudar ejecución de contenedores.
```
docker-compose start
```

### 5. Parar y remover contenedores, imagenes, networks y volumes.
```
docker-compose down
```
