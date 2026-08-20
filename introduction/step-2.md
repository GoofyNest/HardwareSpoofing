---
description: >-
  Build the perfect perm-spoofable setup and never have to pay for spoofing
  again, never get banned again due to spoofer faults.
icon: '2'
---

# Step #2

## NVRAM <mark style="color:$danger;">(Will Cause Issues)</mark>

**NVRAM (Non-Volatile Random-Access Memory)** is memory that can retain information even when the computer is powered off. On modern PCs, the term is commonly used for firmware-managed storage used by the UEFI/BIOS to preserve configuration and platform-specific information.

Unlike normal RAM, which loses its contents when power is removed, NVRAM is designed to retain its contents across reboots and power cycles.

#### The investigation

In my testing with EAC/Rust, leaving these variables intact consistently resulted in the previous device identity persisting across disk wipes, partition removal, and factory resets.

Windows create multiple keys in your NVRam, some of them are:

1. UnlockIDCopy
2. OfflineUniqueIDRandomSeed
3. OfflineUniqueIDRandomSeedCRC

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
```

Remove the Linux immutable attribute (`i`)

```shellscript
sudo chattr -i /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo chattr -i /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeedCRC-*
sudo chattr -i /sys/firmware/efi/efivars/UnlockIDCopy-*
```

Remove the keys

```shellscript
sudo rm /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo rm /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeedCRC-*
sudo rm /sys/firmware/efi/efivars/UnlockIDCopy-*
```

***

## CPU (<mark style="color:$danger;">updated 2026-08-20</mark>)

Intel raid 0 has never worked for EasyAntiCheat - Rust, you can obtain disk serials very low level from tools like HWInfo.

AMD raid 0 is no longer working for EasyAntiCheat - Rust, EasyAntiCheat obtains your disk serials anyways.

Anyone claiming otherwise is all lying.

> Raid 0 itself is not DETECTED or banned, its the fact EasyAntiCheat can read your phyiscal disk serials through the raid array.\
> \
> Meaning if your disks never been banned you can still use RAID 0 / RAIDABLE but it will have no affect in ban evading the anticheats anymore.\
> \
> And just because you can use it and play currently doesn't mean that you are fine or wont be banned at a later date.

This was bound to happen sooner or later, right now if you want to ban evade you will have to have a perm-spoofable disk or a new ssd/nvme per ban.

We will be testing way of spoofing disks in a few days and keep you guys updated.

***

## Motherboard

Having the perfect motherboard is very important, our recommended boards are below:

1. Gigabyte (Awesome for AM4, bad for AM5)
2. ASRock (Reliable on AM4 and AM5)
3. MSI (not ideal, but might work)
4. <mark style="color:red;">ASUS (Not recommended at all)</mark>

#### Why is ASUS not recommended?

ASUS Bios revisions after 2022 (general rule) is not perm-spoofable. They do not allow runtime writes to SMBIOS/DMI.\
\
The only option you have if you bought a ASUS motherboard is to use the oldest possible BIOS version and then try to write changes to SMBIOS/DMI.\
\
However very important that you verify that the serial numbers does not rollback after computer restart.\
\
If downgrading BIOS version is working for you, then you can safely update later when the spoofing is completed.

#### Motherboard requirements <mark style="color:$danger;">(very important)</mark>

Please ensure that the motherboard you have or going to purchase have the following:

* TPM-SPI header (or any TPM header)
* Raid support for NVME SSD

#### What is TPM header?

TPM stands for Trusted Platform Module. It is a hardware-based security feature used to store cryptographic keys and protect sensitive data.

Many motherboards include a **TPM header**, which is a physical connector used to install a separate, discrete TPM module.

A discrete TPM module performs the same function as firmware TPM but exists as a dedicated hardware chip connected directly to the motherboard. These are typically used in systems where additional hardware-based security is preferred.

This guide is utilizing the discrete TPM module on motherboards to bypass **TPM bans/restrictions**

***

## Ram

Corsair Vengeance new generation DDR5 have serial numbers now, so its a gamble if you get ram without serial numbers.

If your ram has serial numbers you can check this guide: [https://goofynest.gitbook.io/spoof/ram-spoofing/spd-security-editor](https://goofynest.gitbook.io/spoof/ram-spoofing/spd-security-editor)

There might be other manufacturers that have null serials, you can verify by running this query in PowerShell:

```powershell
Get-CimInstance Win32_PhysicalMemory | Select-Object Manufacturer, PartNumber, SerialNumber
```

If `SerialNumber` is non unique looking you might be good to continue.

Examples of non unique serials:

```
00000000
```

Also worth mentioning even if your Ram has null serial numbers they might not have null `Asset Tag`

`Asset Tag` can be found by dumping ram kernel level, but can also be retrieved using `AMIDEWINx64` or even simpler in the `DMI_EDIT` UI editor.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

***

## GPU (Video controller)

We recommend having AMD GPU before NVIDIA, due to NVIDIA cards have serial-numbers that anti-cheats can log and in the future ban.

If you want to build a fool-proof system go with **Gigabyte AMD GPU**

<mark style="color:$danger;">Also worth mentioning that disabling onboard graphics is required for this guide to work.</mark>

***

## Monitors

Your computer monitors also might have serial-numbers and anti-cheats do log them and ban them.

You can run this PowerShell script to verify if your monitor have serials:

```powershell
Get-CimInstance -Namespace root\wmi -ClassName WmiMonitorID | ForEach-Object {
    [PSCustomObject]@{
        Manufacturer = ($_.ManufacturerName -ne 0 | ForEach-Object {[char]$_}) -join ""
        Model        = ($_.UserFriendlyName -ne 0 | ForEach-Object {[char]$_}) -join ""
        SerialNumber = ($_.SerialNumberID -ne 0 | ForEach-Object {[char]$_}) -join ""
    }
}
```

If you see non unique serial number you are good to continue, otherwise you need to compromise by buying something to spoof your monitor serials.

I am personally using DMA Fuser

{% embed url="https://goofynest.gitbook.io/spoof/monitor-spoofing/dichen-5" %}

Other listings that might work:

{% embed url="https://goofynest.gitbook.io/spoof/monitor-spoofing/hdmi-edid-emulator-adapter" %}

{% embed url="https://goofynest.gitbook.io/spoof/monitor-spoofing/dr-hdmi" %}

#### What is a DMA Fuser?

They are normally used to display ESP for DMA users on your main monitor, but some fusers have a hidden function and that is **programmable EDID**.

EDID is what monitors are reporting to your Graphic Card, inside the EDID there is a lot of information about your monitors such as Model, Serial number, Manufacturer etc.

The DMA Fuser sits in between your Graphic card and Monitor and can protect your monitor serial number from leaking to the Graphic card.

It is very important that if you have multiple monitors you need multiple Fusers or just buy monitors that do not have a serial number.

We have options in our [devices.md](../part-list/devices.md "mention") later in this documentation.

The cheapest fuser you can purchase is a `DICHEN 2k FUSER` which can be found in our [devices.md](../part-list/devices.md "mention") or from amazon or trusted resellers.

***

## Disk

Spoofing Disks is now a requirement, Raid 0, Raidable is no longer working for EasyAntiCheat - Rust

You can test this:

{% embed url="https://goofynest.gitbook.io/spoof/disk-spoofing/smi-sx2263xt" %}

Or this:

{% embed url="https://captaindma.com/product/privacy-drive-no-hwid-no-serial-number-drive-512g/" %}

We will be releasing another alternative soon but requires testing.

***

## TPM (Trusted Platform Module)

Most modern systems include TPM functionality built into the CPU or chipset, commonly referred to as firmware TPM (fTPM on AMD systems or PTT on Intel systems).

TPM chips include unique identifiers that make each one different. Instead of relying on a simple serial number, they use built-in cryptographic keys, such as the Endorsement Key, which is unique to each TPM.

These keys can be used by operating systems and trusted software to verify the authenticity of the TPM and ensure it has not been altered or tampered with.

More and more anti-cheats are now requiring or forcing people to turn on fTPM on their setups, this is an issue for you that is ban-evading or following this guide.

The only concrete solution for this is to use a discrete TPM chip, its a chip that must be replaced on bans.

They usually goes for around 10-20$ depending on your motherboard. You can find them on Amazon, Temu or sites like aliexpress.

We will have link in our [devices.md](../part-list/devices.md "mention").

***

## Network adapter (NIC)

Every device that is connected to the internet has a MAC address that anti-cheats grabs and ban or flag you for.

NIC is the chipset that is on your motherboard, most of them are spoofable but we will not provide a guide for it because it can destroy/brick your motherboard and also will void the warranty.

However we have a solution that is working and that is a USB Ethernet dongle that is perm-spoofable or you can just replace it per ban.

If you are using WiFi for gaming, then you can just buy a replacement WiFi chip for $9 to $11 usd

***

## USB Devices

Many daily USB devices have serial numbers, you can check if your setup has any unique serial numbers using a tool called [USB Deview](https://www.nirsoft.net/utils/usbdeview-x64.zip)

We recommend people to purchase Razer branded mice, they have no serials.

We have a lot of different peripheral in our [devices.md](../part-list/devices.md "mention"), all of them have no serial numbers.
