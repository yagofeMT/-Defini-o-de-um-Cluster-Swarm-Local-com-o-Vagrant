Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"
  config.vm.define "master" do |master|
    master.vm.network "private_network", ip: "192.168.50.10"
    master.vm.hostname = "master"
    
    # Install Docker and initialize Docker Swarm on master
    master.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y docker.io
      docker swarm init --advertise-addr 192.168.50.10
    SHELL
  end

  config.vm.define "node01" do |node01|
    node01.vm.network "private_network", ip: "192.168.50.11"
    node01.vm.hostname = "node01"
    node01.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y docker.io
      docker swarm join --token $(ssh vagrant@192.168.50.10 docker swarm join-token -q worker) 192.168.50.10:2377
    SHELL
  end

  config.vm.define "node02" do |node02|
    node02.vm.network "private_network", ip: "192.168.50.12"
    node02.vm.hostname = "node02"
    node02.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y docker.io
      docker swarm join --token $(ssh vagrant@192.168.50.10 docker swarm join-token -q worker) 192.168.50.10:2377
    SHELL
  end

  config.vm.define "node03" do |node03|
    node03.vm.network "private_network", ip: "192.168.50.13"
    node03.vm.hostname = "node03"
    node03.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y docker.io
      docker swarm join --token $(ssh vagrant@192.168.50.10 docker swarm join-token -q worker) 192.168.50.10:2377
    SHELL
  end

end
