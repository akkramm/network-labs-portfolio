# Server Configuration (Packet Tracer)

## Server0: TACACS+ AAA and central DNS

**Desktop > IP Configuration**
- Interface: FastEthernet0
- IP address: 200.1.5.11
- Subnet mask: 255.255.255.0
- Default gateway: 200.1.5.10 (HSRP virtual IP)
- DNS server: 127.0.0.1

**Services > AAA** (service ON)

| Client name | Client IP | Type | Secret |
|-------------|-----------|------|--------|
| CORE-SW1 | 192.168.9.50 | TACACS+ | `<TACACS_SHARED_KEY>` |
| CORE-SW1-WAN | 172.168.1.2 | TACACS+ | `<TACACS_SHARED_KEY>` |
| CORE-SW2 | 192.168.9.51 | TACACS+ | `<TACACS_SHARED_KEY>` |

User setup: username `netadmin`, password `<ADMIN_PASSWORD>`.

**Services > DNS** (service ON)
- Resource record: `enterprise.local` -> 200.1.5.12 (Server1)

## Server1: Web / application server

- IP address: 200.1.5.12
- Subnet mask: 255.255.255.0
- Default gateway: 200.1.5.10 (HSRP virtual IP)
