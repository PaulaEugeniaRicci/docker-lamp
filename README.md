# docker-compose-lamp

Docker con Apache, MySQL, PHPMyAdmin y PHP. 

🛠️ Se empleó la herramienta **docker-compose** para orquestar los diferentes contenedores. 

## Sobre su uso ⚙️
- _Codigo relacionado con el servicio Apache debe incluirse en el fichero **`www/`**_
- _Scripts para crear BDD deben incluirse en el fichero **`dump/`**_
- _Variables de entorno pueden ser modificadas desde el **archivo `.yml`**_
- _Para manipular los contenedores es necesario ingresar los **comandos** desde la terminal, ubicandose dentro del fichero que contiene el **archivo `.yml`**_

## Pasos 📌

### 1. Crear e iniciar los contenedores.

```
docker-compose up 
```

### 2. Abrir phpMyAdmin 
Desde el navegador ingresando [http://127.0.0.1:8000](http://127.0.0.1:8000) 



### 3. Incluir proyecto
Clonar NombreProyecto en `www/` y abrir [http://127.0.0.1/NombreProyecto](http://127.0.0.1/NombreProyecto)



### 4. Correr cliente MYSQL
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
