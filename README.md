## Ansible Playbook - A simple easy deployment of LEMP with Wordpress using Ansible

This playbook will...
- Install CentOS epel-release
- Install MySQL-python
- Install Mariadb
- Install NGINX or NGINX Plus
- Install PHP-FPM
- Install Wordpress
- Secure the default MySQL installation
- Create a Wordpress database

## Setup

#### Create a vars.yml with your Ansible deployment variables

Specify your environment specific variables. It is reccomended to make complex passwords and not use the examples below.

```
# ./vars.yml 

# ansible variables
ansible_user: "linux_username"

# database variables
root_db_password:  "password"
wordpress_db_name: "database"

# wordpress database variables
wordpress_db_user: "username"
wordpress_db_password: "password"

# nginx repo rpm location (NGINX F/OSS only)
nginx_yum_rpm: "http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm"
```

#### Edit your Ansible hosts file to include target hosts

```
# /etc/ansible/hosts

[lemp]
example[1-4].com
example.com
127.0.0.1
```

### Copy your NGINX Plus key and certificate to /etc/ssl/nginx

These files are provided to users evaluating or who have purchased NGINX Plus.

Visit https://www.nginx.com/#contact-us for more information.

Visit https://www.nginx.com/#free-trial for a free trial of NGINX Plus.

```
[kjones@ansible ~]$ tree /etc/ssl/nginx/
/etc/ssl/nginx/
├── nginx-repo.crt
└── nginx-repo.key

0 directories, 2 files
```

### NGINX Open source deployment

If you want to install NGINX F/OSS instead of Plus you can change the line in deploy.yml from

```
    - include: 'tasks/install_nginx_plus.yml'
```
to...

```
    - include: 'tasks/install_nginx.yml'
```

Also be sure to specify the proper version in your variable file under "nginx_yum_rpm"

#### Add your SSH key to the target hosts authorized_keys file

Visit https://help.ubuntu.com/community/SSH/OpenSSH/Keys for instructions.

## Deployment

```
ansible-playbook deploy.yml
```

## Configuration

Finish setting up your Wordpress installation by visiting the admin page.

http://yourwordpresssite.com/wp-admin/install.php

