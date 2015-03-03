# ansible-webserver
The aim of this project is to setup LAMP server for PHP based applications. 

## Variables
In group_vars/all.yml You will find configuration that is used across all modules. 

**Build user** - username, group and directory. To provided directory ansible will download source files for apache and will compile it there. 

**Website directory** - preferably /var/www directory. All logs, and htdocs will be stored in that directory.

**Websites** - list of websites that will be placed inside website directory. 

**PHP-FPM port** - initial port for FPM pool. Each website has it's own pool.  

## Roles
### - epel
EPEL  is repository that provides useful software packages that are not included in the official CentOS repositories. 

### - common
Update everything to latest versions and install required packages for CentOS so it can be provisioned by Ansible.
In addition it will create group, user and directory for compiling purposes. 

### - httpd
Apache server in latest version (2.4.12) on CentOS. Apache will be build from source and installed in local system. It contains configuration files, basic hardening, logrotate and /etc/init.d script. 
In addition it comes with ModSecurity module and OWASP rules for better security. 


### - php
PHP in latest version (5.6.6). PHP will be build from source. It contains configuration files, PHP-FPM setup, OPCache setup, basic hardening and /etc/init.d script.