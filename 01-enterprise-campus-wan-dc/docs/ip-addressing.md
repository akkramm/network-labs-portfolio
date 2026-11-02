# Interface and Subnet Inventory

| Device | Interface / Port | IP address | Mask | Gateway / VIP | Purpose |
|--------|------------------|------------|------|---------------|---------|
| CORE-SW1 | Vlan10 / 20 / 30 / 100 | 192.168.{1,2,3,9}.50 | 255.255.255.128 | 192.168.{1,2,3,9}.25 (HSRP Active) | Campus SVI gateway (priority 250) |
| CORE-SW1 | Vlan99 / Fa0/5 | 10.99.99.1 / 172.168.1.2 | 255.255.255.252 | Point-to-point | Inter-core transit / uplink to Router1 |
| CORE-SW2 | Vlan10 / 20 / 30 / 100 | 192.168.{1,2,3,9}.51 | 255.255.255.128 | 192.168.{1,2,3,9}.25 (HSRP Standby) | Campus SVI gateway (priority 100) |
| CORE-SW2 | Vlan99 / Fa0/5 / Fa0/6 | 10.99.99.2 / 172.168.2.2 | 255.255.255.252 | Point-to-point / native VLAN 100 | Inter-core transit / uplink to Router1 / WLC trunk |
| SW1 / SW2 | Vlan100 (management) | 192.168.9.2 / 192.168.9.3 | 255.255.255.128 | 192.168.9.25 | Access switch management |
| Router1 | Gi0/0/0, Gi0/0/1, Se0/1/0 | 172.168.1.1, 172.168.2.1, 10.1.1.1 | 255.255.255.252 | OSPF Area 1 | Campus WAN gateway (DCE, 2 Mbps) |
| Router2 | Se0/1/0, Gi0/0/0, Gi0/0/1 | 10.1.1.2, 11.1.1.1, 12.1.1.1 | 255.255.255.252 | OSPF Area 1 / 0 | ABR, backbone headend |
| Router3 | Gi0/0/0, Gi0/0/1 | 11.1.1.2, 13.1.1.1 | 255.255.255.252 | OSPF Area 0 | Backbone path A |
| Router4 | Gi0/0/0, Gi0/0/1 | 12.1.1.2, 14.1.1.1 | 255.255.255.252 | OSPF Area 0 | Backbone path B |
| Router5 | Gi0/0/0, Gi0/0/1, Se0/1/0 | 13.1.1.2, 14.1.1.2, 15.1.1.1 | 255.255.255.252 | OSPF Area 0 / 2 | ABR, backbone tailend (DCE, 2 Mbps) |
| Router6 | Se0/1/0, Gi0/0/0, Gi0/0/1 | 15.1.1.2, 200.1.1.1, 200.1.2.1 | 255.255.255.252 | OSPF Area 2 / EIGRP | ASBR, mutual redistribution |
| DC-SW2 | Fa0/5, Vlan50 | 200.1.1.2, 200.1.5.2 | /30, 255.255.255.0 | 200.1.5.10 (HSRP Active, priority 110) | Data center L3 core 1 (EIGRP 100) |
| DC-SW3 | Fa0/5, Vlan50 | 200.1.2.2, 200.1.5.3 | /30, 255.255.255.0 | 200.1.5.10 (HSRP Standby, priority 100) | Data center L3 core 2 (EIGRP 100) |
| WLC-2504 | Port 1 (management / dynamic) | 192.168.9.100, 192.168.3.100 | 255.255.255.128 | 192.168.9.25, 192.168.3.25 | Wireless LAN controller |
| Server0 | FastEthernet0 | 200.1.5.11 | 255.255.255.0 | 200.1.5.10 | TACACS+ AAA and DNS |
| Server1 | FastEthernet0 | 200.1.5.12 | 255.255.255.0 | 200.1.5.10 | Web / application server |
| PC0 / PC1 | FastEthernet0 | 192.168.1.11 - .12 (DHCP) | 255.255.255.128 | 192.168.1.25 | HR workstations |
| Laptop0 - Laptop3 | Wireless0 | 192.168.3.11 - .14 (DHCP) | 255.255.255.128 | 192.168.3.25 | IT department Wi-Fi clients |
