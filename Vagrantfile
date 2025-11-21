Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  config.vm.define "frontend" do |frontend|
    frontend.vm.hostname = "frontend-server"
    frontend.vm.network "private_network", ip: "192.168.56.11"
    frontend.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end
  end
end
