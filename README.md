Role Name
========

Installs logrotate and provides an easy way to setup additional logrotate scripts by specifying a list of directives.

Requirements
------------

None

Role Variables
--------------

**logrotate_scripts**: A list of logrotate scripts and the directives to use for the rotation. 

* name - The name of the script that goes into /etc/logrotate.d/
* path - Path to point logrotate to for the log rotation
* options - List of directives for logrotate, view the logrotate man page for specifics

```
logrotate_scripts:
  - name: rails
    path: "/srv/current/log/*.log"
    options:
      - weekly
      - size 25M
      - missingok
      - compress
      - delaycompress
      - copytruncate
```

Dependencies
------------

None

Example Playbook
-------------------------

Setting up logrotate for additional Nginx logs

```
logrotate_scripts:
  - name: nginx
    path: /var/log/nginx/*.log
    options:
      - weekly
      - size 25M
      - rotate 7
      - missingok
      - compress
      - delaycompress
      - copytruncate
```

License
-------

BSD

Author Information
------------------

Find [Nick Hammond]( http://www.nickhammond.com ) on [Twitter](http://twitter.com/nickhammond).
