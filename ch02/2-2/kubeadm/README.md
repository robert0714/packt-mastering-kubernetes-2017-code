USAGE
================
> vagrant up

> vagrant ssh n4
Welcome to Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-81-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 packages can be updated.
0 updates are security updates.


vagrant@n4:~$ sudo su - root
root@n4:~# cd /vagrant/scripts
root@n4:/vagrant/scripts# sh  bootstrap4Ubuntu_ansible.sh
root@n4:/vagrant/scripts# exit
vagrant@n4:~$ ansible-playbook /vagrant/ansible/playbook.yml  -i  /vagrant/ansible/hosts/all  


Initializing the master
================

> vagrant ssh n1

vagrant@n1:~$ sudo kubeadm init --apiserver-advertise-address  192.168.77.10
vagrant@n1:~$  mkdir -p $HOME/.kube
vagrant@n1:~$   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
vagrant@n1:~$   sudo chown $(id -u):$(id -g) $HOME/.kube/config
vagrant@n1:~$ kubectl get nodes
NAME      STATUS     AGE       VERSION
n1        NotReady   6m        v1.7.1
vagrant@n1:~$


Setting up the pod network
================

vagrant@n1:~$ kubectl create -f https://git.io/weave-kube
vagrant@n1:~$ kubectl get po --all-namespaces

and then wait for the below list
vagrant@n1:~$ kubectl get po --all-namespaces


Installtion
==============
https://kubernetes.io/docs/getting-started-guides/ubuntu/

sudo snap install conjure-up --classic
# re-login may be required at that point if you just installed snap utility
conjure-up kubernetes


 sudo   kubeadm join --token 2d05bf.a714ce0a5710462b 192.168.77.10:6443  --skip-preflight-checks