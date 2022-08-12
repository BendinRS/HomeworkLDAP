# Домашняя работа "LDAP"

+ Задание: Установить freeIPA

+ Решение:

Скрипт [test.sh](test.sh) разворачивает ВМ и запускает плейбук для настройки сервера

+ Проблемы, c которыми столкнулся:

1. Как в ансибл работать с промежуточными вводными по ходу установки  

+ Решение: чтение документации (Прикрепляю на будущее)

<details>
<summary>man ipa-server-install</summary>

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -U, --unattended      unattended (un)installation never prompts the user
  --uninstall           uninstall an existing installation. The uninstall can
                        be run with --unattended option

  Basic options:
    -p DM_PASSWORD, --ds-password=DM_PASSWORD
                        Directory Manager password
    -a ADMIN_PASSWORD, --admin-password=ADMIN_PASSWORD
                        admin user kerberos password
    --ip-address=IP_ADDRESS
                        Master Server IP Address. This option can be used
                        multiple times
    -n DOMAIN_NAME, --domain=DOMAIN_NAME
                        primary DNS domain of the IPA deployment (not
                        necessarily related to the current hostname)
    -r REALM_NAME, --realm=REALM_NAME
                        Kerberos realm name of the IPA deployment (typically
                        an upper-cased name of the primary DNS domain)
    --hostname=HOST_NAME
                        fully qualified name of this host
    --ca-cert-file=FILE
                        File containing CA certificates for the service
                        certificate files
    --no-host-dns       Do not use DNS for hostname lookup during installation

  Server options:
    --setup-adtrust     configure AD trust capability
    --setup-kra         configure a dogtag KRA
    --setup-dns         configure bind with our zone
    --idstart=IDSTART   The starting value for the IDs range (default random)
    --idmax=IDMAX       The max value for the IDs range (default:
                        idstart+199999)
    --no-hbac-allow     Don't install allow_all HBAC rule
    --no-pkinit         disables pkinit setup steps
    --no-ui-redirect    Do not automatically redirect to the Web UI
    --dirsrv-config-file=FILE
                        The path to LDIF file that will be used to modify
                        configuration of dse.ldif during installation of the
                        directory server instance

  SSL certificate options:
    --dirsrv-cert-file=FILE
                        File containing the Directory Server SSL certificate
                        and private key
    --http-cert-file=FILE
                        File containing the Apache Server SSL certificate and
                        private key
    --pkinit-cert-file=FILE
                        File containing the Kerberos KDC SSL certificate and
                        private key
    --dirsrv-pin=PIN    The password to unlock the Directory Server private
                        key
    --http-pin=PIN      The password to unlock the Apache Server private key
    --pkinit-pin=PIN    The password to unlock the Kerberos KDC private key
    --dirsrv-cert-name=NAME
                        Name of the Directory Server SSL certificate to
                        install
    --http-cert-name=NAME
                        Name of the Apache Server SSL certificate to install
    --pkinit-cert-name=NAME
                        Name of the Kerberos KDC SSL certificate to install

  Client options:
    --mkhomedir         create home directories for users on their first login
    -N, --no-ntp        do not configure ntp
    --ssh-trust-dns     configure OpenSSH client to trust DNS SSHFP records
    --no-ssh            do not configure OpenSSH client
    --no-sshd           do not configure OpenSSH server
    --no-dns-sshfp      do not automatically create DNS SSHFP records

  Certificate system options:
    --external-ca       Generate a CSR for the IPA CA certificate to be signed
                        by an external CA
    --external-ca-type={generic,ms-cs}
                        Type of the external CA
    --external-ca-profile=EXTERNAL_CA_PROFILE
                        Specify the certificate profile/template to use at the
                        external CA
    --external-cert-file=FILE
                        File containing the IPA CA certificate and the
                        external CA certificate chain
    --subject-base=SUBJECT_BASE
                        The certificate subject base (default O=<realm-name>).
                        RDNs are in LDAP order (most specific RDN first).
    --ca-subject=CA_SUBJECT
                        The CA certificate subject DN (default CN=Certificate
                        Authority,O=<realm-name>). RDNs are in LDAP order
                        (most specific RDN first).
    --ca-signing-algorithm={SHA1withRSA,SHA256withRSA,SHA512withRSA}
                        Signing algorithm of the IPA CA certificate

  DNS options:
    --allow-zone-overlap
                        Create DNS zone even if it already exists
    --reverse-zone=REVERSE_ZONE
                        The reverse DNS zone to use. This option can be used
                        multiple times
    --no-reverse        Do not create new reverse DNS zone
    --auto-reverse      Create necessary reverse zones
    --zonemgr=ZONEMGR   DNS zone manager e-mail address. Defaults to
                        hostmaster@DOMAIN
    --forwarder=FORWARDERS
                        Add a DNS forwarder. This option can be used multiple
                        times
    --no-forwarders     Do not add any DNS forwarders, use root servers
                        instead
    --auto-forwarders   Use DNS forwarders configured in /etc/resolv.conf
    --forward-policy={first,only}
                        DNS forwarding policy for global forwarders
    --no-dnssec-validation
                        Disable DNSSEC validation

  AD trust options:
    --enable-compat     Enable support for trusted domains for old clients
    --netbios-name=NETBIOS_NAME
                        NetBIOS name of the IPA domain
    --rid-base=RID_BASE
                        Start value for mapping UIDs and GIDs to RIDs
    --secondary-rid-base=SECONDARY_RID_BASE
                        Start value of the secondary range for mapping UIDs
                        and GIDs to RIDs

  Uninstall options:
    --ignore-topology-disconnect
                        do not check whether server uninstall disconnects the
                        topology (domain level 1+)
    --ignore-last-of-role
                        do not check whether server uninstall removes last
                        CA/DNS server or DNSSec master (domain level 1+)

  Logging and output options:
    -v, --verbose       print debugging information
    -d, --debug         alias for --verbose (deprecated)
    -q, --quiet         output only errors
    --log-file=FILE     log to the given file


</details>

2. Таймаут  

2.1 При ручной установке

![timeout](https://i.ibb.co/MPb9TLH/123.png)

+ Решение: Увеличил размер оперативной памяти ВМ до 4гб (Увеличение таймаута, не не слышал :D )  


2.2 При автоматической установке

![horror](https://i.ibb.co/4tSChyv/1234.png)

+ Шок, отрицание, агрессия, торг, депрессия, принятие =>  
||  
\/  

+ Просмотр логов  
+ Решение: обновить модуль nss  


![У-успех](https://i.ibb.co/4tSChyv/1234.png)



