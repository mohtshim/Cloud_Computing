### Install MySQL using Ansible Playbook
For this problem we assume that you have ansible installed on your master node. For this demonstration we are installing mysql on the master node instead of on the worker nodes.
You can configure the worker node and link them to the master node using ssh.

Make a folder on your master node named as "Mysql using ansible". After that write this command 
```
nano playbook.yml
```
This will open a nano editor.

![image](https://user-images.githubusercontent.com/46097990/190954648-b29ec8f1-67cc-4cd6-b22a-b66b93ddc34c.png)

Write these command in the playbook and save it.
```
- name: installing mysql
  become: yes
  hosts: localhost
  tasks:
    - name: Installing Mysql  and dependencies
      package:
       name: "{{item}}"
       state: present
       update_cache: yes
     loop:
       - mysql-server
       - mysql-client 
       - python3-mysqldb
       - libmysqlclient-dev
     become: yes
    - name: start and enable mysql service
      service:
        name: mysql
        state: started
        enabled: yes
  handlers:
    - name: Restart mysql
      service:
        name: mysql
        state: restarted
```
After writing that in that playbook we can check the syntax of the playbook that whether it is correct or not.
```
ansible-playbook --syntax-check playbook.yml
```
![image](https://user-images.githubusercontent.com/46097990/190956302-a7f26ac5-83d2-4e48-b6c9-cc1143af49a6.png)

After that run the paybook
```
ansible-playbook -K playbook.yml
```
Its gonna ask for your account password for the sudo privilages. After running the playbook we have mysql running on our master node.

![image](https://user-images.githubusercontent.com/46097990/190963641-11c328fd-0fc0-4942-886c-4be039758d50.png)


