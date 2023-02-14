# install php and dependencies
sudo apt install php libapache2-mod-php php-mcrypt php-mysql
sudo nano /etc/apache2/mods-enabled/dir.conf
    <IfModule mod_dir.c>
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
    </IfModule>
    #ctrl-x y enter
sudo apt install php-curl php-json php-cgi
sudo systemctl restart apache2