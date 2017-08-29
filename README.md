# Ansible Role : lxd-remote

Creation of the remote connection between your local lxd and a remote lxd

First stage to enable the creation of containers

## Requirements

- A working installation of LXD local and distant
- A network connection between LXDs with _lxd-port_ connection available from local to remote
- A ssh connection from local to remote

## Inventory

- need a _Container ship(s)_ group, which will be the hosts of the role
- each host in this group need to be detailled as such:
  - _alias-or-hostname_ [ ansible_host=_ipaddress-or-else_ ]

## Role Variables

Available variable are:

- lxc_url : default is to create it from *ansible_default_ipv4.address*
- lxc_password : Mandatory - May be either in inventory or in host_vars
- lxc_port : default to 8443

## Example playbook

### Inventory

```
[containerships]
clementine ansible_host=2.16.3.168
gudrun     ansible_host=cs.maersk.com
```

### Playbook

```
- hosts: containerships
  roles:
    - jadjay.lxd-remote
```

### Variables

*File: group_vars/containerships.yml*
```
lxd_password: "AyMariekeMariekeZonderliefdewarmeliefde"

```
**Attention** : Ici le mot de passe est commun aux deux porte-conteneurs

Autre possibilité : le définir dans l'inventory.

**Inventory**

```
[containerships]
clementine ansible_host=2.16.3.168 lxd_password="WaaitdewinddestommewindWeentdezeedegrijzezee"
gudrun     ansible_host=cs.maersk.com lxd_password="AyMariekeMariekeZonderliefdewarmeliefde"
```

# License

GNU/GPLv3

# Author Information

This role was created in 2017 by Jerome Avond.



-
