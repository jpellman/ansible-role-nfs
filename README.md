# Ansible Role: NFS

Installs NFS utilities on RedHat/CentOS or Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    nfs_exports:
      - export: /srv/nfs
	hosts: 
          - 192.168.0.0/16
        
A list of export dicts which will be placed in the `/etc/exports` file. Dicts include an `export` key and then a `hosts` key.  See Ubuntu's simple [Network File System (NFS)](https://ubuntu.com/server/docs/service-nfs) guide for more info and examples. (Simple example: `nfs_exports: [ "/home/public    *(rw,sync,no_root_squash)" ]`).

    nfs_rpcbind_state: started
    nfs_rpcbind_enabled: true

(RedHat/CentOS/Fedora only) The state of the `rpcbind` service, and whether it should be enabled at system boot.

## Dependencies

None.

## Example Playbook

    - hosts: db-servers
      roles:
        - { role: geerlingguy.nfs }

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).  Minor tweaks made by John Pellman to suit his tastes.
