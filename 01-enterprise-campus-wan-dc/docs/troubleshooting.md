# Troubleshooting Notes

**1. Destination host unreachable at Router1 during HSRP failover**
If shutting the SVIs on CORE-SW1 causes traffic drops, check that OSPF Area 1 is active on CORE-SW2 with the network statement `172.168.2.0 0.0.0.3`, and that transit VLAN 99 (10.99.99.0/30) is allowed across Port-Channel 6. Router1 should show ECMP routes for the campus subnets.

**2. APs not discovering the WLC (controller IP 0.0.0.0)**
Check that the SW2 access ports Fa0/1 - 2 are in VLAN 100 and that CORE-SW2 Fa0/6 has `switchport trunk native vlan 100`. Confirm the DHCP scope MGMT-VLAN-100 includes `option 150 ip 192.168.9.100`.

**3. SSH login closed by foreign host**
Check that Server0 has both client IPs registered (192.168.9.50 and 172.168.1.2) with the shared key and type TACACS+. Make sure `ip tacacs source-interface Vlan100` is applied on the switch.

**Backup**
Run `copy running-config startup-config` on every device. On the WLC, use Save Configuration in the web GUI.
