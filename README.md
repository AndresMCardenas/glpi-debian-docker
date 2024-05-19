# GLPI con Docker compose

*Paso 1* 

Actualizar repositorios y dependencias

apt-get update

apt-get upgrade

*Paso 2*

se instalan paquetes necesarios

apt-get install curl wget git gpg

clonar este repositorio

*Paso 3* 

clonar este repositorio

git clone https://github.com/AndresMCardenas/glpi-debian-docker.git

*Paso 4* 

Se debe esta en modo rut y se procede a instalar docker y docker-compose con los siguientes comandos

apt-get install ca-certificates curl

install -m 0755 -d /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg

chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \ tee /etc/apt/sources.list.d/docker.list > /dev/null

apt-get update

apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose

*Paso 5*

se continua con el la instalacion de GLPI usando el archivo docker-compose y en mysql.env del repositorio ejecuntando el siguente comandos

nos movemos a la carpeta del repositorio

cd glpi-debian-docker

se levanta el contenedor y los servicios

docker compose up -d

ya se puede acceder desde la ip del servidor y en el puerto configurado en el archivo docker-compose.yml que por defecto es el 8200

### Configurando GLPI

*Paso 6*
accediendo a GLPI y congiruando la base de datos 
host: mysql, usuario: glpi, contraseña: glpi

Los usuarios / contraseñas predeterminadas son:

glpi/glpi para la cuenta de administrador tech/tech para la cuenta de técnico normal/normal para la cuenta normal post-only/postonly para la cuenta de sólo lectura

*opcional* 
Puedes suprimir o modificar estas cuentas así como los datos iniciales.