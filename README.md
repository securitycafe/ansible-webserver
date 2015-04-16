# ansible-webserver
Playbook for LAMP (Linux, Apache, MySQL, PHP) server. For now works only on CentOS system. 
It will install latest Apache (2.4.12), PHP (5.6.7) and MySQL Community server (5.7.7)

For more details and installation instructions: http://blog.astaz3l.com/2014/05/19/setup-vps-server/

## Roles
### - epel
EPEL  is repository that provides useful software packages that are not included in the official CentOS repositories. 

### - common
Update everything to latest versions and install required packages for CentOS so it can be provisioned by Ansible.
In addition it will create group, user and directory for compiling purposes. 

### - firewall
Setup firewall based on iptables. 

### - ssh
Configure SSH daemon and improve security.

### - httpd
Apache server in latest version (2.4.12) on CentOS. Apache will be build from source and installed in local system. It contains configuration files, basic hardening, logrotate and /etc/init.d script. 
In addition it comes with ModSecurity module and OWASP rules for better security. 

### - php
PHP in latest version (5.6.7). PHP will be build from source. It contains configuration files, PHP-FPM setup, OPCache setup, basic hardening and /etc/init.d script.

### - mysql
Install MySQL community server in latest version (5.7.7). It will be installed from official MySQL repository. Contains configuration files and basic hardening. 


## Variables
In group_vars/all.yml You will find configuration that is used across all modules. 

**Build user** - username, group and directory. To provided directory ansible will download source files for apache and will compile it there. 

**Website directory** - preferably /var/www directory. All logs, and htdocs will be stored in that directory.

**Websites** - list of websites that will be placed inside website directory. 

**PHP-FPM port** - initial port for FPM pool. Each website has it's own pool.  

**MySQL socket** - just be sure that PHP will use the same socket as MySQL server 

**WWW group** - this is the group for apache and developer. So they can modify the files without permission denied. 