---
description: Welcome to your team’s developer platform
layout:
  width: wide
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Welcome

## GoofyNest

**Hardware research, technical guides and community documentation.**

Built from frustration. Refined through research.

GoofyNest documents hardware identifiers, firmware behavior, system configuration and hands-on experiments. Explore a topic below, review the prerequisites and understand the risks before making changes.

{% hint style="warning" %}
**Before you begin:** Firmware, EEPROM and hardware modifications can cause data loss or permanently damage devices. Back up important data, document your original settings and confirm a recovery method before attempting changes. Results depend on your specific hardware and firmware.
{% endhint %}

### Start here

* Basics & terminology
* Important information
* Device restrictions
* Hardware and tools

### Motherboards & SMBIOS

* SMBIOS manager
* ASUS motherboards
* CH341A programmer

### Firmware & TPM

* UEFI variables
* Firmware TPM

### Storage

* Sabrent enclosure
* SMI controller
* KingSpec SSD

### Networking

* Realtek NICs
* Intel NICs
* Raspberry Pi 4

### Memory, displays & Windows

* SPD Security Editor
* Monitor tools
* EDID hardware
* Windows installation

### Research notes

{% hint style="info" %}
**How to read the guides:** Documented observations are not universal guarantees. Hardware revisions, firmware versions and operating system builds may change behavior. A successful test does not establish that a configuration is undetectable.
{% endhint %}

The original documentation grew from personal experiences in the Rust and anti-cheat communities, where conflicting advice and unreliable claims made it difficult to understand what hardware tools actually changed. This project aims to make those technical details easier to find, evaluate and discuss.

### Community & source

**GitHub repository**

{% embed url="https://github.com/GoofyNest/HardwareSpoofing" %}

**Discord community**

{% embed url="https://discord.com/invite/JtU8FxQnN5" %}

**Published documentation**

{% embed url="https://goofynest.gitbook.io/spoof" %}

### Credits

Thanks to everyone contributing research, testing and documentation, including **@exclusi0n**, [**@slate\_hub**](https://slatehub.io/), **@awong0**, and **Sauce Machine** for publishing AMIDEWINx64 binaries.

***

If these resources have been helpful, you can support GoofyNest below. Support is entirely optional and the documentation remains freely accessible.

{% embed url="https://buymeacoffee.com/goofynest" %}
