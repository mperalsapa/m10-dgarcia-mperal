# MySQL
## Instal·lar repositori MySQL
Descarregar el repositori <br>```wget https://repo.mysql.com/mysql80-community-release-el7-1.noarch.rpm```<br><br>
Instal·lar el repositori <br>```yum localinstall mysql80-community-release-el7-1.noarch.rpm```<br><br>
Verifiquem que s’ha afegit correctament <br>```yum repolist enabled | grep "mysql.*-community.*"```<br><br>
## Instal·lar MySQL
Instal·lar
<br>```yum install mysql-community-server```<br>
![Instal·lant](https://i.imgur.com/3hh51xU.png)

## Protegir
[Protegir](https://github.com/mperalsapa/m10-dgarcia-mperal/blob/master/PERCONA.md#securitzar) la instal·lacio MySQL

## Comprovacions
Accedim al servei per comprvar que funciona correctament.<br>
![Comprovacio access mysql](https://i.imgur.com/wGJPvDx.png)<br>
Comprovem la versio instal·lada ```mysql --version```<br>
![Comprovacio](https://i.imgur.com/bnqtVen.png)<br>
I que esta donant servei ```systemctl status mysql```<br>
![Status de MySQL](https://i.imgur.com/fd40eUe.png)<br><br>

###	A on es troben físicament els fitxers de dades?
Els fitxers de dades es troben a ```/var/lib/mysql```
###	A on es troba el fitxer de configuració? Quin és el seu contingut?
Es troba a ```/etc/my.cnf```

###	El procés de mysqld escolta al port 3306. Quina modificació/passos caldrien fer per canviar aquest port a 33306 per exemple? Important: No realitzis els canvis. Només indica els passos que faries.
Hauriem de modificar el fitxer ```/etc/my.cnf``` i afegir les seguents linies<br>
```
[client]
port = 33456

[mysqld]
port = 33456
```

###	Un cop finalitzada la instal·lació i veure que funciona, mostra el resultat de la comanda:```ps -ef | grep mysql```<br>
![visualitzacio del process](https://i.imgur.com/2yIJhlc.png)

###	Quines són les característiques principals que ofereix MySQL 8.0 enfront de la 5.7.<br>

- Rols: característica molt emocionant que permet crear rols al servidor MySQL i assignar-los privilegis específics. Aquests rols es poden assignar als usuaris.
- Índex invisible: heu volgut mai ocultar un índex que actualment no necessiteu sense deixar-lo caure? Ara pots. Si no esteu segur de si necessiteu un índex, el podeu marcar com a invisible i l’optimitzador MySQL no l’utilitzarà.
- Persistència de la configuració: el canvi de configuració durant el temps d'execució de MySQL es fa habitualment amb SET GLOBAL. Aquest desavantatge en aquesta tècnica és que els canvis no sobreviuran en reiniciar el servidor. aquí ve SET PERSIST al rescat, que fa exactament això, aplicar canvis de configuració que sobreviuen a un reinici del servidor MySQL.
- Conjunt de caràcters i classificació per defecte: a partir de MySQL 8.0, el conjunt de caràcters per defecte serà utf8mb4 i la classificació serà utf8mb4_800_ci_ai.
- Millores UUID: els UUID solen utilitzar-se per generar identificadors únics a les taules. Començant aquesta nova versió, MySQL pot contenir aquests valors en una columna VARBINARY (16) en lloc de CHAR (36). L'impacte d'aquest canvi és un millor ús d'emmagatzematge i millora del rendiment. A més, es van introduir tres noves funcions per gestionar aquests valors UUID: BIN_TO_UUID (), UUID_TO_BIN (), IS_UUID ().
- Millores del model de costos: per primera vegada, el model de costos de MySQL buscarà a la memòria i comprovarà si les dades rellevants de la consulta ja es troben a la memòria. 
- Índexs descendents: ara MySQL permet crear índexs descendents i escanejar-los en un ordre invers, sense penalització de rendiment.
- Expressions de taula comunes: CTE és una nova característica (que ja està disponible en altres bases de dades) que us simplificarà la forma d’escriure consultes complexes. Per dir-ho en paraules simples, mitjançant aquesta funció (la selecció WITH) es crea automàticament una taula temporal entre bastidors, que podeu utilitzar en la mateixa consulta i fer-hi referència.

###	Ensenya al professor que us podeu connectar al SGBD.
