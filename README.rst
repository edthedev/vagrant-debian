Create the virtual machine::

    cd vagrant-debian # directory next to Vagrantfile
    vagrant up

Install your SSH key::

    ssh-keygen -t rsa # (if needed)
    cd vagrant-debian # directory next to Vagrantfile
    cp ~/.ssh/id_rsa.pub . 
    vagrant ssh
    cat /vagrant/id_rsa.pub >> ~/.ssh/authorized_keys

Add the bridged IP address to your `/etc/ansible/hosts` file::

    [vagrant]
    192.168.33.10

Modify your `playbook.yml` to only point to the Vagrant VM::

    hosts: vagrant    
    user: vagrant
    sudo: yes # necessary if you just switched away from root

Run your playbook.::

    ansible-playbook playbook.yml
