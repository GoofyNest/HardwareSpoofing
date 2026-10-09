---
description: Reposted by @Fundryi/HWID-Privacy
icon: burst-new
---

# fTPM

{% hint style="danger" %}
Not tested personally by us.
{% endhint %}

{% embed url="https://github.com/cycript/FTPM_POC" %}

* **Concept** (more complicated, and may be more relevant on AMD):
  * [fTPM Spoof PoC by cycript](https://github.com/cycript/FTPM_POC)
* **Simpler Working Method**:
  * **Requirements**:
    * Intel platform
    * Motherboard with:
      * Dedicated USB Flash port
      * BIOS Flash Button
        * Tested: MSI Z790
        * Should work with all Intel boards since the 11th-generation release, when the EK went offline.

<figure><img src="../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

* **How it works**:
  * Check your motherboard manual for the exact flash procedure.
  * Place the BIOS file on the USB stick, then insert it into the designated flash USB port.
    * Each vendor has a different flash process; follow official documentation closely to avoid a bad flash.
  * Press the Flash Button and let it rewrite motherboard sectors.
  * This regenerates the fTPM seed
  * Results in a _new, unique fTPM serial_ signed by EK
* **Note: Doesn't work on AMD boards**
