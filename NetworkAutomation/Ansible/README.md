## Introduction

Ansible is a tool to automatically configure other devices in the same network through SSH, such as switches, routers, computers, etc. However, in this repository, Ansible is used to add additional settings which do not change the based network opration.

## Getting started with Ansible
### Control node
A computer on which Ansible is installed. Ansible is only running on Linux, so this computer should have WSL if its is Windows.
### Managed node
A remote system, or host, that Ansible controls. It is not required to have Ansible, but must be in the same network and SSH is available.
### Inventory
A list of managed nodes, created in **control node**.

![image](https://user-images.githubusercontent.com/93396414/206394983-f1659380-bbd5-4feb-a0c4-6e6b13733c0b.png)

### Installation Ansible in Ubuntu server 22.04
   > **Note**  
   > For convenience, I use apt. Ansible in apt is not the latest, but it does not matter.
 
Type:
    
    $ Ssudo apt update && sudo apt upgrade
    $ sudo apt install ansible

Check Ansible's version:
  
    $ ansible --version
    
  ![image](https://user-images.githubusercontent.com/93396414/206399123-956c4f1f-3a61-4680-8d9b-52388f4875d2.png)
  
   > **Note**  
   > Ansible recommend Python version 3.9 or more. However, for some mystery reasons, my Ubuntu server can not update Python version.

Python installed by default misses `paramiko`. To install it:

    $ sudo apt install python3-pip
    $ pip3 install paramiko
    
Now you have installed Ansible. Check out **Ansible playbook**.
### Ansible playbook
 
