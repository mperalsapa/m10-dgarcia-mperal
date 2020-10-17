# Percona for MySQL
## Instal·lar repositori Percona
Instal·lem el repositori amb ```sudo yum install https://repo.percona.com/yum/percona-release-latest.noarch.rpm```<br>
Habilitem el repositori ```sudo percona-release setup ps80```
## Instal·lar el servei
Executem ```sudo yum install percona-server-server``` per instal·lar.

## Securitzar
Ara toca securitzar la instal·lacio de mysql<br>
En el moment en el que instal·lem el MySQL, ens genera una contrasenya i la guarda en un fitxer.<br>
Aquesta la podem trobar amb ```grep 'temporary password' /var/log/mysqld.log```<br>
Una vegada coneixem aquesta password, començem amb el proces de securitzacio amb ```mysql_secure_installation```<br>
![securitzacio](https://i.imgur.com/Sdrn8rO.png)<br>
![securitzacio segona part](https://i.imgur.com/jPNA19Q.png)<br>

## Comprovacions
Comprovem que el servei esta funcionant
![status percona](https://i.imgur.com/CqukLNy.png)<br>
Comprovem que es pot accedir al mysql<br>
![accedit al mysql](https://i.imgur.com/0JZ38fC.png)

- Quines són les instruccions per arrancar / verificar status / apagar servei de la base de dades de Percona Server en el CentOS 7<br>
```systemctl [ status | start | stop ] mysql```
- A on es troba i quin nom rep el fitxer de configuració del SGBD Percona Server?<br>
Es troba a ```/etc``` i el fitxer es ```my.conf```
- A on es troben físicament els fitxers de dades (per defecte). Com ho has sabut?<br>
Els fitxers de dades es troben a ```/var/lib/mysql```, aixo ho indica en el fitxer de configuracio.
- Crea un usuari anomenat asix en el sistema operatiu i en SGBD de tal manera que aquest usuari del sistema operatiu no hagi d'introduir l'usuari i password cada vegada que cridem al client mysql?
		http://dev.mysql.com/doc/refman/5.7/en/password-security-user.html
		Usuari SO-→ asix / patata
		Usuari MySQL → asix / patata

- El servei de MySQL (mysqld) escolta al port 3306. Quina modificació/passos caldrien fer per canviar aquest port a 33306 per exemple? 
Important: No realitzis els canvis. Només indica els passos que faries.
Hauriem de modificar el fitxer ```/etc/my.cnf``` i afegir les seguents linies<br>
```
[client]
port = 33456

[mysqld]
port = 33456
```
Per poder connectar-nos des de l'exterior hem d'obrir el firewall amb el port de MySQL.<br>
```sudo firewall-cmd --zone=public --add-service=mysql --permanent```

A l'hora de connectar-se des de l'exterior, ens diu que no tenim permís.
![error de autenticacio](https://i.imgur.com/7I8sMmu.png)<br>

Per poder accedir des de una xarxa externa hem de afegir un usuari amb permisos de
connexio externa farem servir la seguent comanda
```create user 'usuariPatata' identified by 'P@t@t@m10';```


Ara donarem permisos a aquest usuari per modificar qualsevol base de dades desde qualsevol IP. Aixo no s'hauria de fer mai, pero estem en un entorn de proves, i ens fara el treball mes fàcil.<br>
```GRANT ALL PRIVILEGES ON * . * TO 'usuariPatata'@'%';```
