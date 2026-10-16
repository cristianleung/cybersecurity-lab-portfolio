# Layer 2 mitigation reference

The example assumes a clean Cisco IOS switch, VLAN 1, a verified router/DHCP-server uplink on FastEthernet0/1, and an untrusted client access port on FastEthernet0/2. Confirm the actual cabling, VLAN, and platform support first. The five-address port-security limit and DHCP limit of 15 packets per second are example lab settings.

DHCP snooping and dynamic ARP inspection are explicitly enabled for VLAN 1. Trust is assigned only to the verified infrastructure port. Port-security shutdown uses the complete IOS command, and the client port has a DHCP packet-rate limit. Static clients require the platform's ARP ACL or supported binding configuration before ARP inspection can validate them.

Renew the client lease and confirm `show ip dhcp snooping binding` contains a valid entry. Use `show ip arp inspection vlan 1`, `show port-security interface FastEthernet0/2`, interface status, and logs to inspect behavior. On a router serving DHCP, use `show ip dhcp binding` to inspect leases. These examples were reviewed for command structure; switch behavior was not rerun during portfolio editing.
