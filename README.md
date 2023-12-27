dehydrated
==========

Install, configure and integrate dehydrated on Debian hosts.

It contains explicit support for installing a certificate into Proxmox `pveproxy` and Proxmox Backup Server.

Supports `http-01` and `dns-01` challenge via nsupdate.

Requirements
------------

- Debian

Role Variables
--------------

See example playbook below.

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - haufe_it.dehydrated
  vars:
    - dehydrated:
        - contact_email: admin@example.com
          challenge_type: http-01
          certs:
            - cn: server.example.com
              sAN: www.example.com
            - cn: git.example.com
- hosts: more_servers_via_dns01
  roles:
    - haufe_it.dehydrated
  vars:
    - dehydrated:
        - contact_email: admin@example.org
          challenge_type: dns-01
          tsig_key_name: "{{ key_name_from_vault_variable }}"
          tsig_key_secret: "{{ secret_from_vault_variable }}"
          certs:
            - cn: other.example.org
- hosts: pve
  roles:
   - haufe_it.dehydrated
  vars:
   - dehydrated:
       - contact_email: pveadmin@example.net
         pvenode_cert: pve1.example.net
         certs:
           - cn: pve1.example.net
- hosts: pbs
  roles:
   - haufe_it.dehydrated
  vars:
   - dehydrated:
       - contact_email: pbsadmin@example.net
         pbs_cert: pbs1.example.net
         certs:
           - cn: pbs1.example.net
```

License
-------

GPL-3.0-only

Author Information
------------------

Jakob Haufe <jakob@haufe.it>
