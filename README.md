# ansible-squid
Install and configure a squid for CVMFS and Conditions DB

Requirements
------------

Tested on an SL7 and SL6 machine.


Role Variables
------------

Variables for iptables:

`ssh_gateway`: This is the ipaddress of the node from which ssh connections are permitted. This can be an ipaddress or a CIDR range.

`iptables_rules`: This is a list of ipaddresses and CIDR ranges that should be allowed access to the squid on port 3128

They are `acl_src` and `acl_srcdom`.  They are both dictionaries that that take a key value pair.  The key is the name assigned to the acl; For `acl_src` the value is the ip address or range permitted as a source, and for `acl_srcdom` the value is the regular expression permitted as a source.

Dependencies
------------

None.


Example Playbook
----------------
---
- hosts: squid
  remote_user: root

  roles:
    - ansible-squid
  vars:
    - acl_srcdom: {LOCAL_CLUSTER: ^(site-prefix.*\.site\.ac\.uk)$}
    - acl_src: {LOCALNET: 10.41.1.0/24, TEST_SERVER: 10.41.25.128}
    - ssh_gateway: 10.41.1.1
    - iptables_rules: [10.41.25.0/22, 148.56.32.128/25, 10.10.10.1]

License
-------

GPL v3

Author Information
------------------

Created by Robin Long (GridPP)