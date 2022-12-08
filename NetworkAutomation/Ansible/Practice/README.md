To ensure Ansible can execute actions on other nodes, make sure that the Ansible server can SSH them. Each IOS version of Cisco devices has different way to set up SSH.
- My switch's IOS version: 15.1
- My router's IOS version: 15.2

Scenario:

![image](https://user-images.githubusercontent.com/93396414/206422327-590f5bcc-3436-41ce-b102-c3a30da1e71f.png)

> Watch [here] for more information.

Configuration SSH on switch and router: 
    conf t
    hostname sw3
    ip domain-name example.com
    crypto key generate rsa 
    ! module: 1024
    
    username pngha priv 15 secret type-password
    line vty 0 4 
    ! Since EVE-ng switch set up 4 interface, Ethernet0/0 -> 4
    login local
    transport input ssh
    ip ssh veriosn 2

[here]: https://github.com/PNg-HA/Network-Administration/tree/main/VLAN_access_Internet
