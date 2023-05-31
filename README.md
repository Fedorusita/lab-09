# lab-09
# Данная лабораторная работа посвещена изучению процесса создания и конфигурирования виртуальной среды разработки с использованием Vagrant

# 1.Необходимо установить Vagrant и VirtualBox.
``` $ sudo apt-get update ```  

![image](https://github.com/Fedorusita/lab-09/assets/112895410/7158610c-8e72-407d-b7ef-59e05947f6c7)

``` $ sudo apt-get install virtualbox ```   
``` $ sudo apt-get install vagrant ```   

Проверим версию вагрант.   

``` $ vagrant --version ```   

![image](https://github.com/Fedorusita/lab-09/assets/112895410/c2fb745c-c83c-47b3-ad28-bd2682842411)


# 2. Перейдём к созданию виртуальной машины.  
Для этого в директории lab-09 создадим папку VagrantVM.   
Пропишем команду:   
``` $ vagrant init ```

Создаться файл Vagrantfile в котором мы и будем осуществлять настройку VM   
``` Ruby
 -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "bento/ubuntu-20.04"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end

```   
``` $ vagrant up ```   
К сожалению ничего работать не будет, необходимо произвести настройку через прокси   
Для этого :
```
$ export https_proxy='http://логин:пароль@ip_прокси:порт/'   
$ export VAGRANT_HTTP_PROXY=${http_proxy}   
$ export VAGRANT_NO_PROXY="127.0.0.1"   
$ vagrant up   

```

Также к нашей виртуальной машине мы можем подключиться по ssh. Для этого:   
``` $ vagrant ssh <название машины> ```   






