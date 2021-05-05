Docker
==================================================================

:sipsonis: Comando útiles de docker

Docker es un proyecto de código abierto que automatiza el despliegue de
aplicaciones dentro de contenedores de software, proporcionando una capa
adicional de abstracción y automatización de virtualización a nivel de sistema
operativo en Linux.


Instalación
-------------------------------------------------------------------

`Instalación en Ubuntu <https://docs.docker.com/engine/install/ubuntu/>`_


Ejecutar el comando Docker sin sudo (Opcional)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
De forma predeterminada, el comando docker solamente puede ejecutarse por el
usuario root o por un usuario del grupo docker, el cual se crea
automáticamente durante la instalación de Docker.

Los siguientes pasos son para agregar nuestro usuario al grupo docker.

Crear grupo docker si es que no existe::

  $ sudo addgroup docker

Añadir nuestro usuario al grupo::

  $ sudo usermod -aG docker ${USER}

Para aplicar la nueva membresía de grupo debe cerrar sesión en el servidor y volver a iniciarla,
o puede escribir lo siguiente::

  $ su - ${USER}

Confirmar que se haya agregado su usuario al grupo de docker escribiendo::

  $ id -nG


Docker Hub
----------------------------------------------------------------------------------------
Login::

  $ docker login

Commitear una imagen::

  $ docker commit <contenedor_id> <user>/<repository>:<tag>

Subir una imagen::

  $ docker push <usuario>/<repositorio>:<tag>


Imágenes
----------------------------------------------------------------------------------------
Crear una imagen a partir de un archivo Dockerfile::

  $ docker build -t <usuario>/<repositorio>:<tag> .

Correr una imagen::

  $ docker run -it <nombre>:<tag>

  $ docker run -it <nombre>:<tag> bash

``it``: Terminal interactiva

Correr una imagen y renombrarla::

  $ docker run --name <name> -it <nombre>:<tag>

Renombrar por id::

  $ docker <tag> <imagen_id> <nombre_nuevo>

Listar imágenes::

  $ docker images

Ver el contenido de una imagen::

  $ docker inspect <nombre>

Borrar imagen por id::

  $ docker rmi <imagen_id>

  $ docker rmi --force <imagen_id>

Borrar todas las imágenes::

  $ docker image prune

  $ docker rmi $(docker images -q)

  $ docker image prune -a --filter "until=12h"

Eliminar imagenes colgantes::

  $ docker rmi $(docker images --filter dangling=true -q)


Contenedores
----------------------------------------------------------------------------------------
Correr un contenedor interactivo a travez de una terminal::

  $ docker run -it <imagen>

Correr un contenedor asignadole un nombre::

  $ docker run -it --name <nombre_contenedor>

Correr un contenedor con volúmenes de datos::

  $ docker run -v <ruta_achivo_local>:<ruta_archivo_contenedor> -it <imagen>

Correr un contenedor asignándole una red(en este caso la misma que afuera)::

  $ docker run --net=host -it <nombre>

Correr un contenedor y destruirlo luego::

  $ docker run --rm -it <imagen>

Pegarse a un contenedor que corre en background::

  $ docker attach <container_id>

Ingresar dentro de un contenedor::

  $ docker exec -it <contenedor_id> bash

  $ docker exec -it <contenedor_id> /bin/bash

  $ docker exec -it <contenedor_id> sh

Listar contenedores::

  $ docker ps -a

Listar los contenedores parados::

  $ docker ps -aq

Ver información utíl de un contenedor::

  $ docker inspect <id/nombre>

  $ docker port <nombre_contenedor>

Ver la historia de un contenedor::

  $ docker history <id/nombre>

Parar contenedor::

  $ docker stop <contenedor_id>

Parar todos los contenedores::

  $ docker stop $(docker ps -aq)

Borrar contenedor::

  $ docker rm <contenedor_id>

Borrar contenedores parados(similiar a xargs)::

  $ docker container prune

  $ docker rm $(docker ps -a -q)

  $ docker container prune --filter "until=12h"

Copiar archivos hacia el contenedor::

  $ docker cp foo.txt mycontainer:/foo.txt

Copiar archivos desde el contenedor::

  $ docker cp mycontainer:/foo.txt foo.txt


Redes
----------------------------------------------------------------------------------------
Listar todas las redes::

  $ docker network ls

  $ docker network ps

Borrar redes una por una::

  $ docker network rm <id>

Borrar todas las redes::

  $ docker network prune -a --filter "until=12h"

  $ docker network prune


Volúmenes
----------------------------------------------------------------------------------------
Crear un volumen::

  $ docker volume create <nombre>

Inspeccionar un volumen::

  $ docker inspect <nombre>

Listar todos los volúmenes::

  $ docker volume ls

Borrar volumen colgante::

  $ docker volume rm $(docker volume ls --filter dangling=true -q)

Borrar todos los volúmenes::

  $ docker volume rm prune


Docker compose
----------------------------------------------------------------------------------------
Construir los servicios::

  $ docker-compose -f docker-compose.yml build

Correr servicios::

  $ docker-compose -f docker-compose.yml up

Parar los contenedores::

  $ docker-compose -f docker-compose.yml stop

Bajar los servicios y remueve los contenedores creados en una ejecución anterior::

  $ docker-compose -f docker-compose.yml down --remove-orphans

Correr servicios recontruyendo los servicios::

  $ docker-compose -f docker-compose.yml up --build

Listar contenedores que se están ejecutando::

  $ docker-compose ps

Para debbugear un servico en específico::

  $ docker-compose ps

  $ docker stop -f <id>

  $ docker-compose run --rm --service-ports <servicio>

Correr comandos::

  $ docker-compose run --rm <contenedor> <comando>

Ver lo logs de un contenedor::

  $ docker-compose logs <contenedor>

Levantar contenedores sin cache::

  $ docker-compose up --force-recreate


Sistema
----------------------------------------------------------------------------------------
Memoría utilizada por docker::

  $ docker stats


Extras
----------------------------------------------------------------------------------------
Borrar todo::

  $ docker system prune -a -f --volumes
