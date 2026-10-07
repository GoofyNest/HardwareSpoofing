---
description: USB 3.2 Type-C Tool-Free Enclosure for M.2 PCIe NVMe and SATA SSDs
icon: usb
---

# Sabrent (EC-SVNE)

Going down the rabbit hole of finding a spoofable NVME controller can be very frustrating, even though it is the better option I will present you something that is working for now.

{% embed url="https://sabrent.com/products/ec-snve" %}

{% embed url="https://www.amazon.com/dp/B08RVC6F9Y" %}

Any USB -> NVME enclosure that has **Realtek RTL9210B** should work

{% embed url="https://github.com/bensuperpc/rtl9210" %}

***

So this device is around 30<mark style="color:green;">**$**</mark> and is currently fine for ban evading on EasyAntiCheat protected games.

However this does not mean it will always work, if you are looking for a long term solution you will need to find a spoofable NVME.

This enclosure is good enough for now and it supports any NVME.

***

We download tool from here:&#x20;

{% file src="../.gitbook/assets/UTHSB_MPtool_Lite_v1.15.8.0119_v1.35.6.rar" %}

If Windows does not find your Sabrent or RTL92010(A/B) then your Windows is preventing you, swap to another PC or reinstall windows and dont install any shady USB drives.

***

Inside **Configure** folder you will find a file called: **RTL9210B\_CG.cfg** open this and change your model, serial.

Recommend using this list:

{% embed url="https://www.techpowerup.com/ssd-specs/" %}

You can use this for serial numbers:

{% embed url="https://www.random.org/strings/?num=10&len=15&digits=on&upperalpha=on&unique=on&format=html&rnd=new" %}

***

So what are the downsides?

* Limited READ/WRITE, if using USB3.2 protocol you will get like 400/500 writes like a normal sata SSD.
* However if you use USB-C you can get 1000/1000 READ/WRITE.
* Harder to install Windows
* SMARTCTL exposing EEEE UID64 (as to my knowledge no anticheat using this query yet)

***

How do we install Windows to a USB Device? (Since USB is blocking it from the main GUI)

{% embed url="https://rufus.ie/en/" %}

{% embed url="https://www.youtube.com/watch?v=mRu4JRpubWI" %}

If you cannot find your Disk press **ALT + F** to list hard drives

Recommended to put:

&#x20;**VOLUME LABLE** to `Local Disk`

And remove the 2 files rufus creates inside the disk when completed (favoicon and the ini file)
