# SIMPLE-WEBAPP
Simple [Golang](https://golang.org/) webapp monolítica

## Pre-Requisitos 📋🔧

- [Docker](https://www.docker.com)

- [Golang](https://golang.org/) 

##  **Deployment (Local)** ⛵

### Bajar dependencias 

```golang
go mod vendor
```

### Levantar base de datos local:

Recursos BD en `/sql` y `/docker-compose.yml`

- Levantar Docker compose para la base de datos 
    ```docker
    docker-compose up
    ```

- Sobre la base de datos levantada ejecutar los Scripts de `/sql`:
    - init_db.sql
    - tables.sql
    - user.sql


Para dev crear TLS certificate en `/tls/generate_cert.sh`

```shell
#!/bin/bash
# dependiendo ubicación instalación del GoSDK
go run Root_GoSDK/src/crypto/tls/generate_cert.go --rsa-bits=2048 
--host=localhost

# Mac Os
# go run /usr/local/go/src/crypto/tls/generate_cert.go --rsa-bits=2048 --host=localhost
```

Para iniciar ejecución: 
```shell
./run.sh
```

```shell
#!/bin/bash
export S_ADDR=":4001"
export S_DSN="webusr:passx123@tcp(localhost:3306)/pastein?parseTime=true"
export S_SECRET="z3Roh+pPbnzHbS*+9Pk8qGWhTzbpa@jf"
go run . -addr=$S_ADDR -dsn=$S_DSN -secret=$S_SECRET
```

### Ayuda configuración:

 ```go
go run . -help
```

## Ejecutando las pruebas ⚙️

- TODO: `/tests`