![Header](header-doc.png)


# Resurgentes - Instalación (Desarrollo)

La instalacion requiere de instalar 2 repositorios.
Para eso, ubicados en la carpeta donde les gustaria clonar los repos, supongamos una carpeta `/dev` hacen en la terminal:

```bash
$ cd dev

dev/:$ git clone https://github.com/DemocraciaEnRed/asambleasclimaticas-web
dev/:$ git clone https://github.com/DemocraciaEnRed/asambleasclimaticas-api
```

Una vez hecho, hay que hacer un "Setup" de cada una de los repositorios que acabamos de clonar.

### Setup asambleasclimaticas-api

Ir a la carpeta del repo y instalar las dependencias.

```bash
dev/:$ cd asambleasclimaticas-api
dev/asambleasclimaticas-api:$ npm install
```

Ahora tenemos que crear un archivo `.env` que son nuestras variables de entorno

```bash
PORT=3000
APP_URL=http://localhost:4000
MONGODB_URL=#############
JWT_SECRET=#############
MAILER_FROM==#############
MAILER_HOST=#############
MAILER_PORT=#############
MAILER_USER=#############
MAILER_PASSWORD=#############
```

Comando para ejecutar mongodb y la aplicación:

```bash
dev/asambleasclimaticas-api:$ ./run-dev.sh
```


### Setup asambleasclimaticas-web

Ir a la carpeta del repo y instalar las dependencias.

```bash
dev/:$ cd asambleasclimaticas-web
dev/asambleasclimaticas-web:$ npm install
```

Ahora tenemos que crear un archivo `.env` que son nuestras variables de entorno

```bash
NEXT_PUBLIC_APIURL=http://localhost:3000
NEXT_PUBLIC_PROJECTID=pacto-inter-ciudad
```

Comando para ejecutar:

```bash
dev/asambleasclimaticas-web:$ npm run dev
```