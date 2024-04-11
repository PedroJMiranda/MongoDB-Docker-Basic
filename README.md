# MongoDB-Docker-Basic
Tutorial siemple para configurar un contenedor utilizando MongoDB mediante Docker.

A continuación te dejo un paso a paso, para lo cual debes de tener en cuenta lo siguente: 

## **1.- Vamos a Crear documento de docker-compose**

**Paso 1: Crea un nuevo archivo llamado docker-compose.yml usando el comando touch:**
```
touch docker-compose.yml
```

## Paso 2: Edita el archivo con tu editor de texto favorito e ingresa el siguiente contenido:
```
version: '2.2'

services:

mongo:
  image: mongo:4.0.4
  restart: always
  container_name: monguito
  environment:
    - MONGODB_USER="user"
    - MONGODB_PASS="pass"	
  
  volumes:
    - ./monguitodata:/data/db
    - ./monguitodata/log:/var/log/mongodb/
  ports:
    - "27017:27017"

```
### Nota:

- Reemplaza "usuario" y "contraseña" por tu nombre de usuario y contraseña deseados para MongoDB.
* Puedes modificar la versión de MongoDB a tu gusto.


## **2.- Crear archivos para correr comando en la terminal**
> Selecciona mongo.sh

## **3.- Cargar comandos al archivo creado**
> cat > mongo.sh (Copiar y pegar los comandos que queremos se ejecuten automáticos)

**Paso 1: Crear carpeta para volumen de mongo**
```
mkdir monguitodata

cd monguitodata

mkdir log
```

**Paso 2: Iniciar el contenedor**
```
sudo docker-compose up -d
```
**Paso 3: Mostrar mensaje**
```
echo "Monguito está iniciandose ......."
```
**Paso 4: Entrar en el contenedor**
```
sudo docker exec -it monguito bash
```
## **4.- Salimos del archivo para que se escriba**
> CTRL + D

## **5.- Asignamos permisos de ejecución y ejecutar mongo.sh**
```
chmod u+x mongo.sh
```
```
./mongo.sh
```
## Una vez que tenemos MongoDB corriendo ya podemos probar los comandos básicos:

### Mostrar Bases de datos:
```
show dbs
```
### Crear o ubicarse en una base de datos:
```
use databasename
```
### Saber que base de datos estamos usando:
```
db
```
### Crear colección:
```
db.createCollection('nameCollection')
{"Clave": "Valor"}
```
### Mostrar el contenido de una colección:
```
showCollections
```

## Este tutorial fue hecho por [Pedro Miranda](https://www.linkedin.com/in/pedro-miranda-400a60258/).







