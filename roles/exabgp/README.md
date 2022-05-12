Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

```yaml
# defaults file for exabgp
# exabgp: define the exabgp config
exabgp:
  # vip defines the VIP and health-check configuration
  vip:
    - 
      # the file name of the health-check
      healthcheck: http.run
      # args for the health-check
      args: 1.1.1.1 www.google.ch
  # neighbor definition to router
  neighbor:
    # id of peer
  - id: 127.0.0.1
    # router-id 
    routerId: 127.0.0.1
    # local adress to listen on
    localAddress: 172.0.0.1
    # local as number
    localAs: 1
    # peer as number
    peerAs: 1
    # enable group updates
    groupUpdates: false
    # enable bgp caps
    capability:
      graceful-restart: true


# exabgp config path on host system
exabgp_path: /etc/exabgp/

# systemd path for service files
systemd_path: /etc/systemd/system/
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
