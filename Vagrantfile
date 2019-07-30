Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
    end
	
   config.vm.network :forwarded_port, guest: 81, host: 81
   config.vm.network :forwarded_port, guest: 80, host: 80
   config.vm.network :forwarded_port, guest: 9000, host: 9000
   config.vm.network :forwarded_port, guest: 5000, host: 5000


   config.vm.provision "shell", privileged: true, inline: <<-SHELL
     apt-get update
     apt install apt-transport-https ca-certificates curl software-properties-common -y
	 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add – 
     add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable" 
     apt update
     apt install docker-ce -y
     apt install docker-compose -y
   SHELL
end
