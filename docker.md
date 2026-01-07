# 🐳 Manual de Referencia: Docker

## Gestión de Imágenes

| Comando                                  | Descripción                                                       |
| ---------------------------------------- | ----------------------------------------------------------------- |
| `docker pull imagen:tag`                 | Descarga una imagen desde Docker Hub.                             |
| `docker build -t nombre:tag .`           | Construye una imagen desde un Dockerfile en el directorio actual. |
| `docker images`                          | Lista todas las imágenes locales.                                 |
| `docker rmi imagen:tag`                  | Elimina una imagen específica.                                    |
| `docker rmi $(docker images -q)`         | Elimina todas las imágenes no utilizadas.                         |
| `docker tag imagen:tag nuevo-nombre:tag` | Etiqueta una imagen con un nuevo nombre.                          |
| `docker push nombre:tag`                 | Sube una imagen a un registro (como Docker Hub).                  |
| `docker save imagen > archivo.tar`       | Guarda una imagen en un archivo tar.                              |
| `docker load < archivo.tar`              | Carga una imagen desde un archivo tar.                            |

## Gestión de Contenedores

| Comando                                        | Descripción                                                |
| ---------------------------------------------- | ---------------------------------------------------------- |
| `docker run -d --name contenedor imagen`       | Ejecuta un contenedor en segundo plano.                    |
| `docker run -it --name contenedor imagen bash` | Ejecuta un contenedor interactivo.                         |
| `docker ps`                                    | Lista contenedores en ejecución.                           |
| `docker ps -a`                                 | Lista todos los contenedores (incluyendo detenidos).       |
| `docker start contenedor`                      | Inicia un contenedor detenido.                             |
| `docker stop contenedor`                       | Detiene un contenedor en ejecución.                        |
| `docker restart contenedor`                    | Reinicia un contenedor.                                    |
| `docker rm contenedor`                         | Elimina un contenedor detenido.                            |
| `docker rm $(docker ps -aq)`                   | Elimina todos los contenedores detenidos.                  |
| `docker exec -it contenedor bash`              | Ejecuta un comando en un contenedor en ejecución.          |
| `docker logs contenedor`                       | Muestra los logs de un contenedor.                         |
| `docker logs -f contenedor`                    | Sigue los logs en tiempo real.                             |
| `docker inspect contenedor`                    | Muestra información detallada de un contenedor.            |
| `docker stats`                                 | Muestra estadísticas de uso de recursos de contenedores.   |
| `docker top contenedor`                        | Muestra los procesos en ejecución dentro de un contenedor. |

## Redes

| Comando                                           | Descripción                          |
| ------------------------------------------------- | ------------------------------------ |
| `docker network ls`                               | Lista todas las redes.               |
| `docker network create nombre-red`                | Crea una nueva red.                  |
| `docker network rm nombre-red`                    | Elimina una red.                     |
| `docker network connect nombre-red contenedor`    | Conecta un contenedor a una red.     |
| `docker network disconnect nombre-red contenedor` | Desconecta un contenedor de una red. |
| `docker network inspect nombre-red`               | Muestra detalles de una red.         |

## Volúmenes

| Comando                                     | Descripción                                    |
| ------------------------------------------- | ---------------------------------------------- |
| `docker volume ls`                          | Lista todos los volúmenes.                     |
| `docker volume create nombre-volumen`       | Crea un nuevo volumen.                         |
| `docker volume rm nombre-volumen`           | Elimina un volumen.                            |
| `docker volume prune`                       | Elimina todos los volúmenes no utilizados.     |
| `docker run -v nombre-volumen:/ruta imagen` | Monta un volumen en un contenedor.             |
| `docker run -v /host:/contenedor imagen`    | Monta un directorio del host en el contenedor. |

## Docker Compose

| Comando                                | Descripción                                       |
| -------------------------------------- | ------------------------------------------------- |
| `docker-compose up`                    | Inicia servicios definidos en docker-compose.yml. |
| `docker-compose up -d`                 | Inicia servicios en segundo plano.                |
| `docker-compose down`                  | Detiene y elimina servicios.                      |
| `docker-compose build`                 | Construye imágenes para servicios.                |
| `docker-compose logs`                  | Muestra logs de servicios.                        |
| `docker-compose ps`                    | Lista contenedores de servicios.                  |
| `docker-compose exec servicio comando` | Ejecuta un comando en un servicio.                |
| `docker-compose restart servicio`      | Reinicia un servicio.                             |
| `docker-compose scale servicio=n`      | Escala un servicio a n instancias.                |

## Limpieza y Mantenimiento

| Comando                  | Descripción                                           |
| ------------------------ | ----------------------------------------------------- |
| `docker system prune`    | Elimina contenedores, redes y imágenes no utilizadas. |
| `docker system prune -a` | Elimina todo, incluyendo imágenes no utilizadas.      |
| `docker system df`       | Muestra uso del disco por Docker.                     |
| `docker container prune` | Elimina contenedores detenidos.                       |
| `docker image prune`     | Elimina imágenes colgantes.                           |
| `docker volume prune`    | Elimina volúmenes no utilizados.                      |

## Registros y Autenticación

| Comando                 | Descripción                                            |
| ----------------------- | ------------------------------------------------------ |
| `docker login`          | Inicia sesión en un registro (por defecto Docker Hub). |
| `docker logout`         | Cierra sesión en el registro.                          |
| `docker search termino` | Busca imágenes en Docker Hub.                          |
| `docker info`           | Muestra información del sistema Docker.                |
| `docker version`        | Muestra versiones de Docker cliente y servidor.        |

## Comandos Avanzados

| Comando                                      | Descripción                                      |
| -------------------------------------------- | ------------------------------------------------ | ---------- |
| `docker commit contenedor nueva-imagen:tag`  | Crea una imagen desde un contenedor modificado.  |
| `docker export contenedor > archivo.tar`     | Exporta el sistema de archivos de un contenedor. |
| `docker import archivo.tar nueva-imagen:tag` | Importa un sistema de archivos como imagen.      |
| `docker build --no-cache -t nombre:tag .`    | Construye sin usar cache.                        |
| `docker run --privileged imagen`             | Ejecuta con privilegios extendidos.              |
| `docker run --env VAR=valor imagen`          | Establece variables de entorno.                  |
| `docker run -p host:contenedor imagen`       | Mapea puertos.                                   |
| `docker run --link contenedor:alias imagen`  | Enlaza contenedores (obsoleto, usar redes).      | </content> |

<parameter name="filePath">c:\Users\andre\Desktop\comandos\docker.md
