# m10-dgarcia-mperal
Pràctiques m10

https://guides.github.com/features/mastering-markdown/
https://www.percona.com/doc/percona-server/LATEST/installation/yum_repo.html

# Securitzar Instal·lació
Canviem la contrasenya
```sudo passwd root```<br>
Actualitzem el OS
```sudo yum check-update```
```sudo yum update```

# Percona MySQL
## Instal·lar repositori MySQL
Descarregar el repositori <br>```wget https://repo.mysql.com/mysql80-community-release-el7-1.noarch.rpm```<br><br>
Instal·lar el repositori <br>```yum localinstall mysql80-community-release-el7-1.noarch.rpm```<br><br>
Verifiquem que s’ha afegit correctament <br>```yum repolist enabled | grep "mysql.*-community.*"```<br><br>
## Instal·lar MySQL
Instal·lar
<br>```yum install mysql-community-server```<br><br>

