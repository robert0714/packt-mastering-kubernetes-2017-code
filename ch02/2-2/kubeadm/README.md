USAGE
================
> vagrant ssh n4
Welcome to Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-81-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 packages can be updated.
0 updates are security updates.


> sudo su - root
> cd /vagrant/scripts
> sh  bootstrap4Ubuntu_ansible.sh


> ansible-playbook /vagrant/ansible/playbook.yml  -i  /vagrant/ansible/hosts/all  

