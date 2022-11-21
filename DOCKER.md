# Docker

https://www.youtube.com/watch?v=4Dko5W96WHg

Docker es una plataforma abierta para que desarrolladores y administradores de sistemas desarrollen, envíen y ejecuten aplicaciones distribuidas, ya sea en computadoras portátiles, maquinas virtuales de centros de datos o en la nube.

Reporsitorios Públicos de Imagenes de docker los podemos buscar en https://hub.docker.com/

## Image - Imagen de docker

Una imagen de docker nos proprciona un empaquetado de dependencias que tiene como base una distribución de linux. La más utilizada es alpine la cual es muy liviana. Una imagen de Docker es una plantilla de solo lectura que define su contenedor.

## Conatiner - Contenedor de docker

Un contenedor de Docker es una imagen de Docker instanciada (en ejecución).

## Comandos de Docker

Para poder utilizar docker debemos asegurarnos que docker desktop esté instalado y corriendo en el Sistema Operativo.

### Listar imágenes de docker

Esto te muestra el listado de imágenes descargadas en tu docker:

```sh
docker images 
```

### Descargar una imagen

El primer paso para poder tener un contenedor corriendo en docker es descargar una imagen. Para descargar una imagen se utiliza el siguiente comando:

```sh
docker pull <nombre-de-la-imagen>:[<tag>]
docker pull node # Esto descarga la última versión de la imagen de Node.js
docker pull node:16 # El tag "16" indica que se descargará la versión 16 de la imagen de Node.js
docker pull mongo
```

### Eliminar una imagen

```sh
docker image rm <nombre-de-la-imagen>:[<tag>]
docker image rm node
docker image rm node:16
```

Si la imagen ya ha sido utilizada para crear un contenedor, antes de poder borrar la imagen se debe parar la ejecución y/o eliminar el o los contenedores donde se ha utilizado dicha imagen:

```sh
docker container stop <container-id || conatiner-name>
docker container stop my-node
docker container rm <container-id || conatiner-name>
docker container rm my-node
#se puede eliminar tambien con el nombre que yo le quiera poner al container
docker rm monguito
```
### Crear un container o contenedor

```sh
docker container create <image-name>
docker container create mongo
docker create mongo # Abreviatura de los comandos anteriores
docker create --name <container-name> <image-name> 
docker create --name monguito mongo 
```

### poder ejecutar contenedor

```sh
docker start <id devuelto comando (docker create)>
docker start <id corto que puedes ejecutar con (docker ps)>
```

### Listar contenedores

```sh
docker ps # Lista los contenedores que están en ejecución
docker ps -a # Lista todos los contenedores inclusive los que no están en ejecución
```

### Parar la ejecución de un contenedor

```sh
docker stop <container-id || conatiner-name>
docker stop monguito
```
### crear contenedor pero mapeando los puertos

```sh
docker create -p (puerto de la maquina nuestra):(conteneddor queremos mapear con nuestra maquina o el del contenedor) --name <container-name> <image-name>
docker create -p 27017:27017 --name monguito mongo
docker create -p 27017 --name monguito2 mongo #puedo NO decirle que puerto de origen quiero mapear docker eligiria ese puerto
docker create -p 27017:27017 --name monguito -e MONGO_INITDB_ROOT_USERNAME=mongo -e MONGO_INITDB_ROOT_PASSWORD=mongo mongo --network mired
```
las variables de entorno `MONGO_INITDB_ROOT_USERNAME` y `MONGO_INITDB_ROOT_PASSWORD` las busque en la direccion de la imagen de de mongo en docker hub

### como consultar logs y saber si esta funcionando perfectamente luego de revisarlos
```sh
 docker logs <id container> o <container name>
 docker logs monguito <-- todos los logs que creo y si se siguen escribiendo no sabria 
 docker logs --follow monguito <--  queda escuchando los logs que emita nuestro contenedor                         
 ```
 ### encuentra la imagen y (la descarga), crea un contenedor, inicia el contenedor
  
```sh
docker run  <image-name> # Si no existe automaticamente te la descarga y la inicia, en si todos los comandos de docker create se aplican a docker run! la  diferencia es que el cada vez que ejecute el comando docker run se ira creando un contenedor.
docker run mongo
docker run -d  <image-name> # crea el id contenedor
docker run -d mongo 
docker stop <id-container>
docker rm <id-container>
docker run --name monguito -p27017
``` 
### Dockerfile
Se debe crear un archivo llamado Dockerfile, que me permite configurar y construir una imagen personalizada basada en una imagen previa, ademas, puedo compartir archivos que estan en mi maquina local con el contenedor de docker. Dentro de dicho archivo coloco todas las instrucciones para crear nuestro contenedor 

```Dockerfile
# FROM <image-name>:<tag>

FROM node:18
# El contenedor se crea a partir de una imagen de node:18 

RUN mkdir -p /home/app
# El comando RUN me permite correr comandos de la terminal en el container
# Acá creamos el directorio app dentro de /home, aqui es donde colocaamos el codigo de nuestra app

COPY . /home/app
# El comando COPY nos permite copiar archivos y directorios de nuestro ambiente local o anfitrion (.) a un directorio del contenedor (/home/app)

EXPOSE 3000
# expone el puerto del servicio que va a levantar la app

CMD ["node", "/home/app/index.js"]
# ejecuta un comando en la terminal del contenedor

```

luego de tener nuestro Dockerfile podemos construir una imagen a partir de este archivo:
```sh
docker build -t <custom-image-name>:<tag> <Dockerfile-path>
docker build -t miapp:1.0.0 .
```

una vez se ha creado la imagen podemos correrla y crear un contenedor
```sh
docker create miapp -p 3000:3000 --name chanchito --network mired
docker start chanchito
```

### Trabajando con redes en docker

```sh
docker network ls
```
lista todas las redes creadas en docker

```sh
docker network create <network-name>
docker network create mired
```
este comando crea una nueva red 

```sh
docker network rm <network-name>
docker network rm mired
```
este comando elimina la red (mired)

### Docker Compose

El archivo `docker-compose.yaml` nos permite definir toda nuestra infraestructura de contenedores:

`docker-compose.yaml`
```yaml
version: "3.9"

services:
  chanchito:
    build: .
    container_name: app-chanchito
    ports:
      - "3000:3000"
    links:
      - monguito
  monguito:
    container_name: app-monguito
    image: mongo
    ports:
      - "27017:27017"
    environment:
      - MONGO_INITDB_ROOT_USERNAME=mongo
      - MONGO_INITDB_ROOT_PASSWORD=mongo
    volumes:
      - mongo-data:/data/db

volumes:
  mongo-data:
```

Luego de crear nuestro archivo `docker-compose.yaml` podemos crear toda nuestra infraestructura de contenedores usando el siguiente comando:
```sh
docker compose up -d
```

Para eliminar todos los contenedores del docker-compose y por tanto destruir toda la infraestructura que definimos dentro de nuestro archivo `docker-compose.yaml`
```sh
docker compose down
```
