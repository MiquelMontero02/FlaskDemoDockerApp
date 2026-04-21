# Dokcer Volumes
## Introducción

Ahora que tenemos nuestra base de datos viviendo en un contenedor, nos deberíamos preguntar lo siguiente:

> Que pasa si mi contenedor falla?

Cuando se trabaja en contenedores la metodología de trabajo se centra en **borrar y crear** antés que **arreglar** un contenedor que esté dando problemas.

Pero si hacemos esto en un container cuya función es la de ser la base de datos, no perderíamos toda la información?

La solución a este problema reside en la definición de **Volumenes**. Un volumen no és nada más que una ubicación en nuestra máquina host en la que almacenaremos la información de nuestros contenedores

## Commandos

### Crear un volumen

> ```docker volume create --driver=flocker volumename```

### Assignar volumenes
- Desde `run` comand
> docker run -d --name test -v my_vol:/var/lib/mysql image:latest
- Desde Dockerfile
> `VOLUME /app/data`

