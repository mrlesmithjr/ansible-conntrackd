Role Name
=========

Installs conntrackd http://conntrack-tools.netfilter.org/conntrackd.html

Requirements
------------

Each host must be configured with more than one network interface. A dedicated interface is used for syncing.

Role Variables
--------------

````
config_conntrackd: false  #defines if conntrackd should be configured
conntrackd_ignore_addresses:
  - '{{ ansible_default_ipv4.address }}'
  - '{{ conntrackd_sync_ip }}'
conntrackd_sync_ip: 1.1.1.1  #defines ip address to use for syncing...each host unique...define in host_vars/host
conntrackd_sync_int: eth1  #defines interface to use for syncing...must be a dedicated interface
enable_conntrackd: true  #defines if conntrackd should be enabled

#
# Defaults less likely to be changed
#
multicast_ipv4_address: '225.0.0.50'
multicast_group: '3780'
sndsocketbuffer: '1249280'
rcvsocketbuffer: '1249280'
checksum: 'on'
hashsize: '32768'
hashlimit: '131072'
logfile: 'on'
netlinkbuffersize: '2097152'
netlinkbuffersizemaxgrowth: '8388608'
filterfrom: 'Userspace'
filterfromprotocol: 'Accept'
filterfromprotocols:
  - TCP
  - SCTP
  - DCCP
````

Variables without default values. These only need changes in specific setups:

````
resendqueuesize
committimeout
purgetimeout
ackwindowsize
disableexternalcache
hashsize
hashlimit
logfile
syslog
lockfile
netlinkoverrunresync
netlinkeventsreliable
pollsecs
eventiterationlimit
state_accept
````

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: mrlesmithjr.conntrackd }

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
