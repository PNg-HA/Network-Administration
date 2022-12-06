## VLAN access the Internet using NAT (PAT) and DHCP:
    The time I do this topology is at my university, using wifi UIT.

![image](https://user-images.githubusercontent.com/93396414/205857800-74971928-0a68-4a7f-8b80-d56a42878a91.png)

IP information:

![image](https://user-images.githubusercontent.com/93396414/205860602-97392d74-6b28-4bb7-9148-ade047b2e0cf.png)

#### Configuration of Ubuntu server:

1. Configure static IP:
    
    $ sudo nano /etc/netplans/[`00-installer-config.yml`](00-installer-config.yml)
    
2. Apply the change:

    $ sudo netplan apply
    
If you have a bug here (especially in EVE-ng), don't worry. It is the none-existed floppy. [Here] is how to fix it:
    
    $ sudo rmmod floppy
    $ echo "blacklist floppy" | sudo tee /etc/modprobe.d/blacklist-floppy.conf
    $ sudo dpkg-reconfigure initramfs-tools
 
#### Configuration in switch:

    # conf t
    (config)# vlan 10
    (config)# int e0/0
    (config-if)# no shut
    (config-if)# switchport mode access
    (config-if)# switchport access vlan 10
    (config-if)# int vlan 10
    (config-if)# ip addr 172.3.1.98 255.255.255.240
    (config-if)# no shut
    (config-if)# int e0/1
    (config-if)# no shut
    (config-if)# switchport mode trunk
    ! Ctr + C
    # copy run start
    
#### Configuration in router:

    # conf t
    (config)# int e0/0
    (config-if)# no shut
    (config)# int e0/0.10
    (config-subif)# encap dot1Q 10
    (config-subif)# ip addr 172.3.1.97 255.255.255.240
    (config-subif)# ip nat inside
    (config-subif)# no shut
    (config-subif)# int e0/1
    (config-if)# no shut
    (config-if)# ip addr dhcp
    (config-if)# ip nat outside
    (config-if)# exit
    (config)# access-list 10 permit 172.3.1.96 255.255.255.240
    ! 
    (config)# access-list 10 permit ip-subnet-mask-in-e0/1
    (config)# ip nat inside source list 10 int e0/1 overload
    # copy run start
    
[Here]: https://askubuntu.com/questions/719058/blk-update-request-i-o-error-dev-fd0-sector-0

