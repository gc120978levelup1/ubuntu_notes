# port 22

apt install ssh

# login to another machine
ssh user@machineAddress

# login using azure,aws,gpc account, with private key made by the platform
ssh -i ~/.ssh/private_key.pem user@machineAddress

# enable root login, in order to listen to tunnel to previleged port (below  1024)
sudo -s
nano /root/.ssh/authorized_keys
   # delete everything before command ssh-ed25519, save file, exit
nano /etc/ssh/sshd_config
        PermitRootLogin without-password
        GatewayPorts yes
        AllowTcpForwarding yes
        TCPKeepAlive yes
systemctl restart ssh.service
systemctl status ssh.service

# add new authorized_keys to the root, from the other windows workstation
cd ~/.ssh
ssh-keygen
  (specify no filename and no password)
  (this will generate a new key named id_rsa and id_rsa.pub files)
cat ~/.ssh/id_rsa.pub | ssh -i ~/.ssh/private_key.pem root@jaedns.com "cat >> ~/.ssh/authorized_keys"
ssh root@jaedns.com

# Remote Port Forwarding, let local machine accessable to the public internet via jaedns.com
ssh -N -o ServerAliveInterval=20 -R jaedns.com:80:192.168.1.122:80 root@jaedns.com &
ssh                              -R [REMOTE:]REMOTE_PORT:DESTINATION:DESTINATION_PORT [USER@]SSH_SERVER


# Local Port Forwarding, let remote machine jaedns.com accessable to the private netwrok via 192.168.1.122
ssh -N -o ServerAliveInterval=20 -L 192.168.1.122:80:jaedns.com:80 root@jaedns.com &
ssh                              -L [LOCAL_IP:]LOCAL_PORT:DESTINATION:DESTINATION_PORT [USER@]SSH_SERVER &

# check the port being listened to
netstat -tulpn | grep LISTEN


