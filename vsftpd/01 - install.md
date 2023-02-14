# port 20, 21, 990
# port range 40000-50000

sudo apt update
sudo apt install vsftpd -y
sudo nano /etc/vsftpd.conf
    listen=YES
    anonymous_enable=YES
    local_enable=YES
    write_enable=YES
    local_umask=022
    dirmessage_enable=YES
    use_localtime=YES
    xferlog_enable=YES
    connect_from_port_20=YES
    chown_uploads=YES
    chown_username=root
    async_abor_enable=YES
    ftpd_banner=Welcome to blah FTP service.
    ls_recurse_enable=YES
    secure_chroot_dir=/var/run/vsftpd/empty
    pam_service_name=vsftpd
    rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
    rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
    ssl_enable=YES
    allow_writeable_chroot=YES
    allow_anon_ssl=NO
    force_local_data_ssl=NO
    force_local_logins_ssl=NO
    ssl_tlsv1=YES
    ssl_sslv2=YES
    ssl_sslv3=YES
    utf8_filesystem=YES
    pasv_min_port=40000
    pasv_max_port=50000
    local_root=/var/www/html/
    userlist_enable=YES
    userlist_file=/etc/vsftpd.userlist
    userlist_deny=NO
    chroot_list_enable=NO

cat /etc/vsftpd.conf
sudo touch /etc/vsftpd.userlist
sudo systemctl enable vsftpd
sudo systemctl start vsftpd
sudo systemctl restart vsftpd
sudo systemctl status vsftpd


