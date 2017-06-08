VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	config.vm.provider "virtualbox" do |vb|
		# Display the VirtualBox GUI when booting the machine
		vb.gui = false

		# Customize the amount of memory on the VM:
  		vb.memory = "1024"
		vb.name = "test.boe"
	end


	config.vm.box = "centos/7"
#	config.vm.box = "fedora/25-cloud-base"
	config.vm.hostname = "test.boe"
	config.vm.network "forwarded_port", guest: 80, host: 8088
	config.vm.network "forwarded_port", guest: 2222, host: 2233
	config.vm.network "forwarded_port", guest: 433, host: 8433

	config.ssh.port = 2233
	config.ssh.guest_port = 2222

	config.vm.network "private_network", ip: "192.168.33.11"
	config.vm.network "public_network", :bridge => 'en1: Wi-Fi (AirPort)'
	# config.vm.network :hostonly, "192.168.232.1"
	# config.vm.synced_folder "~/Public/test/ansible/", "/usr/share/nginx/html/", type: "rsync", rsync__exclude: ".git/", rsync__args: ["--verbose", "--rsync-path='sudo rsync'", "--archive", "--delete", "-z"]
	# config.vm.synced_folder "~/Public/", "/opt/vagrant/", type: "sshfs"


   config.vm.provision "ansible" do |ansible|
     ansible.playbook = "boe.yml"
   end
end


#

#
