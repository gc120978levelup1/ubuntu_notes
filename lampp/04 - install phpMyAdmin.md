sudo apt install phpmyadmin apache2-utils php-mbstring php-zip php-gd
   > select Apache2 for the server by pressing space bar
   > yes to configure database for phpmyadmin
   > enter mysql password for phpmyadmin
   > enter password to login to phpmyadmin, usually the same as above

sudo phpenmod mbstring
sudo systemctl restart apache2
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
sudo a2enconf phpmyadmin
sudo systemctl restart apache2

sudo nano /etc/phpmyadmin/apache.conf
    # search <Directory /usr/share/phpmyadmin> ... add below ... DirectoryIndex index.php 
    AllowOverride All
    #ctrl-x y enter

sudo nano /usr/share/phpmyadmin/.htaccess
    AuthType Basic
    AuthName "Restricted Files"
    AuthUserFile /etc/phpmyadmin/.htpasswd
    Require valid-user
    #ctrl-x y enter

sudo htpasswd -c /etc/phpmyadmin/.htpasswd user
    enter password, user

sudo htpasswd -c /etc/phpmyadmin/.htpasswd root
    enter password, root

sudo systemctl restart apache2


