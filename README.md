Enix/ucarp for Ansible
==================

A role for deploying and configuring [ucarp](https://www.pureftpd.org/project/ucarp) on unix hosts using [Ansible](http://www.ansible.com/).


Requirements
------------

Supported targets:

- Ubuntu 16.04 "Xenial"
- Debian 8 "Jessie"
- ...


Role Variables
--------------

This roles comes preloaded with almost every available default. You can override each one in your hosts/group vars, in your inventory, or in your play. See the annotated defaults in `defaults/main.yml` for help in configuration. All provided variables start with `ucarp__`.

- `ucarp__interface` - *mandatory*, network interface on which ucarp should bind on; will fail if none defined, `default: none`.
- `ucarp__interface_configfile` - configuration file where ucarp__interface defined, `default: /etc/network/interfaces`.
- `ucarp__vid` - id of the ucarp setup, `default: 10`.
- `ucarp__vip` - *mandatory*, virtual ip address, `default: none`.
- `ucarp__vip_netmask` - virtual ip netmask, `default: 255.255.255.255`.
- `ucarp__password` - *mandatory*, password used to auth ucarp processes, `default: none`.
- `ucarp__advskew` - advskew parameter, `default: 0`.
- `ucarp__advbase` - advbase parameter, `default: 1`.
- `ucarp__master` - make this host master by default (preempt mode), `default: no`

Dependencies
------------

- None

Usage
-----

Clone this repo into your roles directory:

    $ git clone https://gitlab.enix.org/ansible/ansible-ucarp.git roles/ucarp

Or use Ansible galaxy requirements.yml

And add it to your play's roles:

    - hosts: servers
      roles:
        - role: ucarp
          - ucarp__


You can also use the role as a playbook. You will be asked which hosts to provision, and you can further configure the play by using `--extra-vars`.

    $ ansible-playbook -i inventory --extra-vars='{...}' main.yml


Still to do
-----------

- Write the role itself, for one


Changelog
---------

### 0.1

Initial version.

License
-------

BSD/GPL/Other

Author Information
------------------

Laurent Corbes <laurent.corbes@enix.fr> - http://www.enix.fr
