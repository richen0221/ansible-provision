Ansible Provision
=========

Description
------------

The playbook is for system basic setup on CentOS 7.

Please place the `server-ip` at the `hosts` block in the `provision.yml` file.

# Usage
`ansible-playbook provision.yml -k`
It will ask the root password

Modify the variables as below for needed.

## Variables

Create a secondary, non-root user. It will disable root login via SSH when it created.

Must add the secondary user with the `ANSIBLE_KEY` for the other roles setup. 
    
    ANSIBLE_USER_NAME: secondary_user
    
Edit `/home/user/.ssh/id_rsa.pub` where is the public key's location. use `ssh-keygen -t rsa` to generate it

    ANSIBLE_KEY: "{{ lookup('file', '/home/user/.ssh/id_rsa.pub') }}"
    
If in need, copy the `/etc/shadow` password hash and uncomment the variable.

    ANSIBLE_USER_PASSWORD:
    
root mail alias in `/etc/aliases` and for `checkhd.sh` script alert mail.

    ROOT_MAIL: admin@example.com.tw
    
Uncomment to use the local repo. Modify the `provision/tasks/localrepo.yml` and create the necessary repos in `provision/tasks/templates`.
   
    USE_LOCAL_REPO: your-yum-server.com

License
-------

BSD

Author Information
------------------

Ricky Chen