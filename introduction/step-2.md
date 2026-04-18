---
description: >-
  Build the perfect perm-spoofable setup and never have to pay for spoofing
  again, never get banned again due to spoofer faults.
icon: '2'
---

# Step #2

## CPU

This guide is mainly made for `AMD CPU` platforms, you can still use `Intel CPU` but with heavy limitations.

If you are using a <mark style="color:$danger;">`Intel CPU`</mark> platform and do not wish to upgrade to <mark style="color:$success;">`AMD CPU`</mark>, one option you have is to replace disk for each <mark style="color:$danger;">permanent ban</mark> or use a <mark style="color:$primary;">perm-spoofable disk</mark> from our [devices.md](../part-list/devices.md "mention").\
\
On AMD setups we are utilizing something called Raid and disk replacement is not necessary.

#### What is Raid?

RAID (Redundant Array of Independent Disks) is a storage technology that combines multiple physical disk drives into a single logical unit. It is often associated with data protection, but depending on the RAID level, it can also improve performance or both.

In this guide, we are using RAID 0 (or AMD RAIDXpert/RAIDABLE mode). RAID 0 does not provide redundancy or data protection. Instead, it focuses on performance by distributing data across multiple drives.

The reason for using RAID in this context is to abstract or mask certain disk details from software. Intel and AMD implement RAID differently. <mark style="color:$danger;">Intel RAID typically still exposes more underlying drive information</mark>, while <mark style="color:$success;">AMD RAID tends to hide more of the physical disk details from the operating system.</mark>

Another good part about AMD is that they have a <mark style="color:purple;">**RAIDABLE mode**</mark> which means that you do not need to have more then one disk to create an Raid array.

***

## Motherboard

Having the perfect motherboard is very important, our recommended boards are below:

1. Gigabyte (best option)
2. ASRock (second best)
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

Crosshair Vengeance is a ram manufacturer that has no unique serial numbers that anti-cheats can grab for both DDR4 and DDR5 platforms.

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

If you wanna build a fool-proof system go with **AMD GPU**

<mark style="color:$danger;">Also worth mentioning that disabling onboard graphics is requried for this guide to work.</mark>

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

If you see non unique serial number you are good to continue, otherwise you need to compromise by buying a **DMA Fuser** that supports custom EDID programming.

#### What is a DMA Fuser?

They are normally used to display ESP for DMA users on your main monitor, but some fusers have a hidden function and that is **programmable EDID**.

EDID is what monitors are reporting to your Graphic Card, inside the EDID there is a lot of information about your monitors such as Model, Serial number, Manufacturer etc.

The DMA Fuser sits in between your Graphic card and Monitor and can protect your monitor serial number from leaking to the Graphic card.

It is very important that if you have multiple monitors you need multiple Fusers or just buy monitors that do not have a serial number.

We have options in our [devices.md](../part-list/devices.md "mention") later in this documentation.

The cheapest fuser you can purchase is a `DICHEN 2k FUSER` which can be found in our [devices.md](../part-list/devices.md "mention") or from amazon or trusted resellers.

***

## Disk

For AMD setups any <mark style="color:$danger;">NVME SSD</mark> is suitable for Raid setup <mark style="color:$danger;">(for now).</mark> It's very important that you are using Raid on **NVME SSD** and not normal **SATA drives.**

For **Intel setup** you can use this guide: <mark style="color:purple;">**(NOT TESTED) (NOT RECOMMENDED) (BAD REVIEWS)**</mark>\
[https://github.com/dom0ng/map1202/blob/main/map1202.pdf](https://github.com/dom0ng/map1202/blob/main/map1202.pdf)

The size of the **NVME SSD** does not matter, just that they are using the **Maxio MAP1202 controller**.

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

We have a lot of different perhipials in our [devices.md](../part-list/devices.md "mention"), all of them have no serial numbers.

