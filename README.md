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
# show logs
docker-compose logs /f
# ingresar al contenedor en modo shell para tareas administrativas.
docker-compose exec serviceName bash
# connect to dataBase into the container
# inside the container run:
psql -h localhost -d dbName -U userName
# commando to check all containers actives
docker ps
# container inspection, to show all info about container.
# the containerId can get from command docker ps
docker inspect containerId

# Comandos docker:
#corro el contenedor hello-world
docker run hello-world
# muestra los contenedores activos
docker ps 
# muestra todos los contenedores
docker ps -a 
# muestra el detalle completo de un contenedor
docker inspect <containe ID> 
# igual que el anterior pero invocado con el nombre
docker inspect <name> 
# le asigno un nombre custom “hello-platzi”
docker run –-name hello-platzi hello-world 
# cambio el nombre de hello-platzi a hola-platzi
docker rename hello-platzi hola-platzy 
# borro un contenedor
docker rm <ID o nombre> 
# borro todos lo contenedores que esten parados
docker container prune 
# corre un ubuntu pero lo deja apagado
docker run ubuntu 
# lista todos los contenedores
docker ps -a 
# lo corre y entro al shell de ubuntu -i: interactivo -t: abre la consola
docker -it ubuntu 
 #correo una maquina con debian
Docker run -it debian
# corro un nginx
docker run -d --name proxy nginx 
# apaga el contenedor
docker stop proxy 
# borro el contenedor
docker rm proxy 
# lo para y lo borra
docker rm -f <contenedor> 
# corro un nginx y expongo el puerto 80 del contenedor en el puerto 8080 de mi máquina, # desde mi navegador compruebo que funcione localhost:8080 
docker run -d --name proxy -p 8080:80 nginx 
# veo los logs
docker logs proxy 
# hago un follow del log
docker logs -f proxy 
# veo y sigo solo las 10 últimas entradas del log
docker logs --tail 10 -f proxy 

```

## nodejs
```powershell
#start new project
npm init -y

#install express
npm install express

#install basic libraries for project node 
npm i nodemon eslint eslint-config-prettier eslint-plugin-prettier prettier -D

#install boom for http error handlers
npm install @hapi/boom

#install libraries for data validation 
npm install joi
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
#create class
nest g class busqueda/dtos/busqueda.dto

#create guards
nest g gu auth/guards/[guardName] --flat

#create decorator
nest g d auth/decorators/[decoratorName] --flat

#install mapped-types
npm i '@nestjs/mapped-types'
#install validator
npm i class-validator class-transformer
# install config module
npm i @nestjs/config
#install swagger for autodocumentation
npm install --save @nestjs/swagger swagger-ui-express
#install postgres module an typeorm module
npm install @nestjs/typeorm typeorm
npm install pg
#install bcrypt to hasing passwords
npm i bcrypt
#agregar el tipado
npm i @types/bcrypt -D
#librerias para auth
npm install --save @nestjs/passport passport passport-local
npm install --save-dev @types/passport-local
#install JWT para la creacion de tokens de sesion
npm install --save @nestjs/jwt passport-jwt
npm install --save-dev @types/passport-jwt

# cuando el programa no ecepte cambios es necesario rebuild projext
npm run build
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
pg_dump -U userName dataBaseName > dataBaseNameCopy.sql
#restore database
psql -U userName dataBaseName < dataBaseNameCopy.sql

#change user password
ALTER USER userName WITH PASSWORD newPassword
```


## powershell config haxks
```powershell
#config network adapter
Set-NetIPInterface -InterfaceIndex [interface_index] -IPAddress [ip_address] -PrefixLength [prefijo] -DefaultGateway [gateway]
#to get infor about interfaces, to get interface index
Get-NetAdapter

#set dns server on network adapter
$adapter = Get-NetAdapter -Name ["interface_name"]
Set-DnsClientServerAddress -InterfaceAlias $adapter.Name -ServerAddresses "1.1.1.1","8.8.8.8"
```

## linux config haxks bash
```bash
#config network adapter
#1
sudo ip addr add [ip_address]/[prefijo] dev [Interface_name]
#set defaul GW
sudo ip route add default via [gateway_IP] dev [Interface_name]

#2
sudo ifconfig eth0 192.168.0.10 netmask 255.255.255.0
#set defaul GW
sudo route add default gw 192.168.0.1 eth0

#or editing the /etc/network/interfaces
auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1
```
