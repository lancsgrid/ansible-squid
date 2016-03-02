# ansible-squid
Install and configure a squid for CVMFS and Conditions DB

Requirements
------------

Only tested on an SL 6.7 node.


Role Variables
------------

There are only two variables in this so far.  They are `acl_src` and `acl_srcdom`.  They are both dictionaries that that take a key value pair.  The key is the name assigned to the acl; For `acl_src` the value is the ip address or range permitted as a source, and for `acl_srcdom` the value is the regular expression permitted as a source.

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


License
-------

GPL v3

Author Information
------------------

Created by Robin Long (GridPP)