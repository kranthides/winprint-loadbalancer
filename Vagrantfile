# -*- mode: ruby -*-
# vi: set ft=ruby :

# set the default provider
ENV["VAGRANT_DEFAULT_PROVIDER"] = "virtualbox"

Vagrant.configure(2) do |config|

#---box1---
  config.vm.define :"spool-ps1" do |box1|
    box1.vm.box = "windows_2008_r2"
    box1.vm.hostname = "spool-ps1"
    #box1.vm.network :private_network, ip: "192.168.33.101", gateway: "192.168.33.1"
    #box1.vm.network :public_network, ip: "192.168.2.231", bridge: "en0: Wi-Fi (AirPort)"
    box1.vm.network :public_network, ip: "10.100.30.231", bridge: "en4: Thunderbolt Ethernet"

    box1.vm.provider :virtualbox do |vb, override|
      vb.gui = true
      vb.name = "spool-ps1"
      vb.customize ["modifyvm", :id, "--memory", 1024]
      vb.customize ["modifyvm", :id, "--cpus", 1]
      vb.customize ["modifyvm", :id, "--vram", "32"]
      vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
      vb.customize ["setextradata", "global", "GUI/SuppressMessages", "all" ]
    end
    box1.vm.provision "shell", path: "scripts/install-role-printserver.ps1", privileged: false
    box1.vm.provision "shell", path: "scripts/install-loopback-adapter-nic2.ps1", privileged: false
    box1.vm.provision "shell", path: "install/install-monitor.bat", privileged: false
  end
#---box1---

#---box2---
  config.vm.define :"spool-ps2" do |box2|
    box2.vm.box = "windows_2008_r2"
    box2.vm.hostname = "spool-ps2"
    #box2.vm.network :private_network, ip: "192.168.33.102", gateway: "192.168.33.1"
    #box2.vm.network :public_network, ip: "192.168.2.232", bridge: "en0: Wi-Fi (AirPort)"
    box2.vm.network :public_network, ip: "10.100.30.232", bridge: "en4: Thunderbolt Ethernet"

    box2.vm.provider :virtualbox do |vb, override|
      vb.gui = true
      vb.name = "spool-ps2"
      vb.customize ["modifyvm", :id, "--memory", 1024]
      vb.customize ["modifyvm", :id, "--cpus", 1]
      vb.customize ["modifyvm", :id, "--vram", "32"]
      vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
      vb.customize ["setextradata", "global", "GUI/SuppressMessages", "all" ]
    end
    box2.vm.provision "shell", path: "scripts/install-role-printserver.ps1", privileged: false
    box2.vm.provision "shell", path: "scripts/install-loopback-adapter-nic2.ps1", privileged: false
    box2.vm.provision "shell", path: "install/install-monitor.bat", privileged: false
  end
#---box2---

#---box3---
  config.vm.define :"spool-win7" do |box3|
    box3.vm.box = "windows_7"
    box3.vm.hostname = "spool-win7"
    box3.vm.network :private_network, ip: "192.168.33.107", gateway: "192.168.33.1"

    box3.vm.provider :virtualbox do |vb, override|
      vb.gui = true
      vb.name = "spool-win7"
      vb.customize ["modifyvm", :id, "--memory", 1024]
      vb.customize ["modifyvm", :id, "--cpus", 1]
      vb.customize ["modifyvm", :id, "--vram", "32"]
      vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
      vb.customize ["setextradata", "global", "GUI/SuppressMessages", "all" ]
    end
  end
#---box3---

end
