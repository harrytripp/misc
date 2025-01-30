# Aruba CX Network Switch Configuration Guide

## Interface Configuration

### Device Configuration

#### Access Control
```plaintext
vlan access 10
```

#### Access Point
```plaintext
vlan trunk native 100
vlan trunk allowed 20,30,40,50,60,100
```

#### CCTV
```plaintext
vlan access 20
```

#### Phone
```plaintext
vlan trunk native 30
vlan trunk allowed 10,30
```

#### Printer
```plaintext
vlan access 40
```

#### Staff Device
```plaintext
vlan access 50
```

#### Student Device
```plaintext
vlan access 60
```

#### Trunk Port
```plaintext
vlan trunk allowed all
```

## Useful Commands & Procedures

### Aruba CX Syntax & ArubaOS Equivalent

| Aruba CX Syntax | ArubaOS Syntax | Explanation | Device Examples |
|-----------------|---------------|-------------|-----------------|
| `trunk native` | `untagged` | Only carries traffic on the native VLAN. | Access Points, Phones with passthrough |
| `trunk allowed` | `tagged` | Can carry traffic for multiple VLANs. | Access Points, Phones |
| `access` | `untagged` | Can only carry traffic for one VLAN. | Staff, Students, Printers |

### LED Codes
- VLAN: Access, Native & Trunk explained
- Reset admin password
- Hit `TAB` to auto-complete a command
- Double `TAB` for help with a command

### Console Connection
1. Connect USB-C console cable to switch.
2. Install the USB to UART Driver.
3. Ensure the COM port is active in device manager.
4. In PuTTY, under Serial Line, enter the COM port you are using and set speed to `115200`.

### Reset to Factory Defaults
1. Reboot switch.
2. Input `0` on boot to enter SVOS.
3. Login as Admin.
4. Enter:
   ```plaintext
   erase all zeroize
   ```
   or
   ```plaintext
   erase zeroize
   ```
   and confirm.
5. The switch will reboot and erase itself.
6. On boot, login as Admin (no password required).
7. Set switch password when prompted.

### Set IP of Management VLAN
```plaintext
config
interface vlan 100
ip address 192.168.100.1/24
ip route 0.0.0.0/0 192.168.100.254
ip dns server-address 8.8.8.8
ip dns server-address 8.8.4.4
```
Example:
```plaintext
6300(config)# interface vlan 100
6300(config-if-vlan)# ip address 192.168.100.75/24
6300(config-if-vlan)# ip route 0.0.0.0/0 192.168.100.254
6300(config-if-vlan)# ip dns server-address 8.8.8.8
6300(config-if-vlan)# ip dns server-address 8.8.4.4
```

### Aruba Central Enable/Disable
```plaintext
show aruba-central
aruba-central
disable
```

### Set NTP Server
```plaintext
ntp server 192.168.200.11 burst
```

### Set Hostname
```plaintext
config
hostname SITE-SWITCH-LOCATION
```

### Save Changes
```plaintext
wr me
```

### Turn on Blue Locator Light

| Command | Description |
|---------|-------------|
| `led locator flashing` | Continuous flash |
| `led locator on` | Stays on |
| `led locator off` | Light turns off |

### Names and Descriptions
```plaintext
Switch
VLANs
Ports
hostname xxx
name xxx
description xxxxx
```

## Show Configurations
> Must exit configuration mode to use these commands.
> If in configuration mode, prefix commands with `do`, e.g., `do sh int 1/1/1`.

| Command | Description |
|---------|-------------|
| `show system` | Shows general system status |
| `show running-config` | Displays current non-default configuration |
| `show vlan` | Displays configuration info for all VLANs |
| `show vlan xx` | Displays info for specified VLAN |
| `show interface` | Displays info for all ports |
| `show interface 1/1/xxx` | Displays info for specified port |
| `show vlan interface 1/1/xx` | Displays VLANs configured for a port |
