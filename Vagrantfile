machines = {
  "master" => {"memory" => "1024", "cpu" => "1", "ip" => 100, "image" => "bento/ubuntu=22-04"},
  "node1" => {"memory" => "1024", "cpu" => "1", "ip" => 100, "image" => "bento/ubuntu=22-04"},
  "node2" => {"memory" => "1024", "cpu" => "1", "ip" => 100, "image" => "bento/ubuntu=22-04"},
  "node3" => {"memory" => "1024", "cpu" => "1", "ip" => 100, "image" => "bento/ubuntu=22-04"}
}

Vagrant.configure("2") do ׀config׀

  machines.each do ׀name, conf׀
    config.vm.define "#{name}" do ׀machine׀
      machine.vm.box = "#{conf["image]}"
      machine.vm.hostname = "#{name}"
      machine.vm.network "private_network", ip: "10.10.10.#{conf["ip]}"
      machine.vm.provider "virtualbox do ׀vb׀
          vb.name = "#{name}"
          vb.memory = "#{memory}"
          vb.cpus = conf["cpu"]
        end

        machine.vm.provision "shell", path: docker.sh

        if "#{name}" == "master"
          machine.vm.provision "shell", path: "master.sh"
        else
          machine.vm.provision "shell", path: "worker.sh"
        end
      end
    end
end
