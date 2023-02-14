# port 80, 443

# install apache2
sudo apt install apache2

# get the public ip address
sudo apt-get install curl
curl http://icanhazip.com
curl -4 icanhazip.com

# change foder of index.html, -> /reactjs/build
sudo nano /etc/apache2/apache2.conf
Directory /reactjs/build>
        Options Indexes FollowSymLinks
        AllowOverride All
        Order deny,allow
        Allow from all
        Require all granted
</Directory>
ctrl-x, y enter

# own the folder
sudo chown -R root:root /reactjs/build

# make the folder full access
sudo chmod -R 777 /reactjs/build

# buy a domain name and email address from godaddy.com domain registrar, ex. jaedns.com
    goto https://dcc.godaddy.com/manage/jaedns.com/dns, to
    copy the MX values in DNS entries,
        0   smtp.secureserver.net
        10  mailstore1.secureserver.net
    change the default domain name server to azure domain name servers
        ns1-33.azure-dns.com
        ns2-33.azure-dns.net
        ns3-33.azure-dns.org
        ns4-33.azure-dns.info

# install https certifcates / ssl
apt install snapd
sudo snap install core; sudo snap refresh core
sudo apt remove certbot
sudo snap install --classic certbot
sudo certbot --apache
    # input your email address and website url to have ssl
sudo certbot renew --dry-run