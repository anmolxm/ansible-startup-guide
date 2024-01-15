# ansible-startup-guide
Embark on your Ansible journey with the 'ansible-startup-guide' repository! Tailored for beginners, this repo provides concise, step-by-step tutorials and examples, guiding you through essential Ansible tasks for effective configuration management. Elevate your skills and master Ansible automation effortlessly.

## Contents

### Task 1: Software Installation on Slave Nodes

The first set of tasks focuses on software installation on designated slave nodes. These tasks utilize Ansible playbooks to ensure the presence of necessary software on target servers. For example:

```yaml
---
- name: task for assign1 on slave1
  hosts: slave1
  become: true
  tasks:
    - name: java install on slave1
      apt: name=openjdk-11-jdk update_cache=yes state=latest

- name: task for assign1 on slave2
  hosts: slave2
  become: true
  tasks:
    - name: my-sql install on slave2
      apt: name=mysql-server update_cache=yes state=latest
```

### Task 2: Script Execution on Slave1

The second task involves running a custom script on slave1. Ansible facilitates script execution, providing a flexible way to automate tasks. Example playbook snippet:

```yaml
---
- name: task for assign2 on slave1
  hosts: slave1
  become: true
  tasks:
    - name: running a script on slave1
      script: assign2.sh
```

### Task 3: Web Server Setup on Slave Nodes

Task 3 demonstrates how to set up web servers on designated slave nodes. This includes the installation of Apache2 on slave1 and Nginx on slave2. Example playbook excerpt:

```yaml
---
- name: task for assign3 on slave1
  hosts: slave1
  become: true
  tasks:
    - name: apache2 install on slave1
      apt: name=apache2 update_cache=yes state=latest

- name: task for assign3 on slave2
  hosts: slave2
  become: true
  tasks:
    - name: nginx server install on slave2
      apt: name=nginx update_cache=yes state=latest
```
### Task 4: Custom HTML Files for Nginx and Apache

# nginx/copy.yaml
---
- name: replace default nginx page with custom html file
  copy: src=/etc/ansible/roles/nginx/files/index.html dest=/var/www/html/

# apache/copy.yaml
---
- name: replace default apache page with custom html file
  copy: src=/etc/ansible/roles/apache/files/index.html dest=/var/www/html/

### Task 5: Configuring Java and MySQL Roles

This playbook executes Ansible roles for the test and prod groups, installing Java for the test group and MySQL for the prod group. Adjust the playbook and roles as needed for your specific requirements.

---
- name: running java role for test group
  hosts: test
  become: true
  roles:
    - java

- name: running mysql role for prod group
  hosts: prod
  become: true
  roles:
    - mysql
-------------------------------------------------------------------------END---------------------------------------------------------------------

Happy automating!

— anmolxm
