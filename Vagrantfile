# -*- mode: ruby -*-
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
  config.vm.box = "hashicorp/bionic64"
  # config.disksize.size = "50GB"


  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  config.vm.network "forwarded_port", guest: 8025, host: 8025, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 3000, host: 3000, host_ip: "127.0.0.1"
  # config.vm.network "forwarded_port", guest: 22, host: 222, host_ip: "127.0.0.1"

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
  config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "~/", "/home/vagrant/host_home"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
    vb.gui = false
  #
  #   # Customize the amount of memory on the VM:
    vb.memory = "4096"
    vb.cpus = 2
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  config.vm.provision "ansible" do |ansible|
    ansible.galaxy_role_file = "provision/requirements.yml"
    ansible.playbook = "provision/playbook.yml"
    ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
  end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
=begin

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get -y upgrade
  #   apt-get -y software-properties-common \
    apt-get -y install build-essential git-core curl unison \
                                       software-properties-common \

                       libssl-dev \
                       libyaml-dev \
                       libsqlite3-dev \
                       libreadline-dev \
                       zlib1g zlib1g-dev \
                       libcurl4-openssl-dev \
                       libxslt-dev libxml2-dev \

    apt-add-repository --yes --update ppa:ansible/ansible
    # Install unison:
    apt-get -y install unison ansible
    # Configure git
    git config --global user.name "Your Name"
    git config --global user.email you@example.com

    # Install krypton
    curl https://krypt.co/kr | sh 

    git clone git://github.com/sstephenson/rbenv.git /usr/local/rbenv

    # Add rbenv to the path:
    echo '# rbenv setup' > /etc/profile.d/rbenv.sh
    echo 'export RBENV_ROOT=/usr/local/rbenv' >> /etc/profile.d/rbenv.sh
    echo 'export PATH="$RBENV_ROOT/bin:$PATH"' >> /etc/profile.d/rbenv.sh
    echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh
    chmod +x /etc/profile.d/rbenv.sh
    source /etc/profile.d/rbenv.sh

    # Install ruby-build:
    pushd /tmp
      git clone git://github.com/sstephenson/ruby-build.git
      cd ruby-build
      ./install.sh
    popd
    # Install Ruby 2.6.3:
    rbenv install  2.6.3
    rbenv global   2.3.3
    # Rehash:
    rbenv rehash
  SHELL
=end

end
