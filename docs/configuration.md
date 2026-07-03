# Configuration Options

This page documents the `Vagrantfile` and VirtualBox provider options relevant to `techgeek68/fedora44-arm64`.

## Box Level Options

| Option | Description | Example |
|---|---|---|
| `config.vm.box` | Box name to use | `"techgeek68/fedora44-arm64"` |
| `config.vm.box_version` | Pin a specific box version | `"1.0.0"` |
| `config.vm.box_architecture` | Explicitly request the arm64 architecture | `"arm64"` |
| `config.vm.hostname` | Hostname assigned to the guest | `"dev-fedora"` |

## VirtualBox Provider Options

| Option | Description | Default (as configured in this box) |
|---|---|---|
| `vb.memory` | RAM allocated to the guest, in MB | `2048` |
| `vb.cpus` | Number of virtual CPUs | `2` |
| `vb.gui` | Whether to show the VirtualBox GUI on boot | `false` |

Example:

```ruby
config.vm.provider "virtualbox" do |vb|
  vb.memory = "4096"
  vb.cpus = 4
  vb.gui = false
end
```

## Networking Options

| Option | Description |
|---|---|
| `config.vm.network "forwarded_port", guest: X, host: Y` | Forward a guest port to the host |
| `config.vm.network "private_network", type: "dhcp"` | Add a host only private network |
| `config.vm.network "public_network"` | Bridge the guest to your local network |

> **Assumption:** These are standard Vagrant networking options. No project specific network configuration is published, since network setup is expected to be defined per project.

## Storage Notes

This box uses a VirtIO SCSI controller internally, which is required for reliable disk and optical media handling on ARM64 guests in VirtualBox. This is a build time detail of the box image itself and does not require any configuration from users of the box.

## Synced Folders

```ruby
config.vm.synced_folder "./local-path", "/vagrant/remote-path"
```

Default synced folder behavior follows standard Vagrant and VirtualBox conventions.

## Provisioning Options

Supported provisioners include, but are not limited to:

- `shell`
- `ansible`
- `ansible_local`
- `puppet`
- `chef_solo`

See the [official Vagrant provisioning documentation](https://developer.hashicorp.com/vagrant/docs/provisioning) for the full list and syntax.

## Full Vagrantfile Example

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "techgeek68/fedora44-arm64"
  config.vm.box_version = "1.0.0"
  config.vm.box_architecture = "arm64"
  config.vm.hostname = "dev-fedora-arm64"

  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.synced_folder "./app", "/vagrant/app"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
    vb.gui = false
  end

  config.vm.provision "shell", inline: <<-SHELL
    dnf update -y
  SHELL
end
```
