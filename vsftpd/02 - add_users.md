# add a user
# add user, make a sudoer
cat /etc/vsftpd.userlist
sudo -s
sudo useradd -s /bin/bash -d /home/user/ -m -G sudo user
passwd user
sudo chown root:root /etc/vsftpd.userlist
sudo echo "user" >> /etc/vsftpd.userlist
cat /etc/vsftpd.userlist
sudo cp -r ~/.ssh /home/user/.ssh
sudo systemctl restart vsftpd
sudo systemctl status vsftpd

# add a vftp user named ftps
cat /etc/vsftpd.userlist
sudo -s
sudo useradd -s /bin/bash -d /home/ftps/ -m -G sudo ftps
passwd ftps
sudo chown -R ftps:ftps /home/ftps/
sudo chown root:root /etc/vsftpd.userlist
sudo echo "ftps" >> /etc/vsftpd.userlist
cat /etc/vsftpd.userlist
sudo cp -r ~/.ssh /home/ftps/.ssh
sudo systemctl restart vsftpd
sudo su ftps
sudo chown -R ftps:ftps /var/www/html
sudo chmod -R 777 /var/www/html

# from another remote machine, generate a key
cd ~/.ssh
ssh-keygen
  (specify no filename and no password)
  (this will generate a new key named id_rsa and id_rsa.pub files)
cat ~/.ssh/id_rsa.pub | ssh -i ~/.ssh/git git@jaedns.com "cat >> ~/.ssh/authorized_keys"