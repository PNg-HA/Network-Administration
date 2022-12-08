## Topology:

![image](https://user-images.githubusercontent.com/93396414/205435296-03e0b5b7-7791-4044-9bb6-17cbe479b1e5.png)


  Create file `hosts` in /etc/ansible directory:
    
    [router]
    R9 ansible_host=172.3.1.97
  
 
  Create file hostname.yml in the same directory: 
  
    ---
    - name: IPv6
      hosts: router
      gather_facts: false
      connection: local
      
      vars:
        cli: 
          username: pngha
          password: pngha
          timeout: 100
          
      tasks:
        - name: global config
          ios_config:
            provider: "{{cli}}"
            lines:
              - hostname R9
            register: print_output

In terminal, type: 

    $ ansible-playbook hostname.yml

## Referenced
1. https://www.youtube.com/watch?v=wbVZkb8ocH4&ab_channel=KevinWallaceTraining%2CLLC
