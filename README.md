## Update version zabbix-server using ansible for 5.0

![Badge](https://img.shields.io/badge/ansible-zabbix-red)

## Dependencies
![Badge](https://img.shields.io/badge/ansible-2.9.10-blue)
![Badge](https://img.shields.io/badge/CentOS-7-blue)
![Badge](https://img.shields.io/badge/mysql-5.7-blue)

## Structure
.
├── ansible.cfg
├── hosts
├── playbook.yml
├── README.md
└── roles
    └── zabbix-update
        ├── defaults
        │   └── main.yml
        ├── handlers
        │   └── main.yml
        ├── meta
        │   └── main.yml
        ├── tasks
        │   ├── front_update.yml
        │   ├── main.yml
        │   └── server_update.yml
        └── templates
            ├── zabbix_agentd.conf.44.j2
            ├── zabbix.conf.j2
            ├── zabbix-php.conf.j2
            ├── zabbix_server.conf.44.j2
            └── zabbix_web.conf.j2

7 directories, 15 files

## Edit the inventory file insert your private or public ip

## Playbook example
```
---
- name: Update Zabbix-server
  hosts: all
  vars:
    zbx_mysql: zabbix-web-mysql-4.4.10-1.el7.noarch
    zbx_web: zabbix-web-4.4.10-1.el7.noarch
    zbx_database_password: INSIRA-AQUI-SUA-SENHA-BANCO
    zbx_archive_server: '/etc/zabbix/zabbix_server.conf'
    zbx_archive_agent: '/etc/zabbix/zabbix_agentd.conf'
    zbx_dir: '/usr/share/zabbix'
  become: yes
  roles:
  - zabbix-update
```
``` 
ansible-playbook -i hosts playbook.yml
``` 
## ATTENTION: If the version of zabbix-web, mysql is different from 4.4 and is not using apache modify in vars, the backup of the old zabbix will be stored in the directory /tmp/zabbix-backup

## License
![Badge](https://img.shields.io/badge/license-GPLv3-green)
