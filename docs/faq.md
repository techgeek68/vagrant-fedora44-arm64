# Frequently Asked Questions

### What is this box for?

`techgeek68/fedora44-arm64` provides a native ARM64 Fedora Server 44 environment for local development and testing on ARM64 hosts, primarily Apple Silicon Macs, using VirtualBox.

### Why Fedora Server instead of a desktop edition?

Fedora Server provides a minimal footprint, which keeps the box small, fast to boot, and easy to customize through provisioning rather than shipping with unnecessary preinstalled software.

### Does this box work on Intel or AMD (x86_64) machines?

No. This box is built specifically for the `aarch64` (ARM64) architecture and is intended to run natively on ARM64 hosts. It is not intended for x86_64 hosts.

### Does this box support providers other than VirtualBox?

Not currently. See [Limitations](../README.md#limitations) and [Roadmap](../README.md#roadmap) in the main README.

### What is the default username and authentication method?

Vagrant boxes conventionally use a `vagrant` user with SSH key based authentication using Vagrant's publicly documented insecure keypair, replaced automatically with a secure, randomly generated key on first `vagrant up`. This is standard Vagrant behavior and not specific configuration disclosed by this project.

> **Assumption:** This reflects standard Vagrant box conventions. No project specific credentials are published or should ever be requested.

### How much RAM and disk space does the VM need?

At minimum, allocate 2 GB of RAM and ensure at least 40 GB of free disk space on the host for the virtual disk. See [Configuration Options](configuration.md) for how to adjust resource allocation.

### How do I update to a newer version of the box?

```
vagrant box update
```

See [Updating the Box](../README.md#updating-the-box) in the main README for full details.

### Can I use this box in a CI pipeline?

This has not been officially tested or documented. If you use it in CI, please consider opening an issue or pull request to share your findings.

### Where do I report bugs or request features?

Open an issue in this repository using the appropriate [issue template](../.github/ISSUE_TEMPLATE).

### Where do I report a security vulnerability?

Do not open a public issue. See [SECURITY.md](../SECURITY.md) for the correct reporting process.

### Is this an official Fedora or HashiCorp project?

No. This is an independently maintained community box, built using Fedora Server and distributed through HashiCorp's Vagrant Cloud. It is not officially affiliated with, endorsed by, or maintained by the Fedora Project or HashiCorp.
