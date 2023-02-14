# check the ports being listened to
sudo netstat -tulpn | grep LISTEN
sudo ss -lnpt

# check the routing table
sudo netstat -r

# get public IP addresses
curl icanhazip.com

# check NIC local IP addresses
ip a

# check free memory
htop
free -h

# check file disks
df -h --total

# logout
exit

# delete user
sudo deluser --remove-home user_name
sudo deluser --remove-home ftp

# change user
sudo su user_name

# change to root
sudo -s

# add user, make a sudoer
sudo -s
sudo useradd -s /bin/bash -d /home/user_name/ -m -G sudo user_name
passwd user_name
sudo su user_name

# goto user home folder
cd ~

# create a folder
sudo mkdir new_folder

# delete a folder recursively
sudo rm -r new_folder

# own a folder
sudo chown -R user:user /some/folder/name

# make a folder full access
sudo chmod -R 777 /some/folder/name

# find a file
find . -name garry.txt

# create a file
sudo touch some.file

# append a text inside a file
sudo echo "some text" >> some.file

# append a file content to a file
sudo cat source.file >> destination.file

# copy local files
sudo cp source.file destination.file

# copy local folder
sudo cp -r source.folder destination.folder

# copy local file to remote file of same name
scp source.file username@some.host:source.file

# copy local folder to remote folder
scp -r sourceFolder username@some.host:source.folder

# download file from the internet
wget https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.17.2.tar.xz

# make a scheduled task (CRON JOBS) - run 300ms after start up
sudo crontab -e
    # select 1 nano
        @reboot sleep 300 && date >> ~/date.txt
        # ctrl-x y enter
sudo systemctl enable cron.service
sudo systemctl start cron.service
sudo systemctl status cron.service

# create command alises
sudo nano nano /etc/bash.bashrc
    # Aliases by Garry  Cacho
    alias gs='git status'
    alias ga='git add .'
    alias gc='git commit -m'
    alias gcb='git checkout -b'
    alias gco='git checkout'
    alias gp='git push origin'
    alias gpl='git pull'
    alias t='touch'
    alias a='php artisan'
    alias e='echo'
#ctrl-x y enter

# check all services runnin
sudo service --status-all

# see machine name 
hostnamectl

# change machine name 
sudo hostnamectl set-hostname my-laptop
sudo hostnamectl set-hostname www.jaed.tech
sudo hostnamectl set-hostname gem.jaed.tech

# scan all machine in network
sudo apt-get install arp-scan -y
# if using Wi-Fi:
sudo arp-scan -l --interface=wlan0
# -or if using ethernet:
sudo arp-scan -l --interface=eth0
# for all localnet
sudo arp-scan --localnet
sudo arp-scan -l
