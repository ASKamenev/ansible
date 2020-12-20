This document contain an information about playbook wich install and run Zabbix-server + Zabbix-proxy + Zabbix-gui with postgreSQL.

--------Table of Contents-------
1. Directory tree
2. Files explanations
3. Some notes

1. Directory tree:
.
├── README.txt
├── ansible.cfg
├── config
│   ├── zabbix.conf
│   ├── zabbix.conf.php
│   ├── zabbix_proxy.conf
│   └── zabbix_server.conf
├── hosts.txt
└── zabbix-playbook.yml

2. Files explanations
README.txt - you're already reading this file
ansible.cfg - some ansible variables. In this case there'are only two variables: host_key_checking and inventory
hosts.txt - just a file with hosts and one variable swithing python interpeter to python2 (need to postgres built in functions)
zabbix-playbook.yml - main playbook shining in the sun :)
--config directory:
     zabbix.conf - this is a apache2 vhost file which will be placed in /etc/apache2/sites-available
     zabbix.conf.php - zabbix configuration file for gui. Contain ready DB connetion variables
     zabbix_proxy.conf - zabbix proxy configuration file with all nescessary configs (will be placed after zabbix installing)
     zabbix_server.conf - zabbix server configuration file with all nescessary configs (will be placed after zabbix installing)

3. Some notes
This playbook install ready to work zabbix server. After end of running, type an ip address dash zabbix and you will see an admin page to zabbix. 
PostgreSQL have a two databases: one (zabbix) for zabbix server and gui running and second (zabbix_proxy), for zabbix proxy running.
The Python2 interpeter need to run a postgresql_ builtin functions which require psycopg2 (install with pip). Unfortunelly, with python3 got an error "can't find module psycopg2" So, in the beggining we install pip and psycopg2.

This Playbook will be work in Debian-like systems.
