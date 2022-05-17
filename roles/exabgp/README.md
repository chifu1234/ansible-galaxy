Anycast
=========

This role manages the client side(not router) for a anycast service.

Requirements
------------

This role can only be applied for servers running docker. This role normally needs root access (access to docker socket).

Role Variables
--------------

This role setup a exabgp bgp speaker, which also implements a healthcheck. The role heavaly depends on its input variables as shown below:
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

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

Apache

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
