# Quick Start

This guide gets you from zero to a running Fedora ARM64 VM in a few minutes.

## 1. Create a Project Directory

```
mkdir my-fedora-arm64-project
```

```
cd my-fedora-arm64-project
```

## 2. Initialize the Vagrantfile

```
vagrant init techgeek68/fedora44-arm64
```

This creates a `Vagrantfile` in the current directory.

## 3. Pin a Version (Recommended)

Open the generated `Vagrantfile` and add a version pin for reproducibility:

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "techgeek68/fedora44-arm64"
  config.vm.box_version = "1.0.0"
end
```

## 4. Bring Up the VM

```
vagrant up
```

The first run will download the box if it is not already present locally, then boot the VM.

## 5. Connect to the VM

```
vagrant ssh
```

You should now have a shell inside the Fedora Server 44 ARM64 guest.

## 6. Confirm the Architecture

```
uname -m
```

This should print `aarch64`.

## 7. Shut Down or Remove the VM

To stop the VM without deleting it:

```
vagrant halt
```

To remove the VM entirely:

```
vagrant destroy
```

## Next Steps

- See [Usage Examples](usage.md) for common configuration patterns.
- See [Configuration Options](configuration.md) for the full list of supported `Vagrantfile` settings.
