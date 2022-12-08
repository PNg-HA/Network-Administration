## Introduction

Ansible is a tool to automatically configure other devices in the same network through SSH, such as switches, routers, computers, etc. However, in this repository, Ansible is used to add additional settings which do not change the based network opration.

## Concept
### Control node
A computer on which Ansible is installed. Ansible is only running on Linux, so this computer should have WSL if its is Windows.
### Managed node
A remote system, or host, that Ansible controls. It is not required to have Ansible, but must be in the same network and SSH is available.
### Inventory
A list of managed nodes, created in **control node**, which have detais about the node, such as username, password, type of conncections, etc.
### Playbook
It contains tasks to be executed in managed nodes.
### Module
The script to do tasks.

![image](https://user-images.githubusercontent.com/93396414/206394983-f1659380-bbd5-4feb-a0c4-6e6b13733c0b.png)

### Installation Ansible in Ubuntu server 22.04
   > **Note**  
   > For convenience, I use apt. Ansible in apt is not the latest, but it does not matter.
 
Type:
    
    $ sudo apt update && sudo apt upgrade
    $ sudo apt install ansible

Check Ansible's version:
  
    $ ansible --version
    
  ![image](https://user-images.githubusercontent.com/93396414/206399123-956c4f1f-3a61-4680-8d9b-52388f4875d2.png)
  
   > **Note**  
   > Ansible recommend Python version 3.9 or more. However, for some mystery reasons, my Ubuntu server can not update Python version.

Python installed by default misses `paramiko`. To install it:

    $ sudo apt install python3-pip
    $ pip3 install paramiko
    
    ![image](https://user-images.githubusercontent.com/93396414/206519660-f4b963d7-fd6d-46c2-b2e4-350de3a06c16.png)

    
You have installed Ansible. Now check out **Ansible playbook**, the main part of this instruction.
### Ansible playbook
#### Syntax
Playbook use YAML syntax. Some tags I often use:
- name: the description
- gather_facts: get information of how the playbook operates, usually set `false`
- hosts: the objects listed in Inventory, usually set `all`
- connection: default set `local`
#### Playbook's example
For playbook example, check the `Practice` folder.
