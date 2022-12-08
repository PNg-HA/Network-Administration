# Create VLAN in Cisco switch with Ansible
> **Note**  
> This task is based on the topology (devices already set up) in 'Net challenge' repository.

Create file `hosts` in /etc/ansible với nội dung:
     
     sw3 ansible_host=172.3.1.98
     
Create file `make_vlan_switch.yml`:
     
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
    
    $ anislbe-playbook make_vlan_switch.yml

 > or `$ anislbe-playbook make_vlan_switch.yml -vvvv` if you want to discover more 
 > about the operation of Ansible playbook or debug.

Reference: 
  
1. https://www.youtube.com/watch?v=wbVZkb8ocH4&ab_channel=KevinWallaceTraining%2CLLC
2. https://docs.ansible.com/ansible/2.5/modules/ios_config_module.html
