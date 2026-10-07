---
description: >-
  You must always reinstall windows per ban, there is no getting away from this
  step.
icon: window-restore
---

# Reinstall

### Operating system

{% hint style="warning" %}
You must have a working USB device minimum of 8GB of size
{% endhint %}

<mark style="background-color:$primary;">These ones are highly recommended to use</mark>

* [Windows 10](https://buzzheavier.com/fuxscqu93mnn) \
  Alternative here: [https://massgrave.dev/windows\_10\_links](https://massgrave.dev/windows_10_links)
* [Windows 11](https://zerofs.link/f/7ibXMho/)\
  Alternative here: [https://massgrave.dev/windows\_11\_links](https://massgrave.dev/windows_11_links)

{% hint style="danger" %}
We do no longer recommend the LTSC versions cause they come with the same Product ID
{% endhint %}

***

### Rufus

1. [Open the **Rufus** website](https://rufus.ie/).
2. Click the link to download the latest version under the “Download” section.
3. Double-click the **Rufus** executable file to launch the tool.
4. Select the flash drive to create a Windows 10/11 bootable USB drive in the “Device” section.
5.  Click the **Select** button.<br>

    <figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>
6. Select the **Windows 10/11 ISO** file.
7. Click **Start**
8.  Check the **“Remove requirement for 4GB+ RAM, Secure Boot and TPM 2.0”** option to install version 25H2 on unsupported hardware.\
    <br>

    <figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>
9.  Check the **“Remove requirement for an online Microsoft account”**<br>

    <figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>
10. Select the **“Create a local account with username”** option, then specify the account name to install the operating system with a local account.\
    `user`
11. Check the **“Set regional options to the same values as this user’s”** option to use the current language as the default for new installations.
12. Check the **“Disable data collection”** option to prevent Microsoft from collecting certain data.
13. Check the **“Disable BitLocker automatic device encryption”** option.
14. Click the **OK** button.

***

## NVRAM <mark style="color:$danger;">(Will Cause Issues)</mark>

**NVRAM (Non-Volatile Random-Access Memory)** is memory that can retain information even when the computer is powered off. On modern PCs, the term is commonly used for firmware-managed storage used by the UEFI/BIOS to preserve configuration and platform-specific information.

Unlike normal RAM, which loses its contents when power is removed, NVRAM is designed to retain its contents across reboots and power cycles.

Read more here: [efivars.md](../nvram-spoofing/efivars.md "mention")

***

### Installing Windows

1. Plug in your Windows USB you created
2. Restart PC
3. Hit your boot key\
   Normally F12 on Gigabyte\
   Normally F8 on ASUS, MSI
4.  Select the USB name partition 1<br>

    <figure><img src="../.gitbook/assets/{1B2BBC2E-EE78-4E60-95AF-8B8C299865DB} (1).png" alt=""><figcaption></figcaption></figure>


5.  Select your Windows language<br>

    <figure><img src="../.gitbook/assets/{5A523AD5-80DD-4E83-856A-CA1ED88E277D}.png" alt=""><figcaption></figcaption></figure>


6.  Select keyboard input<br>

    <figure><img src="../.gitbook/assets/{EC4CDE37-DEE4-48C7-8F95-50692BCA0BE4}.png" alt=""><figcaption></figcaption></figure>



1.  Click **I dont have product key**<br>

    <figure><img src="../.gitbook/assets/{BEA36942-60F2-456A-8877-CFE37A75017E}.png" alt=""><figcaption></figcaption></figure>


2.  Select first option<br>

    <figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>


3.  Agree to having no privacy<br>

    <figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>



***

### Removing partitions

Press delete on every partition until you only have 1 Disk, 1 Partition and the full disk size is available.

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

^ This is how its suppose to look if you did it correctly.

***

### Finishing up

1.  Install<br>

    <figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
When the text appears which says "Your PC is re-starting soon" un-plug your USB to avoid leaking banned USB disk serial on your freshly installed PC.
{% endhint %}

Enjoy fresh gaming!
