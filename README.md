# fedora44-arm64

[![Vagrant Cloud](https://img.shields.io/badge/Vagrant%20Cloud-techgeek68%2Ffedora44--arm64-blue)](https://portal.cloud.hashicorp.com/vagrant/discover/techgeek68/fedora44-arm64)
[![Provider](https://img.shields.io/badge/provider-VirtualBox-183a61)](https://www.virtualbox.org/)
[![Architecture](https://img.shields.io/badge/architecture-arm64-orange)](https://portal.cloud.hashicorp.com/vagrant/discover/techgeek68/fedora44-arm64)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

A minimal Fedora Server (aarch64) Vagrant base box, built for VirtualBox on ARM64 hosts such as Apple Silicon Macs.

> **Box:** `techgeek68/fedora44-arm64`
> **Vagrant Cloud:** https://portal.cloud.hashicorp.com/vagrant/discover/techgeek68/fedora44-arm64

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Supported Architecture and Platform](#supported-architecture-and-platform)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Usage Examples](#usage-examples)
- [Configuration Options](#configuration-options)
- [Directory Structure](#directory-structure)
- [Included Software](#included-software)
- [Networking Overview](#networking-overview)
- [Provisioning Overview](#provisioning-overview)
- [Updating the Box](#updating-the-box)
- [Versioning Strategy](#versioning-strategy)
- [Documentation](#documentation)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [Best Practices](#best-practices)
- [Limitations](#limitations)
- [Contributing](#contributing)
- [Security](#security)
- [Roadmap](#roadmap)
- [Credits and Acknowledgements](#credits-and-acknowledgements)
- [License](#license)

---

## Overview

This repository documents and supports `techgeek68/fedora44-arm64`, a Vagrant base box built from Fedora Server 44 for the `aarch64` architecture, packaged for the VirtualBox provider on ARM64 hosts.

The box is intended for developers who work on Apple Silicon Macs (or other ARM64 hosts) and need a lightweight, native ARM64 Linux environment for local development, testing, and experimentation, without relying on emulation.

> **Assumption:** This section is based on standard Vagrant and Fedora practices and should be updated if project specific details differ.

## Features

- Native ARM64 (`aarch64`) guest, no emulation overhead on Apple Silicon hosts
- Based on Fedora Server 44, a current Fedora release at time of publishing
- Minimal install footprint, no desktop environment
- Preconfigured for standard Vagrant workflows (SSH access, insecure key, NAT networking)
- VirtIO SCSI storage controller for reliable disk and media handling on ARM64 guests
- VirtualBox Guest Additions installed for improved host and guest integration

## Supported Architecture and Platform

| Component | Value |
|---|---|
| Guest architecture | arm64 (aarch64) |
| Guest operating system | Fedora Server 44 |
| Provider | VirtualBox |
| Minimum VirtualBox version | 7.1 or newer (ARM64 guest support required) |
| Minimum Vagrant version | 2.4.x or newer |
| Recommended host | Apple Silicon Mac (M1, M2, M3, M4, or later) |

> **Assumption:** Other ARM64 hosts capable of running VirtualBox 7.1 with ARM64 guest support may also work, but only Apple Silicon hosts have been documented here.

This box currently supports the VirtualBox provider only. It does not currently support other providers such as libvirt, QEMU, VMware, Parallels, or UTM. See [Limitations](#limitations) and [Roadmap](#roadmap).

## Prerequisites

Before using this box, install the following on your host machine:

- [VirtualBox](https://www.virtualbox.org/) 7.1 or newer, with ARM64 guest support
- [Vagrant](https://developer.hashicorp.com/vagrant) 2.4.x or newer
- A terminal application
- At least 4 GB of free RAM to allocate to the guest, and 40 GB of free disk space

## Installation

See [docs/installation.md](docs/installation.md) for full installation instructions.

Short version:

```
vagrant box add techgeek68/fedora44-arm64
```

## Quick Start

See [docs/quick-start.md](docs/quick-start.md) for a complete walkthrough.

```
mkdir my-fedora-arm64-project
cd my-fedora-arm64-project
vagrant init techgeek68/fedora44-arm64
vagrant up
vagrant ssh
```

## Usage Examples

See [docs/usage.md](docs/usage.md) for detailed examples, including custom memory and CPU allocation, shared folders, and provisioning.

## Configuration Options

See [docs/configuration.md](docs/configuration.md) for the full list of supported `Vagrantfile` options and provider specific settings.

## Directory Structure

This repository (the documentation and metadata repository, not the box image itself) is organized as follows:

```
.
├── README.md
├── SECURITY.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── CHANGELOG.md
├── LICENSE
├── docs
│   ├── installation.md
│   ├── quick-start.md
│   ├── usage.md
│   ├── configuration.md
│   ├── troubleshooting.md
│   └── faq.md
└── .github
    ├── ISSUE_TEMPLATE
    │   ├── bug_report.md
    │   ├── feature_request.md
    │   └── config.yml
    └── PULL_REQUEST_TEMPLATE.md
```

> **Assumption:** The Vagrant box binary itself is hosted and versioned on Vagrant Cloud, not in this repository. This repository documents the box, tracks changes, and accepts community feedback.

## Included Software

The box ships with a minimal Fedora Server 44 install, plus the packages required for Vagrant and VirtualBox integration.

| Category | Details |
|---|---|
| Base OS | Fedora Server 44 (aarch64) |
| Init system | systemd |
| Guest integration | VirtualBox Guest Additions (ARM64 build) |
| Default shell | bash |
| Package manager | dnf |

No desktop environment, container runtime, or language runtimes are preinstalled beyond what ships with a Fedora Server minimal install. Add any additional software you need through provisioning. See [Provisioning Overview](#provisioning-overview).

> **Assumption:** This reflects a standard Fedora Server minimal install. If custom packages were added during the build process, this section should be updated to list them explicitly.

## Networking Overview

- Default network adapter: NAT, provided automatically by Vagrant and VirtualBox
- SSH access: forwarded automatically by Vagrant, typically to a local port such as `2222`, mapped to guest port `22`
- No static IP addresses, internal hostnames, or private network details are published, since these are environment specific and should be configured per project

If you need host only or bridged networking for your project, configure it in your own `Vagrantfile`. See [docs/configuration.md](docs/configuration.md).

## Provisioning Overview

This box does not ship with a fixed, opinionated provisioning setup. It is intended as a clean base image. Add your own provisioning using any Vagrant supported provisioner, for example:

- Shell scripts
- Ansible
- Puppet
- Chef

Example shell provisioner in a `Vagrantfile`:

```ruby
config.vm.provision "shell", inline: <<-SHELL
  dnf update -y
SHELL
```

> **Assumption:** No project specific provisioning scripts are included in this repository, since publishing them could reveal internal implementation details. Users are expected to supply their own provisioning.

## Updating the Box

To update to the latest published version:

```
vagrant box update
```

To check your currently installed version against what is available:

```
vagrant box outdated
```

To remove an old version after updating:

```
vagrant box remove techgeek68/fedora44-arm64 --box-version OLD_VERSION
```

## Versioning Strategy

This box follows [Semantic Versioning](https://semver.org/) (`MAJOR.MINOR.PATCH`):

- **MAJOR**: incompatible changes, such as a new base OS version or breaking changes to defaults
- **MINOR**: backward compatible additions, such as new preinstalled packages or configuration improvements
- **PATCH**: backward compatible fixes, such as security updates or bug fixes with no behavior change

Current published version: `1.0.0`

See [CHANGELOG.md](CHANGELOG.md) for a full history of changes.

## Documentation

| Document | Description |
|---|---|
| [docs/installation.md](docs/installation.md) | How to install Vagrant, VirtualBox, and add this box |
| [docs/quick-start.md](docs/quick-start.md) | Get a VM running in a few minutes |
| [docs/usage.md](docs/usage.md) | Common usage patterns and examples |
| [docs/configuration.md](docs/configuration.md) | Supported `Vagrantfile` and provider options |
| [docs/troubleshooting.md](docs/troubleshooting.md) | Common errors and how to resolve them |
| [docs/faq.md](docs/faq.md) | Frequently asked questions |

## Troubleshooting

See [docs/troubleshooting.md](docs/troubleshooting.md) for a full list of common issues and fixes.

## FAQ

See [docs/faq.md](docs/faq.md).

## Best Practices

- Pin a specific box version in your `Vagrantfile` using `config.vm.box_version` for reproducible environments
- Always run `vagrant box update` before reporting an issue, to confirm you are on the latest version
- Keep provisioning logic in your own project repository rather than relying on box level customization
- Snapshot your VM (`vagrant snapshot save`) before making risky changes
- Destroy and recreate VMs periodically (`vagrant destroy && vagrant up`) to avoid drift from the published base image

## Limitations

- VirtualBox provider only. No official support for libvirt, QEMU, VMware, Parallels, or UTM at this time
- ARM64 (`aarch64`) guest only. Not compatible with x86_64 hosts or providers that do not support ARM64 guests
- Minimal install. No desktop environment or GUI tools are included
- Requires VirtualBox 7.1 or newer, since earlier versions do not support ARM64 guests

## Contributing

Contributions, issue reports, and suggestions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines, and please review the [Code of Conduct](CODE_OF_CONDUCT.md) before participating.

## Security

Please review [SECURITY.md](SECURITY.md) for how to report a vulnerability. Do not report security issues through public GitHub issues.

## Roadmap

Planned or potential future work, not guaranteed:

- [ ] Additional provider support (evaluation stage)
- [ ] Automated build pipeline documentation
- [ ] Optional provisioning profiles (for example, a Docker ready variant)
- [ ] Signed checksums published alongside each release

> **Assumption:** This roadmap reflects reasonable next steps for a project of this type and does not represent committed features.

## Credits and Acknowledgements

- Built on [Fedora Server](https://fedoraproject.org/server/), maintained by the Fedora Project and community
- Packaged with [HashiCorp Vagrant](https://developer.hashicorp.com/vagrant) and [Oracle VirtualBox](https://www.virtualbox.org/)
- Maintained by [techgeek68](https://portal.cloud.hashicorp.com/vagrant/discover/techgeek68)

## License

This documentation is released under the [MIT License](LICENSE). See the license file for details.

> **Assumption:** MIT is recommended as a permissive, widely understood license suitable for public documentation repositories. Update this if a different license applies to the underlying box image or repository content.
