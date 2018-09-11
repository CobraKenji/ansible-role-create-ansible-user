Role Name
=========
roles/create-ansible-user

Create new sudo user on remote machine.

Copy SSH keys from files/rsa.pub to remote machines authorized_keys

Optional: configure passwordless sudo access for new sudo user. To apply passwordless sudo, uncomment the task ("Ensure passwordless sudo..."").

Note: To expedite play, gather_facts=false in role-local ansible.cfg.


Requirements
------------
None



Role Variables
--------------

You will need to:
- adjust the target hosts.
- append your SSH key (~/.ssh.id_rsa.pub) to files/rsa.pub
- input new username and password upon playbook execution


Dependencies
------------
None


Example Playbook
----------------
Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
---
- hosts: all
  gather_facts: false
  vars_prompt:
    - name: new_admin_user
      prompt: "Enter new sudoer username"
      default: ''
      private: no
      failed_when: new_admin_user == '' or new_admin_user == 'root'
    - name: adminpw
      prompt: "Carefully enter password"
      default: ''
      private: yes
      failed_when: adminpw == ''

  tasks:
    - include: tasks/main.yml
```

License
-------
GPLv2


Author Information
------------------
CobraKenji
2018
