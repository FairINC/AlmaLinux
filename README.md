# AlmaLinux
Things relating to Alma RHEL stuff. 


Here is the initial setup code for bashing a FREEIPA instance together. 

umask 0022 && sudo -E bash -c 'systemctl stop dirsrv.target pki-tomcatd@pki-tomcat.service 2>/dev/null || true; fuser -k 389/tcp 636/tcp 2>/dev/null || true; rm -rf /dev/shm/slapd-LAN-FQDN-COM /run/lock/dirsrv/slapd-LAN-FGDN-COM; rm -rf /var/lib/pki/pki-tomcat /etc/pki/pki-tomcat /var/log/pki/pki-tomcat /var/lib/ipa /etc/ipa /var/lib/ipa-client /etc/dirsrv/slapd-* /var/lib/dirsrv/slapd-*; mkdir -p /var/lib/pki/pki-tomcat /etc/pki/pki-tomcat /var/log/pki/pki-tomcat /var/lib/ipa/sysrestore /var/lib/ipa/sysupgrade /var/lib/ipa/pki-ca /etc/ipa/custodia /var/lib/ipa-client/sysrestore; chown -R pkiuser:pkiuser /var/lib/pki/pki-tomcat /etc/pki/pki-tomcat /var/log/pki/pki-tomcat; chmod -R 755 /var/lib/ipa /etc/ipa /var/lib/pki; ipa-server-install --setup-dns --unattended --domain=lan.fqdn.com --realm=LAN.FQDN.COM--ds-password="PASSWORD" --admin-password="PASSWORD2" --forwarder=1.1.1.1 --forwarder=8.8.8.8 --ntp-server=0.pool.ntp.org --ntp-server=1.pool.ntp.org --netbios-name=GREATDEKU --ip-address=192.168.X.X -v'
