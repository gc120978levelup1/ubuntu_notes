for gcp settings
    @vpc network -> firewall -> create firewall rule -> ingress
        open port imap 993, pop3 995, smtp 465
for azure settings
    @vpc network security group -> inbound security rules
        open port imap 993, pop3 995, smtp 465      
for aws settings
    @vpc security -> security groups -> inbound security rules
        open port imap 993, pop3 995, smtp 465     

# buy a domain name and email address from godaddy.com domain registrar, ex. jaedns.com
    goto https://dcc.godaddy.com/manage/jaedns.com/dns, to
    copy the MX values in DNS entries at godaddy.com domain entries, and put in MX of aws, gcp or azure dns entries
        0   smtp.secureserver.net.
        10  mailstore1.secureserver.net.
    change the godaddy default domain name server for azure domain name servers
        ns1-33.azure-dns.com
        ns2-33.azure-dns.net
        ns3-33.azure-dns.org
        ns4-33.azure-dns.info
    change the godaddy default domain name server for gcp domain name servers
        ns-cloud-c1.googledomains.com
        ns-cloud-c2.googledomains.com
        ns-cloud-c3.googledomains.com
        ns-cloud-c4.googledomains.com
    change the godaddy default domain name server for aws domain name servers
        ns-86.awsdns-10.com
        ns-1674.awsdns-17.co.uk
        ns-1189.awsdns-20.org
        ns-954.awsdns-55.net

for outlook settings
manually configure server settings or additional server types
    imap.secureserver.net @port 993
    smtpout.secureserver.net @ port 465
outlook more settings
    outgoing server
        my outoing server (smtp) requires authentication
            use settings as my incoming server
