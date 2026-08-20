---
description: >-
  You must always reinstall windows per ban, there is no getting away from this
  step.
icon: '1'
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

## NVRAM #1 <mark style="color:$danger;">(Will Cause Issues)</mark>

**NVRAM (Non-Volatile Random-Access Memory)** is memory that can retain information even when the computer is powered off. On modern PCs, the term is commonly used for firmware-managed storage used by the UEFI/BIOS to preserve configuration and platform-specific information.

Unlike normal RAM, which loses its contents when power is removed, NVRAM is designed to retain its contents across reboots and power cycles.

#### The investigation

In my testing with EAC/Rust, leaving these variables intact consistently resulted in the previous device identity persisting across disk wipes, partition removal, and factory resets.

Windows create multiple keys in your NVRam, some of them are:

1. UnlockIDCopy
2. OfflineUniqueIDRandomSeed
3. OfflineUniqueIDRandomSeedCRC
4. OfflineUniqueIDEKPub (TPM related)
5. OfflineUniqueIDEKPubCRC (TPM related)
6. Boot0001-Boot0006

Not clearing them will result in OfflineUniqueIDRandomSeed & OfflineUniqueIDRandomSeedCRC containing unique information across factory resets, no matter if you destroy raid, format disks, remove partitions. It will stay in NVRam.

I have tested all known methods to flash NVRam and controlled the information with Linux and the 2 options you have is

* A) Bios downgrade, Bios upgrade
* B) Clearing the keys manually in Linux terminal

#### Potential ways to clearing NVRAM

It is very important that you do not boot into windows after clearing NVRAM, this should be done as the LAST step after you are completely spoofed.

<mark style="color:$danger;">If you remove the keys or flash bios and then boot into Windows afterwards you are compromised again.</mark>

**1. Flash back&#x20;**<mark style="color:blue;">**(Not guaranteed to work)**</mark>

Download the oldest possible version of your BIOS that <mark style="color:$danger;">supports</mark> your <mark style="color:$danger;">CPU</mark> if you are unsure just message an AI for help like ChatGPT your motherboard model, CPU model and ask what the oldest bios version is that supports this CPU.

<mark style="color:$danger;">(VERY IMPORTANT) to manually check so the AI is not lying.</mark>

Remember that after flashing BIOS that all your settings will go back to factory defaults leaving TPM enabled and other changes you might have done.

It is very important that you go over your settings and disable this:

* Disable onboard ethernet(not needed if you spoof onboard NIC)
* Disable BT/WIFI
* Disable TPM
* Disable Security Device
* Disable onboard sound card
* Disable onboard graphics (if ur cpu has it)
* Setup XMP and any overclocking if you have it
* Disable CSM
* Enable Secure boot
* Set Secure boot to custom
* Restore factory keys
* Restart pc

&#x20;**2. Creating Linux bootable USB**

_<mark style="color:pink;">**I do not recommend or condone messing with this, safest option is to flashback then manually verify that they keys are deleted in a Linux installation.**</mark>_

I will not share the detail of creating the USB, however I was using Ubuntu 22.04 LTS for these commands

List all the keys

```shellscript
ls /sys/firmware/efi/efivars/
```

Read the data (if you want to confirm my testing):

```shellscript
sudo xxd /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo xxd /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeedCRC-*
sudo xxd /sys/firmware/efi/efivars/UnlockIDCopy-*
sudo xxd /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo xxd /sys/firmware/efi/efivars/OfflineUniqueIDEKPubCRC-*
for f in /sys/firmware/efi/efivars/Boot000[1-6]-*; do
    echo "==== $f ===="
    sudo xxd "$f"
    echo
done
```

Remove the Linux immutable attribute (`i`)

```shellscript
sudo chattr -i /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo chattr -i /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeedCRC-*
sudo chattr -i /sys/firmware/efi/efivars/UnlockIDCopy-*
sudo chattr -i /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo chattr -i /sys/firmware/efi/efivars/OfflineUniqueIDEKPubCRC-*

for f in /sys/firmware/efi/efivars/Boot000[1-6]-*; do
    echo "==== $f ===="
    sudo chattr -i "$f"
    echo
done
```

Remove the keys

```shellscript
sudo rm /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo rm /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeedCRC-*
sudo rm /sys/firmware/efi/efivars/UnlockIDCopy-*
sudo rm /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo rm /sys/firmware/efi/efivars/OfflineUniqueIDEKPubCRC-*

for f in /sys/firmware/efi/efivars/Boot000[1-6]-*; do
    echo "==== $f ===="
    sudo rm "$f"
    echo
done
```

***

## NRAM #2 (<mark style="color:pink;">Potential issue</mark>)

Doing some more digging I found something very interesting in the boot order that saves to NVRam:

<figure><img src="../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

1. This is my USB devices that I had plugged in that have a bootloader
2. Example USB Flashdrives (what you using to reinstall windows)

This is not known to yet cause issues for **EasyAntiCheat - Rust** but its very bad if you do not clear this after installing Windows.

<mark style="color:violet;">I recommend flashing Bios another time after reinstalling windows just to ensure no other disk serial is leaking here.</mark>

***

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
