## Task 1: tạo vlan 10 trên switch, gán ip 172.3.1.98/28. (Nhánh computer là phụ - luyện tập)
![image](https://user-images.githubusercontent.com/93396414/204736786-e83ff41c-7812-4b46-a6fe-fb74c3bf47b9.png)

Configuration in Switch:

     # conf t
     (config)# vlan 10
     (config)# int e0/0
     (config-if)# no shut
     (config-if)# switchport mode access
     (config-if)# switchport access vlan 10
     (config-if)# int vlan 10
     (config-if)# ip addr 172.3.1.98 255.255.255.240
     (config-if)# no shut
  
  ![image](https://user-images.githubusercontent.com/93396414/204991854-3271b252-0bf3-432d-9322-f299c5bad850.png)

Kiểm tra bằng lệnh:

     # show ip int brief
     # show vlan status 

Configuration in ubuntu server:

     $ sudo nano /etc/netplan/...
     - Định tuyến tĩnh:
      
   ![image](https://user-images.githubusercontent.com/93396414/204737495-5ecf35c3-c203-48e6-a294-4616520b781f.png)
   
     $ sudo netplan apply

## Task2: Cấu hình SSH trên switch với user pngha priv 15 (quyền cao nhất - privileged). Setup SSH-client trên ubuntu server.

Configuration in Switch:

     # conf t
     (config)# username pngha privilege 15 secret <pass>
     (config)# ip domain-name example.com
     (config)# crypto key generate rsa
     (config)# line vty 0 <max>
     (config-line)# transport input ssh
     (config-line)# login local 
  
  ![image](https://user-images.githubusercontent.com/93396414/204991928-158ff3a2-103b-483c-b126-798865ff510d.png)

Configuration in ubuntu server (normal user recommended):

     $ ssh-keygen -t rsa
     $ ssh-copy-id -i ~/.ssh/id_rsa.pub -oKexAlgorithms=+diifie-hellman-group1-sha1' -o 'Ciphers=+aes256-cbc' 'pngha@ip-add'
     - Sửa file /etc/ssh/ssh_config và tạo file ~/.ssh/config có nội dung: 
  
  ![image](https://user-images.githubusercontent.com/93396414/204994211-e89ffac2-88eb-4626-aec5-14a935e25f9e.png)

  Kiểm tra bằng lệnh:
  
     $ ssh pngha@ip-address

  ## Configure LAN to access Internet
  
 
  
  Topology: 
  
   ![image](https://user-images.githubusercontent.com/93396414/205218883-dd6ff4f1-42bb-43f0-b04d-7fc9b3d19282.png)
  
  Configuration of the Windows computer:
  
   ![image](https://user-images.githubusercontent.com/93396414/205218757-3e710cd5-d956-4e0e-949f-25c3911008d8.png)

  Configuration of the router:
  
    # conf t
    (config)# int e0/1
    (config-if)# ip addr dhcp
    (config-if)# int e0/0
    (config-if)# ip addr 192.168.2.1 255.255.255.128
    
  ![image](https://user-images.githubusercontent.com/93396414/205431503-01a99fd3-b982-46ac-8249-d4f0ee7293bc.png)

## Linux server access Internet:

![image](https://user-images.githubusercontent.com/93396414/205432002-29c8e637-3d2a-4acf-94c7-30ff1a5547c9.png)

  Configuration of the Linux server:
  
  $ sudo nano /etc/netplans/00...
  - Nội dung:
  
  ![image](https://user-images.githubusercontent.com/93396414/205431941-b6067942-5e38-4e27-b14a-e5dbf1bf1747.png)
  
  $sudo netplans apply

## Fix: Command rejected: An interface whose trunk encapsulation is "Auto" can not be configured to "trunk" mode

To fix this error, type:
  
    # conf t
    (config)# int e0/0
    (config)# switchport trunk encapsulation dot1q
 



 
