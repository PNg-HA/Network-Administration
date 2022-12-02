## Task 1: tạo vlan 10 trên switch, gán ip 172.3.1.98/28. (Nhánh computer là phụ - luyện tập)
![image](https://user-images.githubusercontent.com/93396414/204736786-e83ff41c-7812-4b46-a6fe-fb74c3bf47b9.png)

Configuration in Switch:

      - conf t
      - vlan 10
      - int e0/0
      - no shut
      - switchport mode access
      - switchport access vlan 10
      - int vlan 10
      - ip addr 172.3.1.98 255.255.255.240
      - no shut
  
  ![image](https://user-images.githubusercontent.com/93396414/204991854-3271b252-0bf3-432d-9322-f299c5bad850.png)

Kiểm tra bằng lệnh:

      - show ip int brief
      - show vlan status 

Configuration in ubuntu server:

      - $ sudo nano /etc/netplan/...
      - Định tuyến tĩnh:
      
   ![image](https://user-images.githubusercontent.com/93396414/204737495-5ecf35c3-c203-48e6-a294-4616520b781f.png)
   
      - $ sudo netplan apply

## Task2: Cấu hình SSH trên switch với user pngha priv 15 (quyền cao nhất - privileged). Setup SSH-client trên ubuntu server.

Configuration in Switch:

      - conf t
      - username pngha privilege 15 secret <pass>
      - ip domain-name example.com
      - crypto key generate rsa
      - line vty 0 <max>
      - transport input ssh
      - login local 
  
  ![image](https://user-images.githubusercontent.com/93396414/204991928-158ff3a2-103b-483c-b126-798865ff510d.png)

Configuration in ubuntu server (normal user recommended):

      - $ ssh-keygen -t rsa
      - $ ssh-copy-id -i ~/.ssh/id_rsa.pub -oKexAlgorithms=+diifie-hellman-group1-sha1' -o 'Ciphers=+aes256-cbc' 'pngha@ip-add'
      - Sửa file /etc/ssh/ssh_config và tạo file ~/.ssh/config có nội dung: 
  
  ![image](https://user-images.githubusercontent.com/93396414/204994211-e89ffac2-88eb-4626-aec5-14a935e25f9e.png)

  Kiểm tra bằng lệnh:
  - ssh pngha@ip-address

  ## Configure LAN to access Internet
  
 
  
  Topology: 
  
   ![image](https://user-images.githubusercontent.com/93396414/205218883-dd6ff4f1-42bb-43f0-b04d-7fc9b3d19282.png)
  
  Configuration of the computer:
  
   ![image](https://user-images.githubusercontent.com/93396414/205218757-3e710cd5-d956-4e0e-949f-25c3911008d8.png)

  Configuration of the router:
  
    - conf t
    - int e0/1
    - ip addr dhcp
    - int e0/0
    - ip addr 192.168.2.1 255.255.255.128
  
  
## Fix: Command rejected: An interface whose trunk encapsulation is "Auto" can not be configured to "trunk" mode

To fix this error, type:
  
    - conf t
    - int e0/0
    - switchport trunk encapsulation dot1q
  
 
