dehydrated
==========

Install, configure and integrate dehydrated on Debian hosts.

Supports http-01 and dns-01 challenge via nsupdate.

This role is still a work in progress, use with care.

Role Variables
--------------

TBA

Example Playbook
----------------

```yaml
    - hosts: servers
      roles:
        - role: dehydrated
      vars:
        - dehydrated:
            - contact_email: admin@example.com
              challenge_type: http-01
              certs:
                - cn: server.example.com
                  sAN: www.example.com
                - cn: git.example.com
```

License
-------

GPL-3.0-only
