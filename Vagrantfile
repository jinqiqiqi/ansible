# -*- mode: ruby -*-
# vi: set ft=ruby :
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
servers = [
  {
    :hostname => 'master',
    :ip => '192.168.33.40',
    :memory => "512",
    :cpus => 2
    # :forwards => {
    #   80 => 1081,
    #   443 => 1443
    # }
  },
  {
    :hostname => 'slave1',
    :ip => '192.168.33.41',
    :memory => "256",
    :cpus => 2
        # :forwards => {
    #   80 => 1082,
    #   443 => 1444
    # }
  },
  {
    :hostname => 'slave2',
    :ip => '192.168.33.42',
    :memory => "256",
    :cpus => 2
    # :forwards => {
    #   80 => 1082,
    #   443 => 1444
    # }
  }
  # ,
  # {
  #   :hostname => 'client',
  #   :ip => '192.168.33.43',
  #   :memory => "256",
  #   :cpus => 2
  #   # :forwards => {
  #   #   80 => 1082,
  #   #   443 => 1444
  #   # }
  # }
  # ,

  # {
  #   :hostname => 'slave3',
  #   :ip => '192.168.33.44',
  #   :memory => "256",
  #   :cpus => 2
  #   # :forwards => {
  #   #   80 => 1082,
  #   #   443 => 1444
  #   # }
  # }
  # ,
  # {
  #   :hostname => 'slave4',
  #   :ip => '192.168.33.45',
  #   :memory => "256",
  #   :cpus => 2
  #   # :forwards => {
  #   #   80 => 1082,
  #   #   443 => 1444
  #   # }
  # },
  # {
  #   :hostname => 'slave5',
  #   :ip => '192.168.33.46',
  #   :memory => "256",
  #   :cpus => 2
  #   # :forwards => {
  #   #   80 => 1082,
  #   #   443 => 1444
  #   # }
  # },
  # {
  #   :hostname => 'slave6',
  #   :ip => '192.168.33.47',
  #   :memory => "256",
  #   :cpus => 2
  #   # :forwards => {
  #   #   80 => 1082,
  #   #   443 => 1444
  #   # }
  # }
  # ,
  # {
  #   :hostname => 'slave7',
  #   :ip => '192.168.33.48',
  #   :memory => "256",
  #   :cpus => 2
  #   # :forwards => {
  #   #   80 => 1082,
  #   #   443 => 1444
  #   # }
  # },
  # {
  #   :hostname => 'slave8',
  #   :ip => '192.168.33.49',
  #   :memory => "256",
  #   :cpus => 2
  #   # :forwards => {
  #   #   80 => 1082,
  #   #   443 => 1444
  #   # }
  # }
]


VAGRANT_API_VERSION = "2"
Vagrant.configure(VAGRANT_API_VERSION) do |config|

  config.vm.box = "centos/7"
  config.vm.box_check_update = false

  servers.each do |opts|
    config.vm.define opts[:hostname] do |server_config|
      server_config.vm.hostname = opts[:hostname]
      server_config.vm.network :private_network, :ip => opts[:ip],
      # :dev => 'virbr0-nic',
      :type => 'bridge',
      :mode => 'bridge'
    #   server_config.vm.network :public_network, :dev => 'wlp5s0'

      opts[:forwards].each do |guest_port, host_port|
        config.vm.network :forwarded_port, guest: guest_port, host: host_port
      end if opts[:forwards]

      server_config.vm.provider :libvirt do |vm|
        # vm.name = opts[:hostname]
        vm.memory = opts[:memory]
        vm.cpus = opts[:cpus]
        # vm.storage :file, :size => '2G', :allow_existing => true, :type => 'qcow2'
      end
    end

    # config.vm.provision "ansible" do |ansible|
    #   ansible.playbook = "/Users/kinch/Public/devops/ansible/ansible_test/hadoop.yml"
    # end


  end


  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.

  # config.ssh.guest_port = 22
  # config.ssh.port = 2255

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # config.vm.network "forwarded_port", guest: 22, host: 2255, host_ip: "127.0.0.1", id: 'ssh'

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.20"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network", bridge: "en1: Wi-Fi (AirPort)"

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



  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = false
  #   vb.name = "hadoop-namenode"
  #
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  #
  #
  #
  #
  # end

  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #
  #   # yum install -y mariadb-server mariadb-devel sqlite-devel ImageMagick-devel
  #   # yum install -y ruby-devel gem rubygem-bundler rubygem-json rubygems-devel
  #   # yum install -y git
  #   # git clone https://github.com/redmine/redmine.git /home/vagrant/redmine/ && echo 'gem "json", "~> 2.0", "~> 2.0.2"' >> /home/vagrant/redmine/Gemfile
  #   #
  #   # cd /home/vagrant/redmine/
  #   # bundle install —-without development test
  #   # bundle exec rake generate_secret_token
  #   # RAILS_ENV=production bundle exec rake db:migrate
  #   # RAILS_ENV=production REDMINE_LANG=zh bundle exec rake redmine:load_default_data
  #   #
  #   # mkdir -p tmp tmp/pdf public/plugin_assets
  #   # sudo chown -R vagrant:vagrant files log tmp public/plugin_assets
  #   # sudo chmod -R 755 files log tmp public/plugin_assets
  #
  # SHELL
end
