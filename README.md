# ffrn-gw

This role installs and configures a gateway server for the freifunk community
"Freifunk Rhein-Neckar". It is historicaly grown, sorry for the code quality. The README may not reflect the real code.

## Role Variables
The variables that can be passed to this role and a brief description about
them are as follows.

The Variables of the role are separated by the variables specifing a specific host
and the variables that all gateway servers have in common.

#### Host Variables
```
gw_id: '9'                                  # The gateway ID used to generate IP Addresses and a lot more
dhcp_range: "10.142.24.1 10.142.25.254"
fastd_priv_key: "the random fastd secret"
ipv6_br_addr_list:                          # The different IPv6 Addresses for this host
  - '2a01:4f8:171:fcff::9'                  # The host itself
  - '2a01:4f8:171:fcff:9::53'               # The DNS Server IP of this host
gw_mac: "52:54:00:9e:60:44"                 # Change the fourth block for each gateway
bat_mac: "d2:2f:9c:dd:6d:99"                # Change the last block for eacht gateway
fastd_peer_limit: "120"                     # limit the max. connections fast accepts
```

#### Group Variables
```
is_gateway: true
is_dhcp_server: true

v4_subnet_prefix: '10.142'                  # must be changed if subnet < /16
bind_allow_recursion_subnets:
  - '127.0.0.1'
  - '10.142.0.0/16'                         # our ipv4 network
  - '172.23.138.0/23'                       # old dn42
  - '2a01:4f8:171:fc00::/56'                # our ipv6 network
v6_subnet_prefix: '2a01:4f8:171:fcff'
v4_dns_prefix: '.53.'
v4_main_prefix: '.0.'
admin_contact: 'admin@example.com'
v4_mapbone_prefix: "10.142.11."
```
