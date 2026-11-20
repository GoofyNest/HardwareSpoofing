---
description: USB 3.2 Type-C Tool-Free Enclosure for M.2 PCIe NVMe and SATA SSDs
icon: usb
---

# USB => NVME (SWAG ENCLOSURE)

## Undetected

Reverse engineering the firmware and making our own to fully support SMART, blocking all requests.

{% embed url="https://github.com/GoofyNest/RTL9210B-SMARTCTL" %}

_Have fun patching this, L bozo's_

***

{% embed url="https://www.amazon.com/dp/B083XWBR2V" %}

{% file src="../.gitbook/assets/GoofyNest ELUTENG.rar" %}

OR

{% embed url="https://www.amazon.com/dp/B08RVC6F9Y" %}

{% file src="../.gitbook/assets/GoofyNest Sabrent.rar" %}

Any USB -> NVME enclosure that has **Realtek RTL9210B** should work

{% embed url="https://github.com/GoofyNest/RTL9210B-SMARTCTL" %}

{% embed url="https://github.com/bensuperpc/rtl9210" %}

***

So what are the downsides?

* Limited READ/WRITE, if using USB3.2 protocol you will get like 400/500 writes like a normal sata SSD.
* However if you use USB-C you can get 1000/1000 READ/WRITE.
* Harder to install Windows

***

How do we install Windows to a USB Device? (Since USB is blocking it from the main GUI)

{% embed url="https://rufus.ie/en/" %}

{% embed url="https://www.youtube.com/watch?v=mRu4JRpubWI" %}

If you cannot find your Disk press **ALT + F** to list hard drives

Recommended to put:

**VOLUME LABLE** to `Local Disk`

And remove the 2 files rufus creates inside the disk when completed (favoicon and the ini file)
