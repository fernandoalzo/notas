# notas erre
 repositorio con notas

## DOCKER

docker-compose yaml file example:
```
# este numero de version no es importante, puede ser cualquiera
version: '3.3'
# servocios que se van a cargar
services:
  # nombre del servicio que se iniciara, puede ser cualquiera, como ejemplo se usa postgres 
  postgres:
  # version de la aplicacion que se quiere instalar
    image: postgres:13
    environment:
      - POSTGRES_DB=my_db
      - POSTGRES_USER=root
      - POSTGRES_PASSWORD=12345
    ports:
      - '5432:5432'
    # con esta definicion se agrega persistencia a los datos.
    volumes:
      - ./postgres_data:/var/lib/postgresql/data
  # installacion de pgadmin para la administracion de la base de datos desde un entorno grafico
  pgadmin:
    image: dpage/pgadmin4

    environment:
      - PGADMIN_DEFAULT_EMAIL=rrr@admin.com
      - PGADMIN_DEFAULT_PASSWORD=root
    # el servicio de pgadmin por default escucha solicitudes por el puerto 80, pero yo lo voy a gestionar desde el puerto 5050
    ports:
      - "5050:80"
```

```powershell
#create a docker image from YAML file 
#in same directory of .yml file run:
docker-compose up -d containerName
#check container process
docker-compose up -d postgres
#stop container
docker-compose down
```

## NESTJS NEST.JS
```powershell
#install nestjs
npm i -g @nestjs/cli
#check nest version
nest --version
#nest manual
nest --help

#create new project
nest new projectName
#create new project inside folder previously create
nest new .
#run project
npm run start
#run project in developer mode with autoreload
npm run start:dev

#create controllers
nest g controller controllerName
# create controller with no subfolder
nest g controller controllerName --flat

#create services
nest g s serviceName
# create service with no subfolder
nest g s serviceName --flat

# create modules
nest g mo moduleName

#install validator
npm i class-validator class-transformer
#install mapped-types
npm i mapped-types
# install config module
npm i @nestjs/config
#install swagger for autodocumentation
npm install --save @nestjs/swagger swagger-ui-express
```

## postgresql
```powershell
#ingresar a postgres
psql.exe -U postgress
#list databases
\l
#create database
CREATE DATABASE dataBaseName
#connect to database
\c dataBaseName
#list tables
\dt
#show especification for table
\d tableName
#delete database 
drop database dataBaseName

#backup database
pd_dump -U userName dataBaseName > dataBaseNameCopy.sql
#restore database
psql -U userName dataBaseName < dataBaseNameCopy.sql

#change user password
ALTER USER userName WITH PASSWORD newPassword
```