# Installation

This guide covers installing the prerequisites and adding the `techgeek68/fedora44-arm64` box.

## 1. Install VirtualBox

Download VirtualBox 7.1 or newer for your platform from the [official VirtualBox downloads page](https://www.virtualbox.org/wiki/Downloads).

ARM64 guest support requires VirtualBox 7.1 or newer. Confirm your installed version:

```
VBoxManage --version
```

## 2. Install Vagrant

Download Vagrant from the [official Vagrant downloads page](https://developer.hashicorp.com/vagrant/downloads).

Confirm your installed version:

```
vagrant --version
```

Version 2.4.x or newer is recommended.

## 3. Add the Box

Add the box directly from Vagrant Cloud:

```
vagrant box add techgeek68/fedora44-arm64
```

You will be prompted to select a provider if more than one is detected. Choose `virtualbox`.

To add a specific version instead of the latest:

```
vagrant box add techgeek68/fedora44-arm64 --box-version 1.0.0
```

## 4. Verify the Box Was Added

```
vagrant box list
```

You should see `techgeek68/fedora44-arm64` in the output, along with its provider and version.

## Next Steps

Continue to the [Quick Start guide](quick-start.md) to bring up your first VM.
