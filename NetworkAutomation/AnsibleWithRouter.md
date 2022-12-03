## Summary:

![image](https://user-images.githubusercontent.com/93396414/205435274-72e1eea0-4bea-4c12-b0c0-08c675f311ba.png)

Referenced: https://www.youtube.com/watch?v=wbVZkb8ocH4&ab_channel=KevinWallaceTraining%2CLLC

#### Delete old router's footprint in Ubuntu server:

   > **Note**  
   > I run ansible with user pngha. I delete footprint in /home/pngha

    $ cd ~/.ssh
    $ nano know_hosts
    Delete router's footprint (look at the IP's router). 

#### Ubuntu server SSH to router:

    $ ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -oCiphers=+aes256-cbc pngha@172.3.1.97
    $ sudo nano /etc/hosts (does not matter)
    
    ![image](https://user-images.githubusercontent.com/93396414/205434170-307a434d-7ead-4a68-871f-d3c0ab95773b.png)

#### Configuration in Ubuntu server:

    $ cd /etc/ansible
    $ ls
  
  ![image](https://user-images.githubusercontent.com/93396414/205433321-c0c8030b-1837-414a-b885-a30671f37bd6.png)

    $ sudo nano hosts
  
  ![image](https://user-images.githubusercontent.com/93396414/205433350-35dd63f4-4e35-485c-b103-84aef833d71e.png)

  File ansible.cfg is not edited.
  
    $ sudo nano ipv6.yml
  
  ![image](https://user-images.githubusercontent.com/93396414/205433393-9f2c85de-7bbd-4986-a184-dd429363ab4e.png)
