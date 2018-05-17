Requirements
------------

- Ansible Installation
- User Authentication with Kerberos
- inventory file
- Define extra variables

Install Ansible On Ubuntu
-------------------------

```Install Ansible
  sudo apt-get update
 sudo apt-get install software-properties-common
 sudo apt-add-repository ppa:ansible/ansible
 sudo apt-get update
 sudo apt-get install ansible
```

Install Kerberos Authentitacion on Ubuntu
-----------------------------------------

```Install Kerberos
*pip install pywinrm[kerberos]
```

Configuring Host Kerberos
-------------------------

```Configuring Kerberos
-vi /etc/krb5.conf

-[realms]
    MY.DOMAIN.COM = {
        kdc = domain-controller1.my.domain.com
        kdc = domain-controller2.my.domain.com
    }
    
-[domain_realm]
    .my.domain.com = MY.DOMAIN.COM
    
-kinit username@MY.DOMAIN.COM
```










