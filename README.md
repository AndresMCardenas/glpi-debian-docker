# GLPI con Docker compose

*Paso 1* clonar este repositorio

*Paso 2* 
Se debe esta en modo rut y se procede a instalar docker y docker-compose con los siguientes comandos

apt-get update

apt-get upgrade

apt-get install curl wget

apt-get install ca-certificates curl

install -m 0755 -d /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc

chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \ tee /etc/apt/sources.list.d/docker.list > /dev/null

apt-get update

apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose

*Paso 3* 
se continua con el la instalacion de GLPI usando el archivo docker-compose y en mysql.env del repositorio ejecuntando el siguente comandos

docker compose up -d

ya se puede acceder desde la ip del servidor y en el puerto configurado en el archivo docker-compose.yml que por defecto es el 8200

### Configurando GLPI

*Paso 4*
accediendo a GLPI y congiruando la base de datos 
host: mysql, usuario: glpi, contraseña: glpi

Los usuarios / contraseñas predeterminadas son:

glpi/glpi para la cuenta de administrador tech/tech para la cuenta de técnico normal/normal para la cuenta normal post-only/postonly para la cuenta de sólo lectura

*opcional* 
Puedes suprimir o modificar estas cuentas así como los datos iniciales.