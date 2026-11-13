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

## Welcome

### Hardware Spoofing

{% hint style="info" %}
Built from frustration. Refined through research.

The endless hunt for answers ends here.\
Built around research, transparency, and understanding your system.\
\
This guide covers advanced system concepts.\
Take your time, understand each step, and make informed decisions.
{% endhint %}

**Why this guide exists**

This guide started out of frustration within the EAC and Rust communities.

Like many others, I was a regular consumer who trusted recommendations, purchased popular hardware spoofers, and followed solutions advertised as "working."

Instead of finding clear answers, I found myself stuck in an endless cycle of testing different solutions and searching for something reliable.

Whenever problems occurred, the blame was often passed around. Spoofer developers blamed cheat developers, cheat developers blamed spoofers, and users were left trying to figure out what was actually happening.

This guide was created to break that cycle by documenting my personal experiences, combining them with research and findings shared by others in the community.

Over the years, permanent hardware-level spoofers have developed a complicated reputation. Users have reported incidents involving corrupted firmware, damaged hardware, and even claims of permanently disabled components due to e-fuse-related issues.

I have personally witnessed tools corrupting SMBIOS data, replacing legitimate manufacturer information with random characters and numbers, leaving systems with inconsistent or damaged hardware identification records.

Another issue is that many products advertised as **permanent spoofers** are not entirely permanent.

Some use what I call **hybrid solutions**, modifying identifiers that can be changed persistently while relying on additional software or drivers to modify or intercept the remaining identifiers at runtime.

This distinction is often overlooked when these products are advertised.

Our approach continues to evolve through research into hardware components, firmware configurations, and identifiers that can be modified persistently.

The goal is to understand which changes survive a complete Windows reinstallation, which require additional software, and how to achieve consistent hardware configurations without relying on unnecessary background drivers.

#### :point\_right: Find us here:

* Discord server [https://discord.com/invite/JtU8FxQnN5](https://discord.com/invite/JtU8FxQnN5)
* Github: [https://github.com/GoofyNest/HardwareSpoofing](https://github.com/GoofyNest/HardwareSpoofing)
* Gitbook: [https://goofynest.gitbook.io/spoof](https://goofynest.gitbook.io/spoof)

#### 🙌 Special thanks to

* Everyone who keep contributing to the documentation and all our supporters at **buymeacoffee**
* discord = **@exclusi0n** for helping with research
* discord = [**@slate\_hub**](https://slatehub.io/) for helping with research
* discord = **@awong0** for helping with research
* **Sauche Machine** for releasing binaries for AMIDEWINx64

{% hint style="success" icon="dollar-sign" %}
If our guides/tools/open research has helped you in any way, consider helping us back by donating

{% embed url="https://buymeacoffee.com/goofynest" %}

People whom donate will get a special role in our Discord server as a Thank you :heart:
{% endhint %}

***

{% hint style="info" icon="gamepad-modern" %}
Supported Anti Cheats
{% endhint %}

Most anti-cheats that does not force fTPM(**CPU**)

| AntiCheat     | Status     | Last issue                | Requirements             |
| ------------- | ---------- | ------------------------- | ------------------------ |
| EasyAntiCheat | 🟢 Working | — 8/16/26 (RAID 0, NVRAM) | dTPM, Secure boot, IOMMU |
| BattlEye      | 🟢 Working |                           |                          |
| EA Javeline   | 🟢 Working |                           | dTPM, Secure boot        |
| Tencent ACE   | 🟢 Working |                           | dTPM, Secure boot, IOMMU |

{% hint style="info" icon="microchip" %}
Supported CPU (CPU no longer matters)
{% endhint %}

<table data-view="cards"><thead><tr><th></th><th data-type="rating" data-max="5"></th><th></th><th></th><th></th><th data-hidden data-card-cover data-type="image">Cover image</th></tr></thead><tbody><tr><td>AMD</td><td>5</td><td></td><td></td><td></td><td data-object-fit="fill"><a href=".gitbook/assets/amd-logo-ruby-red.webp">amd-logo-ruby-red.webp</a></td></tr><tr><td>Intel</td><td>5</td><td></td><td></td><td></td><td data-object-fit="fill"><a href=".gitbook/assets/Intel_logo_(2006-2020).svg.png">Intel_logo_(2006-2020).svg.png</a></td></tr></tbody></table>

{% hint style="info" icon="desktop" %}
Supported Motherboards
{% endhint %}

<table data-view="cards"><thead><tr><th></th><th data-type="rating" data-max="5"></th><th></th><th data-hidden data-card-cover data-type="image">Cover image</th></tr></thead><tbody><tr><td>Gigabyte</td><td>4</td><td>Reliable</td><td><a href=".gitbook/assets/gigabyte-logo.png">gigabyte-logo.png</a></td></tr><tr><td>MSI</td><td>4</td><td>Reliable</td><td><a href=".gitbook/assets/MSI-Logo.png">MSI-Logo.png</a></td></tr><tr><td>ASRock</td><td>3</td><td>Reliable</td><td><a href=".gitbook/assets/asrock.png">asrock.png</a></td></tr><tr><td>ASUS</td><td>1</td><td>Very limited support</td><td><a href=".gitbook/assets/asus-logo.webp">asus-logo.webp</a></td></tr></tbody></table>

{% hint style="info" icon="memory" %}
Supported Ram
{% endhint %}

<table data-view="cards"><thead><tr><th></th><th data-type="rating" data-max="5"></th><th></th><th data-hidden data-card-cover data-type="image">Cover image</th></tr></thead><tbody><tr><td>Most ram</td><td>4</td><td>G.SKILL memory modules not supported, confirmed E-WASTE</td><td data-object-fit="contain"><a href=".gitbook/assets/image (56).png">image (56).png</a></td></tr></tbody></table>

{% hint style="info" icon="windows" %}
Supported operating systems

This guide focuses on hardware identification, hardware-level modifications, and how these technologies interact with kernel-level anti-cheat systems on Windows. Many of the documented techniques also apply to Linux, although hardware identification and anti-cheat implementations differ between operating systems.
{% endhint %}

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="image">Cover image</th></tr></thead><tbody><tr><td>Windows 7</td><td>All versions</td><td data-object-fit="contain"><a href=".gitbook/assets/windows-7-use.png">windows-7-use.png</a></td></tr><tr><td>Windows 10</td><td>All versions</td><td data-object-fit="contain"><a href=".gitbook/assets/win-10.webp">win-10.webp</a></td></tr><tr><td>Windows 11</td><td>All versions</td><td data-object-fit="contain"><a href=".gitbook/assets/win-11.jpg">win-11.jpg</a></td></tr></tbody></table>
