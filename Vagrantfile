# ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'


VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	# config.vm.provider = "libvirt"


	config.vm.define :virtual_test do |machine|

		config.vm.provider :libvirt do |libvirt|
			# Display the VirtualBox GUI when booting the machine
			# libvirt.gui = false

			# Customize the amount of memory on the VM:
	  		libvirt.memory = "1024"
			libvirt.cpus = "3"
			# libvirt.host = "test.boe"
			# libvirt.driver="virtualbox"
		end



		machine.vm.box = "centos/7"
	#	machine.vm.box = "fedora/25-cloud-base"
		machine.vm.hostname = "test.boe"
		machine.vm.network :private_network, :ip => "192.168.33.13",
		# :dev => 'virbr0-nic',
		:type => 'bridge',
		:mode => 'bridge'
		# machine.vm.network "forwarded_port", guest: 80, host: 8088
		# machine.vm.network "forwarded_port", guest: 22, host: 2232
		# machine.vm.network "forwarded_port", guest: 433, host: 8433

		# machine.ssh.port = 2222
		# machine.ssh.guest_port = 2222

		# machine.vm.network :private_network,
		# 	:ip => "192.168.44.110"
			# :libvirt__dhcp_enabled => false

		# machine.vm.network :public_network,
		# 	# :auto_config => 'false',
		# 	:libvirt__dhcp_enabled => false,
		# 	# :dev => "wlp5s0",
		# 	:type => 'bridge',
		# 	:mode => 'bridge'

		# machine.vm.network :public_network,
		# 	# :auto_config => 'false',
		# 	:libvirt__dhcp_enabled => false,
		# 	:type => 'bridge',
		# 	:mode => 'bridge',
		# 	# :dev => "wlp5s0",
		# 	:ip => "192.168.121.211"
			# :netmask => "255.255.255.0"
		# machine.vm.network "public_network", ip: "192.168.121.245"
		# machine.vm.network "public_network", :bridge => 'eth0', ip: "192.168.121.245"
		# machine.vm.network "public_network", :bridge => 'en1: Wi-Fi (AirPort)'
		# machine.vm.network :hostonly, :ip => "192.168.121.246"
		# machine.vm.synced_folder "~/Public/test/ansible/", "/usr/share/nginx/html/", type: "rsync", rsync__exclude: ".git/", rsync__args: ["--verbose", "--rsync-path='sudo rsync'", "--archive", "--delete", "-z"]
		# machine.vm.synced_folder "~/Public/", "/opt/vagrant/", type: "sshfs"


	   machine.vm.provision "ansible" do |ansible|
	     ansible.playbook = "docker-jenkins.yml"
	   end
   end
end


#

#
