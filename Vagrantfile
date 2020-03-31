Vagrant.configure("2") do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  #hashicorp/bionic64 - 18.04.4
  #hashicorp/precise64 - ubuntu 12.04
  config.vm.box = "hashicorp/bionic64"
  # config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # Make it possible to use the SSH keys from the host
  config.ssh.forward_agent = true

  # Forward guest port 4000 to host port 4000 (for Jekyll)
  #  config.vm.network "forwarded_port", guest: 4000, host: 4000

  # Forward guest port 8787 to host port 8788 (for RStudio Server)
  #  config.vm.network "forwarded_port", guest: 8787, host: 8787

   config.vm.network "private_network", ip: "192.168.50.110",
    virtualbox__intnet: true
  # Forward guest port 5432 to host port 5432 (for PostgreSQL)
   config.vm.network "forwarded_port", guest: 5432, host: 5432

  # Forward guest port 7474 to host port 7474,7687 (for Neo4J)
   config.vm.network "forwarded_port", guest: 7474, host: 7474
   config.vm.network "forwarded_port", guest: 7687, host: 7687

  # Change some default options for better experience, up memory and change VM name
  config.vm.provider :virtualbox do |vb|
    # Sets VM name equal to the parent directory + millis when started
    vb.name = Dir.pwd().split("/")[-1] + "-" + Time.now.to_f.to_i.to_s
    vb.memory = 4096
  end

  # Run the provision.sh file, which install Ansible on the guest VM
  config.vm.provision :shell do |sh|
    sh.path = "scripts/provision.sh"
  end
end
