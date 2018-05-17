Requirements
------------

- Ansible Installation
- User Authentication with Kerberos
- inventory file
- Define Variables

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

Defining Variables
------------------
You should define your variables(Octopus Tentacle Instace Name, Port, OctopusThumprint, OctopusApiKey, Octopus Role, OctopusEnvironmentName )

https://github.com/vcan92/Automating-Octopus-Tentacle-Installation/blob/master/server_register_to_octopus_deploy_server/vars/main.yml

```DefineVariable

---
InstanceName: ExampleInstanceName
Port: YourPort(Default 10933)
Thumprint: YourOctopusThumprint
ApiKey: YourOctopusApiKey
Role: YourServerRole
EnvironmentName: YourEnvironmentName
```

```Run Ansible-Palybook

Ansible-Playbook -i inventory.yml configuration_octopus_windows_servers.yml

```














