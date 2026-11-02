# WLC-2504 and Wireless Setup

## Baseline parameters

| Item | Value |
|------|-------|
| Management IP | 192.168.9.100 |
| Netmask | 255.255.255.128 |
| Gateway | 192.168.9.25 |
| Management VLAN | 0 (untagged native) |
| Admin user | admin (password `<WLC_ADMIN_PASSWORD>`) |

## Provisioning steps

1. **Initial wizard.** From PC0, browse to http://192.168.9.100. Set the system name (WLC-CAMPUS), admin credentials, management IP (192.168.9.100, mask 255.255.255.128, gateway 192.168.9.25, VLAN 0), and create the initial SSID CAMPUS-WIFI with WPA2-PSK (`<WLAN_PSK>`) and virtual IP 1.1.1.1. Apply and let the WLC reboot (fast-forward the simulation time).
2. **Dynamic interface.** Reconnect via https://192.168.9.100. Go to CONTROLLER > Interfaces > New. Name `IT-VLAN30`, VLAN ID 30, port 1, IP 192.168.3.100, netmask 255.255.255.128, gateway 192.168.3.25, primary DHCP server 192.168.3.50 (CORE-SW1 SVI). Apply.
3. **Bind the WLAN.** Go to WLANs > WLAN ID 1 (CAMPUS-WIFI). Enable it, radio policy All, interface IT-VLAN30, broadcast SSID. Under Security > Layer 2 use WPA+WPA2, WPA2-PSK, AES. Apply and Save Configuration.
4. **Lightweight AP join.** Power cycle AP0 and AP1. They receive DHCP leases in VLAN 100 and discover the WLC through option 150 (192.168.9.100), forming CAPWAP tunnels.

## Wireless clients (Laptop0 - Laptop3)

1. Physical tab: power off, replace the Ethernet module with the WPC300N wireless NIC, power on.
2. Config tab > Wireless0: port status ON, SSID CAMPUS-WIFI, WPA2-PSK, AES, passphrase `<WLAN_PSK>`.
3. Desktop > IP Configuration: DHCP (receives 192.168.3.x /25, gateway 192.168.3.25).
4. Verify:
```
C:\> ipconfig
C:\> ping 192.168.3.25
C:\> ping 200.1.5.11
```
