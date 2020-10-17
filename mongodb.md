# mongodb
## Instal·lar mongodb
### Configurarem el sistema de administracio de paquets
Crearem aquest fitxer ```/etc/yum.repos.d/mongodb-org-4.4.repo``` i guardarem el seguent text.
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

## Iniciar i comprobar el servei
Per iniciar el servei executem ```sudo systemctl start mongod```<br>
Si l'anterior comanda no ha funcionat, executa aquesta avans ```sudo systemctl daemon-reload```<br
Verificarem que el servei esta funcionant amb ```sudo systemctl status mongod```
![verificacio del process](https://i.imgur.com/xQtsehW.png)
## Obrir el firewall
Per poder accedir al servei hem de configurar el firewall del sistema per permetre conexions a la base de dades.
```
sudo firewall-cmd --zone=public --add-port=27017/tcp --permanent
sudo firewall-cmd --reload
```
## Securitzar
Crearem un usuari admin accedint a la base de dades des del servidor.<br>
Executem la comanda ```mongo``` i despres seleccionem la base "admin" amb ```use admin;```.<br>
Ara inserim el nou usuari
```
db.createUser({
      user: "admin",
      pwd: "Patata",
      roles: [
                { role: "userAdminAnyDatabase", db: "admin" },
                { role: "readWriteAnyDatabase", db: "admin" },
                { role: "dbAdminAnyDatabase",   db: "admin" }
             ]
  });
```
Afegirem la seguent linia en aquest fitxer ```/etc/mongod.conf```
```
security:
        authorization: 'enabled'
```
I per accedir des de fora, hem de modificar la direccio del servei, de 127.0.0.1 a 0.0.0.0
```
net:
    port: 27017
    bindIp: 0.0.0.0   #default value is 127.0.0.1
```
I reiniciem el servei per carregar els canvis a la configuracio
```systemctl restart mongod```

Una vegada fet lo anterior ja podem accedir a traves de xarxa.
![mongodb compass](https://i.imgur.com/QO0oGrF.png)

## Connectar amb la base de dades
Per connectar hem de fer servir el programari de mongo. Oficialment es pot fer amb comandes o amb un programa grafic.<br>
Ens descarregarem el programa grafic des de aquest ![enllaç](https://www.mongodb.com/try/download/compass)<br>
Una vegada instal·lat en l'apartat de "New connection" fem clic a "Fill in connection fields individually"<br>
I aqui afegim les dades de la connexio al servidor, com la ip, el port, i el usuari amb la contrasenya.
![credencials](https://i.imgur.com/gKOjuHb.png)
