# Vagrant

## Notizen
* Standardmäßig wird das erste Device als NAT konfiguriert

## Kommandozeile


## Beispiel
### Vagrantfile
```
Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  
  config.vm.provider "virtualbox" do |v|
    v.name = "ansible_debian"
    v.memory = 1024
    v.cpus = 2
  end
  
  config.vm.network "public_network", :mac=> "aa22bbccddee", bridge: "enp4s0"
  config.vm.hostname = "ansible"
  
  config.ssh.private_key_path = ["keys/private", "~/.vagrant.d/insecure_private_key"]
  config.ssh.insert_key = false
  config.vm.provision "file", source: "keys/public", destination: "~/.ssh/authorized_keys"
  config.vm.provision "shell", path: "provision.sh"
end
```

### Provisioning
```
sudo useradd -m -s /bin/bash jdoe
```