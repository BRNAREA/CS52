sudo pacman -S mariadb php php-apache

seus projetos ficarao salvos em /srv/http\


agora ative os servicos http : 
sudo systemctl enable httpd
sudo systemctl start httpd
sudo gedit /etc/httpd/conf/httpd.conf

agora para instalar mariadb

sudo mariadb-install-db --user=mysql --basedir=/usr --datadir=/var/lib/mysql

instalado. agora vamos configurar

sudo systemctl enable mariadb
sudo systemctl start mariadb

agora que configurar e ligamos

vamos setar uma senha pro nosso banco ksksk

sudo systemctl stop mariadb

---
sudo mysqld_safe --skip-grant-tables --skip-networking
mysql -u root

para criar usuario 

mysql -u root -p

agora que criamos

mysql_secure_installation

instale o phpmyadmin 

sudo pacman -S phpmyadmin
sudo gedit /etc/httpd/conf/extra/phpmyadmin.conf
sudo gedit /etc/httpd/conf/httpd.conf

# phpMyAdmin configuration
Include conf/extra/phpmyadmin.conf

sudo gedit /etc/php/php.ini