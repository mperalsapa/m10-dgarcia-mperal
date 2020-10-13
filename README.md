# m10-dgarcia-mperal
Pràctiques m10

https://guides.github.com/features/mastering-markdown/

# Securitzar Instal·lació
Canviem la contrasenya
```sudo passwd root```<br>
Actualitzem el OS
```sudo yum check-update```
```sudo yum update```

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
- A on es troba i quin nom rep el fitxer de configuració del SGBD Percona Server?
Es troba a ```/etc``` i el fitxer es ```my.conf```
- A on es troben físicament els fitxers de dades (per defecte). Com ho has sabut?
Els fitxers de dades es troben a ```/var/lib/mysql```, aixo ho indica en el fitxer de configuracio.
- Crea un usuari anomenat asix en el sistema operatiu i en SGBD de tal manera que aquest usuari del sistema operatiu no hagi d'introduir l'usuari i password cada vegada que cridem al client mysql?
		http://dev.mysql.com/doc/refman/5.7/en/password-security-user.html
		Usuari SO-→ asix / patata
		Usuari MySQL → asix / patata

- El servei de MySQL (mysqld) escolta al port 3306. Quina modificació/passos caldrien fer per canviar aquest port a 33306 per exemple? 
Important: No realitzis els canvis. Només indica els passos que faries.
- nsenya al professor que us podeu connectar al SGBD.


# MySQL
## Instal·lar repositori MySQL
Descarregar el repositori <br>```wget https://repo.mysql.com/mysql80-community-release-el7-1.noarch.rpm```<br><br>
Instal·lar el repositori <br>```yum localinstall mysql80-community-release-el7-1.noarch.rpm```<br><br>
Verifiquem que s’ha afegit correctament <br>```yum repolist enabled | grep "mysql.*-community.*"```<br><br>
## Instal·lar MySQL
Instal·lar
<br>```yum install mysql-community-server```<br>
![Instal·lant](https://github.com/mperalsapa/m10-dgarcia-mperal/blob/master/Captura%20de%20pantalla%202020-10-05%20174927.png)

## Securitzar
[Securitzar](https://github.com/mperalsapa/m10-dgarcia-mperal/blob/master/README.md#securitzar) la instal·lacio MySQL

## Comprovacions
Accedim al servei per comprvar que funciona correctament.<br>
![Comprovacio access mysql](https://i.imgur.com/wGJPvDx.png)<br>
Comprovem la versio instal·lada ```mysql --version```<br>
![Comprovacio](https://i.imgur.com/bnqtVen.png)<br>
I que esta donant servei ```systemctl status mysql```<br>
![Status de MySQL](https://i.imgur.com/fd40eUe.png)<br><br>
P@t@t@m10
