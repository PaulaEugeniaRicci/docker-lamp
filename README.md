# docker-lamp

Docker con Apache, MySQL, PHPMyAdmin y PHP. 

🛠️ Con Dockerfile, sin herramientas de orquestación de contenedores.

## Sobre su uso ⚙️
- _Cada contenedor (con su correspondiente servicio) tendrá su Dockerfile y se ejecutará por separado_
- _Las imagenes para crear contenedores pueden bajarse de hub.docker.com_
- _Codigo relacionado con el servicio Apache debe incluirse en el fichero **`www/`**_

## Pasos para PHP-APACHE📌

### 1. Crear un archivo Dockerfile dentro del fichero donde se alojarán proyectos.

### 2. Editar el archivo Dockerfile:

```
FROM php:7.2-apache
COPY src/ /var/www/html/
```

### 3. Ejecutar, desde la terminal, los siguientes comandos:
```
$ docker build -t nombre-php .
$ docker run -d --name nombre-app -p 80:80 -v "$PWD":/var/www/html  nombre-php
```

### 4. Probar si funciona el servidor
Desde el navegador ingresando [http://127.0.0.1:80]

## Pasos para MYSQL📌

### 1. Ejecutar, desde la terminal, los siguientes comandos:
```
$ docker run --name nombre-contenedor-mysql -v /my/own/datadir:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=password -d mysql:tag
```
### 2. Ejecutar mas comandos para conectar con el servicio desde la línea de comando:
```
$ docker run -it --network nombtr-network --rm mysql mysql -hnombre-contenedor-mysql -uejemplousuario -p
```
### 3. 



### 4. Probar si funciona el servidor


## Pasos para PHPMyAdmin📌




## ¿Qué significan los flags y comandos? 📄

- `-name`: da un nombre para identificar el contenedor.

#### Comandos⌨️
- `FROM`: inicializa una build stage y establece la imagen base.
- `RUN`: busca imagen localmente, sino encuentra la busca y descarga, crea contenedor y lo ejecuta.
- `COPY`: copia el contenido a un fichero destino dentro del contenedor.


#### Flags⌨️
- `-d`: ejecuta el contenedor en **modo detached**, en el background. 
- `-e`: ejecuta una sentencia.
- `-i`: para que sea interactivo (_mantiene STDIN abierto aunque este en modo detached_).
- `-p`: mapeo de puertos.
- `-v`: crea un **volume**. Es imprescindible para persistir datos. A continuación de este flag se incluye `"$PWD"` en referencia al fichero actual, seguido de ":" y una ruta donde se guardarán los datos.


## Networks 🔩
Los contenedores se comunican entre sí a través de **networks**. Al iniciar, Docker crea una network por defecto llamada **bridge**, permitiendo comunicación container-a-container. Cada nuevo contenedor creado será parte de esa network, a menos que le indiques lo contrario. **User-defined networks** pueden ser creadas para configurar aspectos como la exposición de puertos, qué contenedores forman parte de la red, y de qué forma se conectan con otros (_uso de alias_). 
