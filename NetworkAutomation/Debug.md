 ## Fix: paramiko is not installed, no module named 'paramiko'
 This solution is for python3.
 You need the server connected to Internet (to download).
 
      $ sudo apt install python3-pip
      $ pip3 install paramiko

## Commands, options to debug:

 - ansible-playbook playbook-file.yml --syntax-check
 - ansible-playbook playbook-file.yml -vvvv

https://askubuntu.com/questions/719058/blk-update-request-i-o-error-dev-fd0-sector-0
