# 🛡️ Ban Evading the AntiCheat
**Safely bypass all the AntiCheats below, never need to pay someone for spoofing your serials again**
- BattleEye
- Ricochet
- Easy Anti Cheat
- Ace Anti Cheat
- Chinese-Ace

This is the most reliable approach with minimal to zero detection flags if done correctly.

## 🙌 Credits
- Jakb aka Jacob White (Swivelly Boy, Chad Purifier, Slithery Boy)
- Reported.lol dev for releasing this version of AMIDEWINx64

> [!WARNING]
> If you get banned using this method, it's most likely because:
> 1. You're doing it wrong
> 2. You're using a detected cheat
>
> You cannot be banned by only using this spoofing method.

### ✅ Supported Motherboards
- ASUS
- Gigabyte
- ASRock
- MSI

> [!WARNING]
> If your motherboard isn't listed, it's likely not supported.

### 📋 Requirements

- RAID 0 or fresh disk per ban
- WiFi / Bluetooth disabled in BIOS, or physically removed from the motherboard
- TPM disabled in BIOS
- RAM with null serials (00000) — e.g., `Corsair Vengeance`
- Onboard LAN adapter disabled in BIOS
- USB Ethernet Adapter (for MAC spoofing)
🔹 Recommended: TP-Link UE300 (~$9)
- Windows 10 for Monitor spoofing

  
### 🧩 What Is RAID 0 (and Why It Matters for Spoofing)?

**RAID 0** is a storage setup that combines two or more drives into a single "virtual" drive using a method called striping. While it’s traditionally used for performance, in ban evasion, the goal is different:

> [!TIP]
> RAID 0 is used to completely change the hardware signature of your drive(s).

Most games that use anti-cheats like EasyAntiCheat (EAC) or BattlEye (BE) will log unique identifiers from your drives (like serial numbers, volume IDs, etc.). 
When you set up RAID 0, those identifiers get wiped or replaced, making your system appear brand new from a storage/hardware perspective.


## 🛠️ How Do I Know If My Motherboard Supports RAID 0?
✅ Step-by-step:
- Enter your BIOS/UEFI (usually by pressing DEL, F2, or F10 on boot).
- Look for:
 - SATA Configuration
 - Intel Rapid Storage Technology (IRST) -- Intel boards
 - RAIDXpert2 -- AMD boards
- If you see **RAID MODE**, your board most likely supports RAID 0.
- Refer to your motherboard manual or Google your motherboard model + RAID support.

> [!TIP]
> Even if your board supports RAID, you may need at least 2 drives of the same type (either 2× SSDs or 2× NVMe).

Type					NVMe RAID 0							SATA SSD RAID 0
Works for spoofing?		✅ Yes			   	   			   ✅ Yes
Setup Difficulty		🔧 Moderate–Hard	    		    🔧 Easy–Moderate
Controller Needed		Intel VMD / AMD RAIDXpert2	         Basic RAID controller

> [!IMPORTANT]
> NVMe RAID 0 might require driver injection during Windows install
> SATA SSD RAID 0 is easier for beginners

## 🧼 Why Do You Need RAID 0 for Ban Evasion?

Anti-cheats can track:
- Disk Serial Numbers
- Volume IDs
- Firmware versions
- Hidden sector data

> [!NOTE]
> When you use RAID 0, you completely overwrite these markers and build a new virtual disk with its own RAID-specific ID — making your system look like a new machine.

## 📦 Bonus: RAID 0 Tips for Evasion

- Always delete all partitions during RAID setup
- Always re-create your array pool on ban
- Use a clean Windows ISO after creating the RAID array
- Do not use backup images or old installs

### 🎮 Graphic card (GPU) spoofing

EasyAntiCheat does not log your graphics card’s serial number—since GPUs are frequently resold, tracking serials would cause many false bans. 
However, it’s worth mentioning that the anticheat does log the name/model of your graphics card.

### 🔌 USB Adapter spoofing

If you're concerned about USB device serials such as:

- Headset
- Keyboard
- Mouse
- RGB devices (CPU fans, etc.)

You can choose to buy Chinese or unbranded USB peripherals, or simply stick with [Razer](https://www.razer.com/)

All Razer products—headsets, mice, keyboards—come with no serial numbers from the factory, making them ideal for spoofing purposes.

### 📶 Router / Network Adapter spoofing

EasyAntiCheat/Vanguard can use ARP and nearby device scanning to catch players in games like Fortnite tournaments. 
If you’re worried about your MAC address leaking through ARP or nearby device detection, I recommend getting a separate router for your cheating setup, isolating it from your normal devices.

Keep in mind, even if your router supports MAC spoofing, it doesn’t always mean the spoofed MAC is actually reported to your connected devices.

While I haven’t personally seen this method used against Rust players on EasyAntiCheat, it’s definitely something to consider if you want to stay legit.

### 🖥️ Monitor Spoofing Guide

> [!IMPORTANT]
> If you're experiencing black screens after spoofing or restarting your PC, disable FreeSYNC/SYNC in your monitor’s on-screen panel settings before proceeding.
> 
> If you do get a black screen:
> 
> → Re-plugging the display cable or switching ports on the back of your PC and restarting a few times usually resolves it.
> 
> Recommendation: `Disable FreeSYNC/SYNC before starting to avoid issues.`

## Required Tool
CRU (Custom Resolution Utility):
🔗 https://customresolutionutility.net/

## Instructions
- Launch CRU.exe
- In the drop-down list at the top left, select each monitor (including inactive ones)
- Click Edit (top right)

🔹 Device ID Section
- ID: Leave as default
- ID Serial #: Clear the field until the box is empty

🔹 Serial Number Section
- Clear the field until the box is empty
- Check “Include if slot available”

- Click OK
- Repeat these steps for each monitor listed

### 🧬 SMBIOS Spoofing Guide

- You’ll need the binaries listed in the referenced repo (⚠️ I did not create these binaries)
- After spoofing all SMBIOS fields, you must reinstall your Operating System
- Reinstall using a clean Windows ISO bootable USB
- Delete all partitions or destroy the RAID pool before reinstalling

> [!WARNING]
> You might get away skipping some steps — but don’t blame me if you get banned.
> 
> Follow everything carefully for a fully clean slate.
