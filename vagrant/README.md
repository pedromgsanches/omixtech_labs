## Tutorial "10min" Vagrant // how to
Criar quatro servidores com recurso a vagrant, imagem oficial "Oracle Linux 8".

# Como executar o exemplo do tutorial:
1- Download + instalar vagrant: https://www.vagrantup.com/
2- $ vagrant box add --name ol8 https://yum.oracle.com/boxes/oraclelinux/ol80/ol80.box
2- Criar ficheiro Vagrantfile
3- $ vagrant up
4- $ vagrant ssh <máquina-como-descrito-no-Vagrantfile>


# Para criarmos apenas um servidor e mais rápido:
$ vagrant init oraclelinux/8 https://oracle.github.io/vagrant-projects/boxes/oraclelinux/8.json
$ vagrant up
$ vagrant ssh