# Troubleshooting

Common issues encountered when using `techgeek68/fedora44-arm64`, and how to resolve them.

## The box will not download

**Symptom:** `vagrant up` or `vagrant box add` fails to fetch the box.

**Fix:**
- Confirm you have internet access and that Vagrant Cloud is reachable.
- Confirm the box name and version are correct:
  ```
  vagrant box add techgeek68/fedora44-arm64 --box-version 1.0.0
  ```

## Box provider not found

**Symptom:** Vagrant reports that no matching provider was found for your host.

**Fix:** Confirm you are using VirtualBox, and that it is version 7.1 or newer with ARM64 guest support:
```
VBoxManage --version
```

## VM fails to boot or hangs at startup

**Fix:**
- Confirm your host has ARM64 guest support enabled in VirtualBox 7.1 or newer.
- Confirm you have enough free RAM and disk space on the host.
- Try increasing allocated memory in your `Vagrantfile`:
  ```ruby
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  ```

## SSH connection times out

**Symptom:** `vagrant up` hangs at "Waiting for machine to boot" or `vagrant ssh` fails to connect.

**Fix:**
- Give the VM more time to boot on the first run, since first boot can take longer than subsequent boots.
- Confirm no other process on the host is using the forwarded SSH port.
- Try:
  ```
  vagrant reload
  ```

## Architecture mismatch

**Symptom:** Errors referencing architecture, or the guest reports the wrong architecture.

**Fix:** Confirm your `Vagrantfile` explicitly requests the arm64 architecture:
```ruby
config.vm.box_architecture = "arm64"
```

Verify inside the guest:
```
uname -m
```
This should print `aarch64`.

## Outdated box causing unexpected behavior

**Fix:** Update to the latest published version:
```
vagrant box update
```
Then destroy and recreate the VM:
```
vagrant destroy
```
```
vagrant up
```

## Still Stuck

If none of the above resolves your issue:

1. Check the [FAQ](faq.md).
2. Search [existing issues](../../issues) in this repository.
3. Open a new issue using the [bug report template](../.github/ISSUE_TEMPLATE/bug_report.md), including your host OS, VirtualBox version, Vagrant version, and box version.

> **Assumption:** These troubleshooting steps reflect general Vagrant, VirtualBox, and Fedora ARM64 guest behavior, and should be updated with project specific findings as they are reported.
