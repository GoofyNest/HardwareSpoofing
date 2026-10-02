---
description: >-
  Build the perfect perm-spoofable setup and never have to pay for spoofing
  again, never get banned again due to spoofer faults.
icon: '2'
---

# Important information

## NVRAM #1 <mark style="color:$danger;">(Will Cause Issues)</mark>

**NVRAM (Non-Volatile Random-Access Memory)** is memory that can retain information even when the computer is powered off. On modern PCs, the term is commonly used for firmware-managed storage used by the UEFI/BIOS to preserve configuration and platform-specific information.

Unlike normal RAM, which loses its contents when power is removed, NVRAM is designed to retain its contents across reboots and power cycles.

#### The investigation

In my testing with EAC/Rust, leaving these variables intact consistently resulted in the previous device identity persisting across disk wipes, partition removal, and factory resets.

**Windows create multiple keys in your NVRam, some of them are:**

1. UnlockIDCopy
2. OfflineUniqueIDRandomSeed
3. OfflineUniqueIDRandomSeedCRC
4. OfflineUniqueIDEKPub (TPM related)
5. OfflineUniqueIDEKPubCRC (TPM related)

**Bios generated vars:**

1. DmiVar\*-\*
2. MacAddrVar-\*
3. Boot0001-Boot0006

Not clearing them will result in OfflineUniqueIDRandomSeed & OfflineUniqueIDRandomSeedCRC containing unique information across factory resets, no matter if you destroy raid, format disks, remove partitions. It will stay in NVRam.

***

### NVRAM (Windows)

Requirements

{% embed url="https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/" %}

* Secure boot (Temporairly disabled)
* cmd.exe as Admin ⇒ bcdedit /set TESTSIGNING ON
* Restart PC

Use our app:

{% file src="../.gitbook/assets/HardwareReport.rar" %}

Archieve password is `1`

***

### NVRAM (Linux)

{% stepper %}
{% step %}
### Correct steps are:

* Make sure the system is fully prepared for the new installation.
* Disconnect any storage devices that should not be involved.
* Flash bios
* Clear NVRAM
* Proceed directly with the clean installation.
{% endstep %}

{% step %}
### Step 1: Unplug External Storage and Remove Windows

> **Important:** Before clearing NVRAM, disconnect all storage devices that will not be used for the new installation.

Unplug or physically disconnect:

* USB flash drives
* External hard drives
* SATA SSDs/HDDs
* Additional NVMe drives
* Any other removable storage devices
{% endstep %}

{% step %}
### Step 2: Flashing BIOS

Download the **oldest BIOS version that supports your CPU**.

If you are unsure which version you need, you can ask an AI such as ChatGPT by providing your **motherboard model and CPU model** and asking which BIOS version is the oldest that supports your CPU.

> **VERY IMPORTANT:** Always verify the information yourself using your motherboard manufacturer's official BIOS/CPU compatibility documentation. Do not rely solely on AI-generated information.

After flashing the BIOS, your BIOS settings will be reset to their **factory defaults**. This means settings such as TPM, Secure Boot, CSM, XMP, and other options may be changed from their previous configuration.

It is therefore important to go through your BIOS settings again and configure the following:

* Disable onboard Ethernet _(not required if you are spoofing the onboard NIC)_
* Disable Bluetooth/Wi-Fi
* Disable TPM
* Disable Security Device
* Disable onboard audio
* Disable onboard graphics _(if your CPU has integrated graphics)_
* Enable XMP and configure any desired overclocking settings
* Disable CSM
* Enable Secure Boot
* Set Secure Boot mode to **Custom**
* Restore the factory Secure Boot keys
* Save your changes and restart the PC
{% endstep %}

{% step %}
### Step 3: **Creating Linux bootable USB**

I will not share the detail of creating the USB, however I was using Ubuntu 22.04 LTS for these commands
{% endstep %}

{% step %}
### Step 4: Removing Windows / Partitions

[reinstall.md](../windows/reinstall.md "mention")

* Pick a windows from the guide
* Create the USB (If using NVME enclosure follow this: [sabrent-ec-svne.md](../disk-spoofing/sabrent-ec-svne.md "mention")
* Follow **#Removing partitions** (If using NVME enclosure follow this: [sabrent-ec-svne.md](../disk-spoofing/sabrent-ec-svne.md "mention")
{% endstep %}

{% step %}
### Step 5: Clearing NVRam

> **IMPORTANT:** Do **not** boot into Windows after clearing NVRAM.\
> \
> Clearing NVRAM should be performed as the **final step**, after you have completed all other required changes.
>
> If you remove EFI variables or make BIOS changes and then boot into Windows afterward, Windows or the firmware may recreate or modify certain configuration data.



**1. Boot into Linux**

Plug in the Linux USB you created earlier and boot the PC from it.

Become root:

```shellscript
sudo su
```

**2. List the EFI variables**

```shellscript
ls /sys/firmware/efi/efivars/
```

**3. Read the variables**

If you want to inspect the variables before making any changes, you can use:

```shellscript
sudo xxd /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo xxd /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeedCRC-*
sudo xxd /sys/firmware/efi/efivars/UnlockIDCopy-*
sudo xxd /sys/firmware/efi/efivars/OfflineUniqueIDEKPubCRC-*
sudo xxd /sys/firmware/efi/efivars/MacAddrVar-*
```

To inspect the relevant `Boot` variables:

```shellscript
for f in /sys/firmware/efi/efivars/Boot000[1-6]-*; do
    echo "==== $f ===="
    sudo xxd "$f"
    echo
done
```

To inspect the `DmiVar` variables:

```shellscript
for f in /sys/firmware/efi/efivars/DmiVar-*; do
    echo "==== $f ===="
    sudo xxd "$f"
    echo
done
```

**4. Remove the Linux immutable attribute**

Some EFI variables may have the Linux immutable (`i`) attribute set. Remove it before attempting to delete the variables:

```shellscript
sudo chattr -i /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo chattr -i /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeedCRC-*
sudo chattr -i /sys/firmware/efi/efivars/UnlockIDCopy-*
sudo chattr -i /sys/firmware/efi/efivars/OfflineUniqueIDEKPubCRC-*
sudo chattr -i /sys/firmware/efi/efivars/MacAddrVar-*
```

For the `Boot` variables:

```shellscript
for f in /sys/firmware/efi/efivars/Boot000[1-6]-*; do
    echo "==== $f ===="
    sudo chattr -i "$f"
    echo
done
```

For the `DmiVar` variables:

```shellscript
for f in /sys/firmware/efi/efivars/DmiVar-*; do
    echo "==== $f ===="
    sudo chattr -i "$f"
    echo "done"
done
```

**5. Remove the selected EFI variables**

```shellscript
sudo rm /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeed-*
sudo rm /sys/firmware/efi/efivars/OfflineUniqueIDRandomSeedCRC-*
sudo rm /sys/firmware/efi/efivars/UnlockIDCopy-*
sudo rm /sys/firmware/efi/efivars/OfflineUniqueIDEKPubCRC-*
sudo rm /sys/firmware/efi/efivars/MacAddrVar-*
```

Remove the selected `Boot` variables:

```shellscript
for f in /sys/firmware/efi/efivars/Boot000[1-6]-*; do
    echo "==== $f ===="
    sudo rm "$f"
    echo
done
```

Remove the selected `DmiVar` variables:

```shellscript
for f in /sys/firmware/efi/efivars/DmiVar-*; do
    echo "==== $f ===="
    sudo rm "$f"
    echo "done"
done
```

> **WARNING:** EFI variables are firmware configuration data. Deleting the wrong variables can affect boot configuration or other firmware functionality. Only remove variables that you have verified are safe to remove for your specific motherboard/firmware.

**6. Shut down the PC**

When you are finished, disconnect all removable storage:

* **Unplug all USB flash drives**, including the Linux USB.
* **Disconnect any storage devices that should not be present during the installation.**

Then shut down the system:

```shellscript
shutdown -h now
```
{% endstep %}

{% step %}
### Final step

Do **not** boot back into Windows at this point.

Only power the PC back on when you are ready to proceed with the intended installation.

> **Do not flash the BIOS again after clearing the EFI variables**, unless you have a specific reason to do so. A BIOS flash can reset or recreate firmware variables and therefore changes the state you just configured.
{% endstep %}
{% endstepper %}

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

If your ram has serial numbers you can check this guide:&#x20;

{% embed url="https://goofynest.gitbook.io/spoof/ram-spoofing/spd-security-editor" %}

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

Very cheap and reliable (works for now) (support any nvme)

{% embed url="https://goofynest.gitbook.io/spoof/disk-spoofing/sabrent-ec-svne" %}

You can test this:

{% embed url="https://goofynest.gitbook.io/spoof/disk-spoofing/smi-sx2263xt" %}

Or this:

{% embed url="https://captaindma.com/product/privacy-drive-no-hwid-no-serial-number-drive-512g/" %}

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
