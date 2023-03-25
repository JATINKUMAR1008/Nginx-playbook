# Nginx-playbook


A Ansible playbook for installing Nginx on Slave hosts and copying a page from master to all slave
Running it on nginx and make it visible on the slave hosts at port number 80.


![image](https://user-images.githubusercontent.com/97216852/227734806-b276031e-2991-48af-ad0e-d8a649b9e71b.png)

in this Ansible_Master is a master system and other are slaves they require .pem key for ssh connection



//ansible_inventory

[slaves]
slave1 ansible_host=public_ip_1
slave2 ansible_host=public_ip_2
slave3 ansible_host=public_ip_3

[all:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_ssh_private_key_file=~/.ssh/ansible_key
ansible_user=ubuntu

//

write a playbook for hosts (all)

nginx.yaml in repo

anad then use 

ansible-playbook -i hosts nginx.yaml    

This command will automatically make changes to all the slave and start nginx with new page from master system.

![image](https://user-images.githubusercontent.com/97216852/227735059-10d58ea4-9f54-44ff-b96b-197365bbce8c.png)

output like this will display and now you can check your page on the public_ip of slave on port number 80.

![image](https://user-images.githubusercontent.com/97216852/227735178-51f0db86-1a4d-4eb0-92f3-63f7c86cbb8f.png)
