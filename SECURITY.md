# Security Policy

## Supported Versions

Security fixes are provided for the most recently published version of this box. Older versions are not patched retroactively. Users are strongly encouraged to run:

```
vagrant box update
```

before assuming a security issue affects the current release.

| Version | Supported |
|---|---|
| Latest (`1.0.0` and newer) | Yes |
| Older versions | No |

## Reporting a Vulnerability

If you discover a security vulnerability in this box, its documentation, or its publicly available build process, please report it privately rather than opening a public issue.

**Do not report security vulnerabilities through public GitHub issues, discussions, or pull requests.**

To report a vulnerability, please use one of the following:

- Open a [GitHub Security Advisory](../../security/advisories/new) on this repository, if enabled
- Contact the maintainer through the contact method listed on the [Vagrant Cloud profile](https://portal.cloud.hashicorp.com/vagrant/discover/techgeek68)

Please include as much of the following as possible:

- A description of the vulnerability and its potential impact
- Steps to reproduce the issue
- The box version affected
- Your VirtualBox and Vagrant versions
- Any relevant logs, with sensitive information removed

## What Happens Next

- We aim to acknowledge reports within a reasonable timeframe.
- Once a report is confirmed, a fix will be prepared and published as a new box version.
- Credit will be given to the reporter in the [Changelog](CHANGELOG.md), unless anonymity is requested.

## Scope

This policy covers:

- The Vagrant box image itself (`techgeek68/fedora44-arm64`)
- This documentation repository
- Any scripts published in this repository

This policy does not cover:

- Third party software installed by end users after provisioning
- Custom `Vagrantfile` configurations written by end users
- Issues in upstream projects such as Fedora, Vagrant, or VirtualBox. Please report those directly to the relevant upstream project.

## Disclosure Policy

We follow a coordinated disclosure approach. Please allow time for a fix to be published before publicly disclosing details of a vulnerability.
