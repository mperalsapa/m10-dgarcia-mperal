# mongodb
## Instal·lar mongodb
### Configurarem el sistema d'administració de paquets
Crearem aquest fitxer ```/etc/yum.repos.d/mongodb-org-4.4.repo``` i guardarem el següent text.
```
[mongodb-org-4.4]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/4.4/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-4.4.asc
```
### Instal·lar el paquet
Instal·larem amb ```sudo yum install -y mongodb-org```<br>
![Instal·lacio de paquet completada](https://i.imgur.com/4fBkd9m.png)

## Iniciar i comprovar el servei
Per iniciar el servei executem '''sudo systemctl start mongod'''
Si l'anterior comanda no ha funcionat, executa aquesta abans '''sudo systemctl daemon-reload'''<br
Verificarem que el servei està funcionant amb '''sudo systemctl status mongod'''
![verificació del procés](https://i.imgur.com/xQtsehW.png)

## Obrir el firewall
Per poder accedir al servei hem de configurar el firewall del sistema per permetre connexions a la base de dades.
```
sudo firewall-cmd --zone=public --add-port=27017/tcp --permanent
sudo firewall-cmd --reload
```
## Protegir
Crearem un usuari admin accedint a la base de dades des del servidor.

Executem la comanda '''mongo''' i desprès seleccionem la base "admin" amb '''use admin;'''.

Ara inserim el nou usuari
```
db.createUser({
user: "admin",
pwd: "Patata",
roles: [
{ role: "userAdminAnyDatabase", db: "admin" },
{ role: "readWriteAnyDatabase", db: "admin" },
{ role: "dbAdminAnyDatabase", db: "admin" }
]
});
```
Afegirem la seguent linia en aquest fitxer '''/etc/mongod.conf'''
'''
security:
authorization: 'enabled'
'''
I per accedir des de fora, hem de modificar la direcció del servei, de 127.0.0.1 a 0.0.0.0
'''
net:
port: 27017
bindIp: 0.0.0.0 #default value is 127.0.0.1
'''
I reiniciem el servei per carregar els canvis a la configuració
'''systemctl restart mongod'''

Una vegada fet lo anterior ja podem accedir a traves de xarxa.
![mongodb compass](https://i.imgur.com/QO0oGrF.png)

## Connectar amb la base de dades
Per connectar hem de fer servir el programari de mongo. Oficialment es pot fer amb comandes o amb un programa gràfic.
Ens descarregarem el programa gràfic des de aquest [enllaç](https://www.mongodb.com/try/download/compass)
Una vegada instal·lat en l'apartat de "New connection" fem clic a "Fill in connection fields individually"
I a qui afegim les dades de la connexió al servidor, com la ip, el port, i el usuari amb la contrasenya.
![credencials](https://i.imgur.com/gKOjuHb.png)
