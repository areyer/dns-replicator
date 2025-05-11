# Update one or more target DNS zones to have the same entries as a source zone
Get the source zone by AXFR, get the target zone by AXFR, compare it and adjust the target zone to have the same content.

## Requirements
- nsupdate utility, e.g. `apt install bind9-dnsutils`
- dnspython, e.g. `apt install python3-dnspython`

`tsig_key_secret_file` file format is as used by bind9

## Sample config
deploy as `/etc/dns-replicator/config.yml`
```
# dns_server: default use first from system configuration
source_domain: "gw.freifunk-stuttgart.de"
source_domain_dns_server: "dns2.lihas.de"
tsig_key_name: "gw.freifunk-stuttgart.de"
tsig_key_secret_file: "/etc/dns-replicator/gw.freifunk-stuttgart.de.secret"

target_domains:
  - domain: "gw.freifunk-stuttgart.net"
    tsig_key_name: "gw.freifunk-stuttgart.de"
    tsig_key_secret_file: "/etc/dns-replicator/gw.freifunk-stuttgart.de.secret"
#  - domain: "gw.stuttgart.freifunk.net"
#    dns_server: "" # might be set manually as well
#    tsig_key_name: "target-key-name-2"
#    tsig_key_secret_file: "/etc/dns-replicator/target2.secret"
```
