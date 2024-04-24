![Header](header-doc.png)


# Resurgentes - Instalación (Producción)

En este repositorio encontrarás el [docker-compose.yml](docker-compose.yml) y un archivo ejemplo de las variables de entorno que necesitan los componentes `example.env`. 

Primero debes generar el archivo de las variables de entorno partiendo `example.env`.

```bash
cp example.env .env
```

Luego correr `docker-compose up` para descargar las imagenes, crear y correr los containers. Luego se puede acceder a la web desde [https://localhost:4000](https://localhost:4000)

Este comando correrá los cuatro contenedores de docker necesarios para el funcionamiento del sistema. Para verlos `docker ps`

```bash
CONTAINER ID   IMAGE                                                            COMMAND                  CREATED              STATUS         PORTS                                           NAMES
f010a9dfc0a0   ghcr.io/democraciaenred/asambleasclimaticas-api:1.0.1            "docker-entrypoint.s…"   About a minute ago   Up 8 seconds   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp       asambleasclimaticas-api-1
f0e7ae7747c4   ghcr.io/democraciaenred/asambleasclimaticas-api:1.0.1            "docker-entrypoint.s…"   About a minute ago   Up 8 seconds   0.0.0.0:5000->3000/tcp, :::5000->3000/tcp       asambleasclimaticas-queue-1
1e1446305124   mongo:3.6                                                        "docker-entrypoint.s…"   About a minute ago   Up 8 seconds   0.0.0.0:27017->27017/tcp, :::27017->27017/tcp   asambleasclimaticas-mongo-1
7ebb11c55f39   ghcr.io/democraciaenred/asambleasclimaticas-web:1.0.0-beta11.4   "docker-entrypoint.s…"   About a minute ago   Up 8 seconds   0.0.0.0:4000->4000/tcp, :::4000->4000/tcp       asambleasclimaticas-web-1

```
Para conocer el uso y los límites de recursos de los contenedores utilizar el comando `docker stats`

```bash
CONTAINER ID   NAME             CPU %     MEM USAGE / LIMIT     MEM %     NET I/O       BLOCK I/O         PIDS
f010a9dfc0a0   asambleasclimaticas-api-1     6.99%     96.14MiB / 7.633GiB   1.23%     5.64kB / 0B   0B / 4.1kB        22
f0e7ae7747c4   asambleasclimaticas-queue-1   4.58%     52.03MiB / 7.633GiB   0.67%     5.64kB / 0B   0B / 4.1kB        22
1e1446305124   asambleasclimaticas-mongo-1   0.22%     40.57MiB / 7.633GiB   0.52%     5.64kB / 0B   24.6kB / 53.2kB   24
7ebb11c55f39   asambleasclimaticas-web-1     0.02%     75.69MiB / 7.633GiB   0.97%     5.81kB / 0B   0B / 4.1kB        22
```


Dejamos algunos comandos utiles y su descripción

```bash
# Levantar servicios. Se puede detener si se hace Ctrl+C
$ docker-compose up

# Si los containers siguen corriendo y se quieren detener:
$ docker-compose stop

# Si se quiere eliminar solo los containers
$ docker-compose rm

# Si se quiere eliminar todo lo que el comando "up" inicializo (containers, volumenes, imagenes, etc)
$ docker-compose down
```

