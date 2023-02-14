# install mysql server
sudo apt install mysql-server -y

# change the root account password to root, create a new user 'sa' with password 'sa'
sudo mysql -user root -p
  > enter password, click enter if password is null at first
  > UPDATE mysql.user SET host='%' WHERE user='root' AND host='localhost';
  > ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
  > CREATE USER 'sa'@'%' IDENTIFIED WITH mysql_native_password BY 'sa';
  > GRANT ALL PRIVILEGES ON *.* TO 'sa'@'%' WITH GRANT OPTION;
  > FLUSH PRIVILEGES;
  > SHOW GRANTS FOR 'root'@'%';
  > SHOW GRANTS FOR 'sa'@'%';
  > exit;

# allow mysql remote access from navicat or workbench
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
    bind-address            = 0.0.0.0
    mysqlx-bind-address     = 0.0.0.0
    #ctrl-x y enter
sudo systemctl restart mysql
sudo systemctl status mysql

# make mysql secured 
mysql_secure_installation
  > dont validate the password
  > remove test db
  > allow root to access the database remotely
