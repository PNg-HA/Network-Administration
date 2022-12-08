### Ubuntu server SSH to switch
This task is related to 'Net challenge' repository
## Task3: Network automation with Ansible.
Tạo file hosts trong /etc/ansible với nội dung:
     
     sw3 ansible_host=172.3.1.98
     
Tạo file make1.yml:
     
     ---
     #This playbook creates vlan 11
     
     - hosts: sw3
       gather_facts: false
       connection: local
       
       vars: 
          cli:
               username: pngha
               password: pngha
               timeout: 100
       tasks:
          - name: make vlan 11
            ios_config: 
               provider: "{{cli}}"
               lines:
                    - name Core
               parents:
                    - vlan 11
            register: print_output
            
         - name:
           ios_config: "{{cli}}"
           lines:
               - switchport mode access 
               - switchport access vlan 11
           parents:
               - interface Ethernet0/1
     
In terminal, type:
    
    $ anislbe-playbook make1.yml



Referenced: 
  
1. https://www.youtube.com/watch?v=wbVZkb8ocH4&ab_channel=KevinWallaceTraining%2CLLC
2. https://docs.ansible.com/ansible/2.5/modules/ios_config_module.html
