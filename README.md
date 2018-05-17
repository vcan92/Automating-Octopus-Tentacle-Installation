Requirements
------------

- Ansible Installation
- User Authentication with Kerberos
- inventory file

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
 vi /etc/krb5.conf

 [realms]
    MY.DOMAIN.COM = {
        kdc = domain-controller1.my.domain.com
        kdc = domain-controller2.my.domain.com
    }
    
 [domain_realm]
    .my.domain.com = MY.DOMAIN.COM
       
kinit username@MY.DOMAIN.COM
```

Create Inventory File
---------------------
```Create Inventory File

vi inventory.yml

[ExampleWindowsServer]
domain-controller1.my.domain.com

[ExampleWindowsServers:vars]
ansible_port: 5985
ansible_connection: winrm
ansible_winrm_scheme: http
ansible_winrm_cert_validation: ignore
ansible_user: Username
ansible_password: Password
```















