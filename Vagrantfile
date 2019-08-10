Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
    end
   config.vm.synced_folder "./files", "/home/vagrant/files"
	
   config.vm.network :forwarded_port, guest: 81, host: 81
   config.vm.network :forwarded_port, guest: 82, host: 82
   config.vm.network :forwarded_port, guest: 9000, host: 9000
   config.vm.network :forwarded_port, guest: 5000, host: 5000


   config.vm.provision "shell", privileged: true, inline: <<-SHELL
     apt-get update
     apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y
	 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
     add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
     apt-get update
     apt-get install docker-ce docker-ce-cli containerd.io -y
     curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
     chmod +x /usr/local/bin/docker-compose
   SHELL
end
