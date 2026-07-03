# Usage Examples

This page covers common patterns for using `techgeek68/fedora44-arm64` in real projects.

## Basic Vagrantfile

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "techgeek68/fedora44-arm64"
  config.vm.box_version = "1.0.0"
end
```

## Setting Memory and CPU

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "techgeek68/fedora44-arm64"
  config.vm.box_version = "1.0.0"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end
end
```

## Setting a Hostname

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "techgeek68/fedora44-arm64"
  config.vm.hostname = "dev-fedora-arm64"
end
```

## Adding a Shared Folder

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "techgeek68/fedora44-arm64"
  config.vm.synced_folder "./app", "/vagrant/app"
end
```

> **Assumption:** Shared folder performance and default sync mechanism follow standard Vagrant and VirtualBox behavior. Test with your own workload before relying on this in production tooling.

## Forwarding an Additional Port

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "techgeek68/fedora44-arm64"
  config.vm.network "forwarded_port", guest: 8080, host: 8080
end
```

## Shell Provisioning

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "techgeek68/fedora44-arm64"

  config.vm.provision "shell", inline: <<-SHELL
    dnf update -y
    dnf install -y git
  SHELL
end
```

## Ansible Provisioning

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "techgeek68/fedora44-arm64"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
```

## Multi Machine Setup

```ruby
Vagrant.configure("2") do |config|
  config.vm.define "web" do |web|
    web.vm.box = "techgeek68/fedora44-arm64"
    web.vm.hostname = "web"
  end

  config.vm.define "db" do |db|
    db.vm.box = "techgeek68/fedora44-arm64"
    db.vm.hostname = "db"
  end
end
```

## Running Commands Without an Interactive Shell

```
vagrant ssh -c "uname -a"
```

## Checking VM Status

```
vagrant status
```

## Full Command Reference

For the complete set of Vagrant commands, see the [official Vagrant CLI documentation](https://developer.hashicorp.com/vagrant/docs/cli).
