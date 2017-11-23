Freeswitch-mw
=============

[![Build Status](https://travis-ci.org/mwolff44/freeswitch-mw.png)](https://travis-ci.org/mwolff44/freeswitch-mw)
[![Galaxy](http://img.shields.io/badge/galaxy-mwolff44.freeswitch--mw-blue.svg?style=flat-square)](https://galaxy.ansible.com/list#/roles/2582)


Ansible role for FreeSwitch 1.6

Requirements
------------

- Tested on Ansible 2.0 or higher.

Ansible installation via pip
----------------------------


    sudo apt-get install -y ansible


Role Variables
--------------

The role variables and default values.

### FreeSwitch


    freeswitch_conf_dir: '/etc/freeswitch' # Configuration directory
    freeswitch_symlinks: True # default FS layout in /usr/local/freeswitch by creating symlinks
    freeswitch_install_conf: True # Allow the installation of the configuration files - Could be disabled when updating
    freeswitch_conf_backup_dir: '/etc/freeswitch.orig' # Backup configuration directory
    freeswitch_config_template_dir: ../templates/freeswitch/config # Templates directory used for FreeSwitch configuration
    freeswitch_config_list: # List of templates config files without ending ".j2"
        - autoload_configs/console.conf.xml
        - autoload_configs/logfile.conf.xml
        - autoload_configs/modules.conf.xml
        - autoload_configs/switch.conf.xml
        - autoload_configs/syslog.conf.xml

    freeswitch_install_script: True # Allow the installation of the script files - Could be disabled when updating
    freeswitch_script_dir: '/usr/share/freeswitch/scripts' # Script directory
    freeswitch_script_backup_dir: '/usr/share/freeswitch/scripts.orig' # Backup cscript directory
    freeswitch_script_template_dir: ../templates/freeswitch/scripts # Templates directory used for FreeSwitch script
    freeswitch_script_list: # List of templates script files without ending ".j2"
        - test.lua

    freeswitch_packages: # FreeSwitch packages to be installed
        - freeswitch-meta-all
        - freeswitch-all-dbg
        - gdb

### FreeSwitch config


    freeswitch_log_mapping: <map name="err" value="debug,info,notice,warning,err,crit,alert"/>
    freeswitch_log_max_rotate: <!-- <param name="maximum-rotate" value="32"/> -->
    freeswitch_max_db_handles: 50 # Maximum number of simultaneous DB handles open
    freeswitch_db_handle_timeout: 10 # Maximum number of seconds to wait for a new DB handle before failing
    freeswitch_min_idle_cpu: 25 # Minimum idle CPU before refusing calls
    freeswitch_max_sessions: 1000 # Max number of sessions to allow at any given time
    freeswitch_sessions_per_second: 30 # Most channels to create per second
    freeswitch_global_loglevel: debug # Default Global Log Level - value is one of debug,info,notice,warning,err,crit,alert
    freeswitch_rtp_start_port: 16384
    freeswitch_rtp_end_port: 32768

### ODBC


    odbc_install: false
    odbc_packages_install: false
    odbc_packages:
        - unixodbc-bin
        - unixodbc-dev
    odbc_postgresql_install: false
    odbc_postgresql_packages:
        - odbc-postgresql
    postgresql_packages_install: false
    odbc_template_dir: ../templates/odbc # Templates directory used for ODBC
    odbc_server: 127.0.0.1
    odbc_port: 5432
    odbc_database: 'mydatabase'
    odbc_user: 'myuser'
    odbc_password: 'mypass'
    odbc_tracefile: '/tmp/psqlodbc.log'

### Fail2ban


    fail2ban_install: False # Default : fail2ban will not be installed
    fail2ban_local_jail_file: /etc/fail2ban/jail.local # fail2ban jail file for FreeSwitch
    fail2ban_filter_dir: /etc/fail2ban/filter.d # fail2ban filter directory
    fail2ban_local_jail: ../templates/fail2ban/jail.local # fail2ban template jail for FreeSwitch
    fail2ban_fs: ../templates/fail2ban/freeswitch.conf # Fail2ban filter template for FreeSwitch
    fail2ban_dos_fs: ../templates/fail2ban/freeswitch-dos.conf # Fail2ban filter template for freeswitch dos


### Sngrep


    sngrep_install: False # Default : sngrep will not be installed


### Time sync with systemd


    ntp_install: False # Default : time sync will not be configured
    ntp_servers: '{{ ntp_servers_map[ansible_distribution]
                      | d(ntp_servers_map["default"]) }}'
    ntp_servers_map:
      'Debian':  [ '0.debian.pool.ntp.org', '1.debian.pool.ntp.org',
                   '2.debian.pool.ntp.org', '3.debian.pool.ntp.org' ]
      'Ubuntu':  [ '0.ubuntu.pool.ntp.org', '1.ubuntu.pool.ntp.org',
                   '2.ubuntu.pool.ntp.org', '3.ubuntu.pool.ntp.org' ]
      'default': [ '0.pool.ntp.org', '1.pool.ntp.org',
                   '2.pool.ntp.org', '3.pool.ntp.org' ]
    ntp_timezone: 'Europe/Paris'
    ntp_timesyncd_template : ../templates/etc/systemd/timesyncd.conf.d/ansible.conf.j2


Dependencies
------------

No

Usage
-----

Add `mwolff44.freeswitch-mw` to your roles ans setup the variables in your playbook file. Example :


    - hosts: all
      vars_files:
        - 'defaults/main.yml'
      tasks:
        - include: 'tasks/main.yml'
      handlers:
        - include: 'handlers/main.yml'



License
-------


Licensed under the GPL v3 license. See the LICENSE file for details.


Contributor
--------

A special thank to :
Bruno SALZANO / [d4rkstar@gmail.com](d4rkstar@gmail.com)

Author Information
------------------

Mathias WOLFF / [Blog des télécoms](http://www.blog-des-telecoms.com) - [PyFreeBilling](https://www.pyfreebilling.com)
