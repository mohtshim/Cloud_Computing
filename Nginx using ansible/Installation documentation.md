### Install Nginx using Ansible Playbook
For this problem we assume that you have ansible installed on your master node. For this demonstration we are installing nginx on the master node instead of on the worker nodes.
You can configure the worker node and link them to the master node using ssh.

Make a folder on your master node named as "Nginx using ansible". After that write this command 
```
nano playbook.yml
```
This will open a nano editor.

Write these command in the playbook and save it.
```
--
- name: Install nginx
  hosts: localhost
  become: true

  tasks:
  - name: Add epel-release repo
    yum:
      name: epel-release
      state: present

  - name: Install nginx
    yum:
      name: nginx
      state: present

  - name: Start NGiNX
    service:
      name: nginx
      state: started

```
After writing that in that playbook we can check the syntax of the playbook that whether it is correct or not.
```
ansible-playbook --syntax-check playbook.yml
```
After that run the paybook
```
ansible-playbook -K playbook.yml
```
Its gonna ask for your account password for the sudo privilages. After running the playbook we have mysql running on our master node.

![image](https://user-images.githubusercontent.com/46097990/190971485-468f9ace-c4d8-44f8-b36b-d335ada2cc0f.png)
