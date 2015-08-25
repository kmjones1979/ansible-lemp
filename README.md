## Ansible Playbook - Install and configure a LEMP Stack with NGINX Plus, PHP-FPM, Wordpress and Mariadb on CentOS 7.1
This playbook will...
- Install CentOS epel-release
- Install MySQL-python
- Install Mariadb
- Install NGINX Plus
- Install PHP-FPM
- Install Wordpress
- Secure the default MySQL installation
- Create a Wordpress database

## Setup

1. Create a vars.yml with your Ansible deployment variables
```
# ./vars.yml 

# database variables
root_db_password:  "password"
wordpress_db_name: "database"

# wordpress database variables
wordpress_db_user: "username"
wordpress_db_password: "password"
```

2. Edit your Ansible hosts file to target hosts
```
# /etc/ansible/hosts

[lemp]
<hostname or ip address>
```

3. Add your SSH key to the target hosts authorized_keys file
https://help.ubuntu.com/community/SSH/OpenSSH/Keys

## Deployment

```
ansible-playbook deploy.yml
```

## Configuration

Finish setting up your Wordpress installation

http://<yourdomain>/wp-admin/install.php

