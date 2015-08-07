Freeswitch-mw
=============

[![Build Status](https://travis-ci.org/mwolff44/freeswitch-mw.png)](https://travis-ci.org/mwolff44/freeswitch-mw)
[![Galaxy](http://img.shields.io/badge/galaxy-mwolff44.freeswitch--mw-blue.svg?style=flat-square)](https://galaxy.ansible.com/list#/roles/2582)


Ansible role for FreeSwitch

Requirements
------------

- Tested on Ansible 1.8 or higher.

Role Variables
--------------

The role variables and default values.

::

	freeswitch_version: v1.4 #FreeSwitch version. Becareful, only tested with 1.4 version for the time being
	freeswitch_sources_path: /usr/src/freeswitch/ #Path to the FreeSwitch source directory
	freeswitch_path: /usr/local/freeswitch/ #Path to the FreeSwith directory
	freeswitch_owner: freeswitch
	freeswitch_group: daemon
	freeswitch_modules_template: ../templates/modules.conf #modules.conf file used for FreeSwitch compilation
	freeswitch_init_template: ../templates/freeswitch.init #init script template
	freeswitch_configure_command: configure # freeswicth configure command - you can add option
	freeswicth_log_rotate_script: ../templates/freeswitch_log_rotation # log management script
    freeswitch_log_conf_template: ../template/logfile.conf.xml # freeswitch log configuration file template
    fail2ban_local_jail_file: /etc/fail2ban/jail.local # fail2ban jail file for FreeSwitch
    fail2ban_filter_dir: /etc/fail2ban/filter.d # fail2ban filter directory
    fail2ban_local_jail: ../templates/jail.local # fail2ban template jail for FreeSwitch
    fail2ban_fs: ../templates/freeswitch.conf # Fail2ban filter template for FreeSwitch
    fail2ban_dos_fs: ../templates/freeswitch-dos.conf # Fail2ban filter template for freeswitch dos


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

Author Information
------------------

Mathias WOLFF [Blog des télécoms](http://www.blog-des-telecoms.com) - [PyFreeBilling](https://www.pyfreebilling.com)
