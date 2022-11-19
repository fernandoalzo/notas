# notas erre
 repositorio con notas

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