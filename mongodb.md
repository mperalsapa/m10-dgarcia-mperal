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
