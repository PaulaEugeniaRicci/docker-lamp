# docker-lamp

Docker con Apache, MySQL, PHPMyAdmin y PHP. 

🛠️ Con Dockerfile, sin herramientas de orquestación de contenedores.

## Sobre su uso ⚙️
- _Cada contenedor (con su correspondiente servicio) tendrá su Dockerfile y se ejecutará por separado_
- _Las imagenes para crear contenedores pueden bajarse de hub.docker.com_
- _Codigo relacionado con el servicio Apache debe incluirse en el fichero **`www/`**_

## Pasos para APACHE📌

### 1. Crear un archivo Dockerfile dentro del fichero donde se alojarán proyectos.

### 2. Editar el archivo Dockerfile:

```
FROM _imagen_
COPY _index.html /var/www/html/_
CMD _[“/usr/sbin/httpd”, “-D”, “FOREGROUND”]_
EXPOSE 80
```
### 3. Ejecutar, desde la terminal, los siguientes comandos:
```
$ docker build -t nombre_app .
$ docker run -dit --name nombre_app -p 8080:80 -v "$PWD":www/var/www/html 
```
### 4. Probar si funciona el servidor
Desde el navegador ingresando [http://127.0.0.1:8080]

## Pasos para MYSQL📌

## Pasos para PHPMyAdmin📌




## ¿Qué significan los flags y comandos? 📄

- `-name`: da un nombre para identificar el contenedor.

#### Comandos⌨️
- `FROM`: inicializa una build stage y establece la imagen base.
- `RUN`: busca imagen localmente, sino encuentra la busca y descarga, crea contenedor y lo ejecuta.
- `COPY`: copia el contenido a un fichero destino dentro del contenedor.
- `CMD`: ejecuta un comando no bien se crea el contenedor. Especifica **parametros** que se le darán al archivo ejecutable (_ver ENTRYPOINT_). _En este caso CMD [“/usr/sbin/httpd”,” -D”,” FOREGROUND”] permite correr el servidor de fondo._

#### Flags⌨️
- `-d`: ejecuta el contenedor en **modo detached**, en el background. 
- `-i`: para que sea interactivo (_mantiene STDIN abierto aunque este en modo detached_).
- `-p`: mapeo de puertos.
- `-v`: crea un **volume**. Es imprescindible para persistir datos. A continuación de este flag se incluye `"$PWD"` en referencia al fichero actual, seguido de ":" y una ruta donde se guardarán los datos.


## Networks 🔩
Los contenedores se comunican entre sí a través de **networks**. Al iniciar, Docker crea una network por defecto llamada **bridge**, permitiendo comunicación container-a-container. Cada nuevo contenedor creado será parte de esa network, a menos que le indiques lo contrario. **User-defined networks** pueden ser creadas para configurar aspectos como la exposición de puertos, qué contenedores forman parte de la red, y de qué forma se conectan con otros (_uso de alias_). 
