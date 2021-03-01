# ubuntu-netplan-secondary-static-ip

Below we add secondary static IP address to Ubuntu with netplan. 

Current set up: Ubuntu 20.04 LTS, IP is assigned via DHCP.

Existing network setup at `/etc/netplan/00-installer-config.yaml`:

```
# This is the network config written by 'subiquity'
network:
        #  ethernets: {}
  ethernets:
          enp2s0:
                  dhcp4: true
  version: 2
```
To add another static IP create `/etc/netplan/10-static.yaml` file with content similar to this: 

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      addresses:
        - 192.168.1.3/24
```

Apply the changes: 

`sudo netplan try`
