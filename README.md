patching
=========

This role to updates the linux system ( Redhat or Centos ) as follows:  
1- Prechecks like Repository checks, and gather all your mandatory checks information(mount,ip details,routing,services,etc).  
2- if repository is success, patch the server.  
3- if patch the server reboot.  
4- wait for  server booting, once back and validate your server with your precheck data.  


There are 2 Patching_type you can use:  
  - NOREBOOT
  - KERNEL (FULL )

Role Variables
--------------
The variables that can be passed to this role are as follows:  
```
supported_distros:  
  - Redhat
  - CentOS
```
local_dir is a directory where to store the logs during the playbooks is running. Default: /tmp/ansible/sys-patching:  
local_dir: "/tmp/ansible/os-patching"  

Patching_type: KERNEL --> Full patch with reboot , NOREBOOT . Default: KERNEL:  
Patching_type:  KERNEL  

Requirements
------------
These playbooks were designed to be used in Linux system  (RHEL and centos for now ). You need to have a valid yum repository on each managed node.


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too :)  
```
---  
- name: Patching the linux system using patching roles  
  hosts: all  
  become: true  
  vars:  
    Patching_type: "KERNEL"  
  roles:  
    - patching  
```

Playbook Execution
------------------

ansible-playbook patching_linux.yml --extra-vars="ansible_hostname=targethostname" -vvv
 
