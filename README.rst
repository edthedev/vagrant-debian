Create the virtual machine::

    vagrant up

Install your SSH key::

    vagrant ssh
    cat /vagrant/id_rsa.pub >> ~/.ssh/authorized_keys

Add the bridged IP address to your `/etc/ansible/hosts` file::

    [vagrant]
    192.168.33.10

Modify your `playbook.yml` to only point to the Vagrant VM::

    hosts: vagrant    

Run your playbook.::

    ansible-playbook playbook.yml
