# Redes Docker
## Conceptos
Supongamos que disponemos de 2 componentes:
- Una aplicación Flask donde servir HTML y gestionar peticiones
- Una base de datos para ofrecer la información

La primera duda que nos aborda es
> Quien debe poder acceder a la base de datos?

La respuesta es que **solo el backend** debería poder acceder

Por tanto aprovachamos que los contenedores están aislados entre sí para mantener las responsabilidades separadas.

Pero, como hacemos esto en Docker? Generando **redes internas**. Las redes internas indican que los contenedores son visibles entre ellos siempre y cuando residan en la misma red, haciendo incluso más fácil su referenciación, como veremos más adelante
## Comandos
- Crear Red

> ```docker network create mi-red-local```

- Indicar en el comando **run** que red queremos usar
> `docker run -d --name mysql-db --network mi-red-local -e MYSQL_ROOT_PASSWORD=secret mysql:9-slim`

- Para contenedores ya instanciados, también se les puede conectar una red
> `docker network connect mi-red-local mysql-db`

## Ejercicio
- Desplegad 2 containers: 1 con la aplicación flask y otro con una imagen de MySQL o MariaDB
- Cread una red de nombre `my-first-net`
- Connectad ambos contenedores a dicha red
- Cambiad las configuraciones de entorno
    - Está es la parte más importante!! Tened en cuenta que, el `DATABASE_HOSTNAME` debé ser **nombre del contenedor de la base de datos** y las credenciales del usuario también debe coincidir con las credenciales del contenedor

