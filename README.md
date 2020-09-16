Role Name
=========

This role will install Kubernetes onto a cluster of nodes defined within an
Ansible hostgroup.

Requirements
------------

None.

Role Variables
--------------

A full list and description of the available variables in this role can be found
in [defaults/main.yml](defaults/main.yml).

Dependencies
------------

This role assumes that a number of dependencies have already been handled on
your nodes in preparation for an install. This generally includes: Docker
installation, swap space management (ie. disabling your swap),
firewall configuration, etc. There are no explicit dependencies from this role
that try to make those things happen, but your install will fail if you don't
handle them somehow.

Example Playbook
----------------

Since this role is meant to deploy a cluster, some configuration items will
appear as host-only values, such as the declaration of a master or control
plane replica through the `kubernetes_master` or
`kubernetes_control_plane_replica` values. Please see
[defaults/main.yml](defaults/main.yml) for more info.

Eg. In `host_vars/node1.yml` where node1 is the master node for your host group:

    ---
    kubernetes_master: true
    # Remove master taints
    kubernetes_taints: []

In the playbook:

    - hosts: k8s
      roles:
         - role: dudefellah.kubernetes

License
-------

GPLv2 or greater

Author Information
------------------

Dan Thomson - https://github.com/dudefellah
