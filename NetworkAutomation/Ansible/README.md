## Introduction

Ansible is a tool to automatically configure other devices in the same network through SSH, such as switches, routers, computers, etc. However, in this repository, Ansible is used to add additional settings which do not change the based network opration.

## Getting started with Ansible
### Control node
A computer on which Ansible is installed. Ansible is only running on Linux, so this computer should have WSL if its is Windows.
### Managed node
A remote system, or host, that Ansible controls. It is not required to have Ansible, but must be in the same network and SSH is available.

![image](https://user-images.githubusercontent.com/93396414/206394983-f1659380-bbd5-4feb-a0c4-6e6b13733c0b.png)

