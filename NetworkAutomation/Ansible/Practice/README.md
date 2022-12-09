# Scenario and setup based network

To ensure Ansible can execute actions on other nodes, make sure that the Ansible server can SSH them. Each IOS version of Cisco devices has different way to set up SSH.
- My switch's IOS version: 15.1
- My router's IOS version: 15.2



![image](https://user-images.githubusercontent.com/93396414/206422327-590f5bcc-3436-41ce-b102-c3a30da1e71f.png)

> Watch [here] for more information.

Configuration SSH on switch and router: 

    conf t
    hostname sw3
    ip domain-name example.com
    crypto key generate rsa 
    ! module: 1024
    
    username pngha priv 15 secret type-password
    ! privilege 15 let user access EXEC mode
    line vty 0 4 
    ! Since EVE-ng switch set up 4 interface, Ethernet0/0 -> 4
    login local
    transport input ssh
    ip ssh veriosn 2

Configuration in ubuntu server for SSH in switch:

     $ ssh-keygen -t rsa
     ! The terminal will prompt the location of the key and the passphrase. Press Enter for all of them if you want the location is at ~/.ssh/id_rsa and no passphrase.
     $ ssh-copy-id -i ~/.ssh/id_rsa.pub -oKexAlgorithms=+diifie-hellman-group1-sha1' -o 'Ciphers=+aes256-cbc' 'pngha@172.3.1.98'
     
Edit file /etc/ssh/ssh_config and create file ~/.ssh/config. The OS sometimes prefers the former. 
    
    Host 172.3.1.98
        KexAlgoirthms diffie-hellman-group-sha1
        User pngha
        Port 22
        Ciphers aes256-cbc
 
 Now you can 
    
    $ ssh pngha@172.3.1.98

Configuration for router is much easier. In terminal, just type:

    $ssh pngha@172.3.1.97
    
Follow the OS recommendation. Type yes for footprint.


[here]: https://github.com/PNg-HA/Network-Administration/tree/main/VLAN_access_Internet
