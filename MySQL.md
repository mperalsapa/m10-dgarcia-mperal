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

-	A on es troben físicament els fitxers de dades?
Els fitxers de dades es troben a ```/var/lib/mysql```
-	A on es troba el fitxer de configuració? Quin és el seu contingut?
Es troba a ```/etc/my.cnf```

-	El procés de mysqld escolta al port 3306. Quina modificació/passos caldrien fer per canviar aquest port a 33306 per exemple? Important: No realitzis els canvis. Només indica els passos que faries.
Hauriem de modificar el fitxer ```/etc/my.cnf``` i afegir les seguents linies<br>
```
[client]
port = 33456

[mysqld]
port = 33456
```

-	Un cop finalitzada la instal·lació i veure que funciona, mostra el resultat de la comanda:<br>
```ps -ef | grep mysql```<br>
![visualitzacio del process](https://i.imgur.com/2yIJhlc.png)

-	Quines són les característiques principals que ofereix MySQL 8.0 enfront de la 5.7.<br>

-- Rols: característica molt emocionant que permet crear rols al servidor MySQL i assignar-los privilegis específics. Aquests rols es poden assignar als usuaris. Per tant, a partir d’ara no haureu de recordar quins permisos necessita un programador de l’equip X i si un QA de l’equip Y necessita el privilegi Z<br>
-	Ensenya al professor que us podeu connectar al SGBD.
