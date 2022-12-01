## Task1: tạo vlan 10 trên switch, gán ip 172.3.1.98/28. (Nhánh computer là phụ - luyện tập)
![image](https://user-images.githubusercontent.com/93396414/204736786-e83ff41c-7812-4b46-a6fe-fb74c3bf47b9.png)

Configuration in Switch:
  - ##### conf t
  - ##### vlan 10
  - ##### int e0/0
  - ##### no shut
  - ##### switchport mode access
  - ##### switchport access vlan 10
  - ##### int vlan 10
  - ##### ip addr 172.3.1.98 255.255.255.240
  - ##### no shut
  
  ![image](https://user-images.githubusercontent.com/93396414/204991854-3271b252-0bf3-432d-9322-f299c5bad850.png)

Kiểm tra bằng lệnh:
  - ##### show ip int brief
  - ##### show vlan status 

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
  - crypto generate key rsa
  - line vty 0 <max>
  - transport input ssh
  - login local 
  
  ![image](https://user-images.githubusercontent.com/93396414/204991928-158ff3a2-103b-483c-b126-798865ff510d.png)

Configuration in ubuntu server (normal user recommended):
  - $ ssh-keygen -t rsa
  - $ ssh-copy-id -oKexAlgorithms=+diifie-hellman-group1-sha1' -o 'Ciphers=+aes256-cbc' 'pngha@172.3.1.98'
  - Sửa file /etc/ssh/ssh_config và tạo file ~/.ssh/config có nội dung: 
  
  ![image](https://user-images.githubusercontent.com/93396414/204994211-e89ffac2-88eb-4626-aec5-14a935e25f9e.png)

  Kiểm tra bằng lệnh:
  - ssh pngha@<ip>

  
## Task3: Network automation with Ansible.
  Referenced: https://www.youtube.com/watch?v=wbVZkb8ocH4&ab_channel=KevinWallaceTraining%2CLLC
  - Tạo file hosts trong /etc/ansible với nội dung:
     sw3 ansible_host=172.3.1.98
  - Tạo file make1.yml:
  
  ![image](https://user-images.githubusercontent.com/93396414/205001773-d5fc0758-2276-4754-bc07-df96749b78b4.png)
  - $anislbe-playbook make1.yml

  
  
