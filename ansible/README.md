# Tutorial "10min" Ansible // how to

Instalar MariaDB em três servidores OracleLinux8 (previamente criados com Vagrant)


## Como executar o exemplo do tutorial:

$ vagrant ssh dbatools

$ sudo dnf -y install net-tools bind-utils python3 epel-release ansible-core

$ ssh-keygen -t rsa # gerar chave SSH para que o "servidor" ansible possa ligar diretamente aos restantes sem pedir password

$ cp ~/.ssh/id_rsa.pub /vagrant/dbatools.id_rsa.pub # '/vagrant' é um volume partilhado que se encontra junto do Vagrantfile no host

$ mkdir ~/ansible && cd ~/ansible

$ curl -O https://dlm.mariadb.com/3899605/MariaDB/mariadb-11.5.2/bintar-linux-systemd-x86_64/mariadb-11.5.2-linux-systemd-x86_64.tar.gz

### Adicionar o conteúdo de "hosts" ao /etc/hosts

$ vi inventory # colocar o conteúdo do ficheiro deste repositório com o mesmo nome

$ vi install-mariadb.yml # colocar o conteúdo do ficheiro deste repositório com o mesmo nome

$ vi my.cnf.j2 # colocar o conteúdo do ficheiro deste repositório com o mesmo nome


## Autorizar login do "dbatools" nos restantes servidores:

$ vagrant ssh dbasrv0[1-3]

$ cat /vagrant/dbatools.id_rsa.pub >> ~/.ssh/authorized_keys


### Executar o playbook, no dbatools:

$ ansible-playbook -i ./inventory install-mariadb.yml 



## Confirmar instalação:

$ vagrant ssh dbasrv0[1-3]

$ sudo su -

$ cd /opt/mariadb/bin/bin

$ ./mariadb --socket=/opt/mariadb/conf/mysql.sock

$ mariadb> MariaDB [(none)]> show databases;
