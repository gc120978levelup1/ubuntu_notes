# login as root
sudo useradd git
sudo passwd git
usermod -aG sudo git
sudo su git

# generate an ssh access key to this user
cd ~
sudo mkdir .ssh
cd .ssh
touch authorized_keys
ssh-keygen
  (specify no filename and no password)
  (this will generate a new key named id_rsa and id_rsa.pub files)
sudo cat id_rsa.pub > authorized_keys

# show private key
cat id_rsa

# copy the file content and save to local machine as "git" file

# or from another remote machine, generate a key
cd ~/.ssh
ssh-keygen
  (specify no filename and no password)
  (this will generate a new key named id_rsa and id_rsa.pub files)
cat ~/.ssh/id_rsa.pub | ssh -i ~/.ssh/git git@jaedns.com "cat >> ~/.ssh/authorized_keys"

# allow the root user to login without the password
cat ~/.ssh/id_rsa.pub | ssh -i ~/.ssh/webserver.pem root@jaedns.com "cat >> ~/.ssh/authorized_keys"
ssh root@jaedns.com

# create the git project folder
sudo mkdir /git
cd /git
git init --bare my-project.git
sudo chown -R git:git /git/my-project.git

# now from another local machine
git clone git@jaedns.com:/git/my-project.git
cd my-project.git


