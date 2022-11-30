Task: tạo vlan 10 trên switch, gán ip 172.3.1.98/28. (Nhánh computer là phụ - luyện tập)
![image](https://user-images.githubusercontent.com/93396414/204736786-e83ff41c-7812-4b46-a6fe-fb74c3bf47b9.png)

Configuration in Switch:
  - # conf t
  - # vlan 10
  - # int e0/0
  - # no shut
  - # switchport mode access
  - # switchport access vlan 10
  - # int vlan 10
  - # ip addr 172.3.1.98 255.255.255.240
  - # no shut

Kiểm tra bằng lệnh:
  - # show ip int brief
  - # show vlan status 

Cấu hình trên máy ubuntu server:
  - $ sudo nano /etc/netplan/...
  - Định tuyến tĩnh:
    ![image](https://user-images.githubusercontent.com/93396414/204737495-5ecf35c3-c203-48e6-a294-4616520b781f.png)
  - $ sudo netplan apply
