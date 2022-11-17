# notas erre
 repositorio con notas

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
psql -U userName
```