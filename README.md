Role Name
=========

An Ansible role for setup of RabbitMQ Cluster.

Requirements
------------

Needs minimum 2 instances to work with. One Master node, rest worker nodes. A change in the number of instances/nodes will result in edits in inventory file and in the default/main.yml file.


Role Variables
--------------

Variables to be set by the user are:

1. `master.ip` : Set the ip of the master node here.

2. `master.name` : Set up the hostname of the master node here.

3. `slave01.ip` : Set the ip of the 1st slave node here.

4. `slave01.name` : Set the hostname of the 1st slave here.

5. `slave02.ip` : Set the ip of the 2nd slave node here.

6. `slave02.name` : Set the hostname of the 2nd slave here.

7. `rabbit_username` : Set the username of the rabbitmq user over here which will have admin access.

8. `rabbit_password` : Set the password of the rabbitmq user over here which will have admin access.

 - Note: Don't change other variables in the file, those varibles are fixed values which shouldn't be changed before executing the playbook.

Example Playbook
----------------

You can create a simple master playbook to run this role:
```yml
- hosts: all
  become: yes
  become_method: sudo
  become_user: root
  roles:
    - rabbitmq-cluster
```

Example Inventory File
----------------------
Use the same naming convention as stated in the below example, like for adding worker nodes use the nomenclature slave(n) - where n would be a two-digit number.

You have to list the nodes in the inventory.yml file in the following format:

```yml
all:
  hosts:
    master:
      ansible_host: vagrant@192.168.33.10
    slave01:
      ansible_host: vagrant@192.168.33.11
    salve02:
      ansible_host: vagrant@192.168.33.12
```

 - Note: You can also use the ini format for the inventory file, but you have to make sure the there is atleast one master node and rest are worker nodes.

- Note: Using a different format of inventory file format will have an effect on the playbook, make sure to customise the playbook according to the changes in the inventory file - like adding up of mode slave nodes or removing slave nodes.

License
-------

BSD

Author Information
------------------

- Initial Work - Alizey Jalil (alizey.jalil@gdn-commerce.com)
