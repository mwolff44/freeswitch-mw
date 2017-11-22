Changelog
=========

v2.2
-----
- Script install management for freeswitch
- Correct installation bug of freeswitch config files
- Add new freeswitch config vars (for log and switch)
- Add symlinks like default freeswitch configuration
- Test if FS script directory exists, if not, it creates it
- Add scripts directory in freeswitch templates

v2.1
-----
- Upgrade kernel tasks to Debian backport (for performance)
- Install others packages from list
- Locales configuration

v2.0
-----
- Install from packages
- Only for Debian Jessie
- Freewitch version 1.6
- Add Fail2ban optionnal
- Add sngrep install optional
- Ansible > 2

v1.3
----
- Add Jessie compatibility
- Correct typo in default modules.conf file
- Add mod_curl appilcation in default modules.conf file

v1.2
----
- Add Fail2ban : installation and configuration
- Change FreeSwitch log management (standard debian directory and cron rotate)

v1.1
----
- Add variables
- Change cli symlinks task to file command

v1.0
----
First release
