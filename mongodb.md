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
Afegirem la seguent linia en aquest fitxer ```/etc/mongod.conf```
```
security:
        authorization: 'enabled'```
