# 🖥️ Supported Operating System

### ✅ **[Windows 10](https://drive.massgrave.dev/en-us_windows_10_iot_enterprise_ltsc_2021_x64_dvd_257ad90f.iso)** – Fully supported and recommended

> [!WARNING]
> **Custom Resolution Utility (CRU)** does **not** work reliably on Windows 11.  
> If you're using Windows 11, spoofing your monitor may not be possible.

> [!IMPORTANT]
> If you like Windows 11 and want to check if your existing monitor does not have a serial number you can run this command in **powershell:**
```
Get-WmiObject -Namespace root\wmi -Class WmiMonitorID | ForEach-Object {
    if ($_.UserFriendlyName) {
        $name = ($_.UserFriendlyName | ForEach-Object { [char]$_ }) -join ''
        $serial = ($_.SerialNumberID | ForEach-Object { [char]$_ }) -join ''
        Write-Output "Monitor: $name"
        Write-Output "Serial Number: $serial"
        Write-Output ""
    }
}
```

> [!TIP]
> You can ignore this limitation **if your monitor does not have a serial number**, or if you're using one of the listed devices we recommend.
> 
> 📝 We're working on a document listing **monitors and peripherals that don't include serial numbers**, so you can buy spoof-safe hardware without guessing.

# Supported motherboards
- [ASRock](https://github.com/GoofyNest/HardwareSpoofing/blob/main/ASRock.md)
- [Gigabyte](https://github.com/GoofyNest/HardwareSpoofing/blob/main/Gigabyte.md)
- [ASUS](https://github.com/GoofyNest/HardwareSpoofing/blob/main/ASUS.md) ⚠️
- MSI ⚠️

> [!IMPORTANT]
> Most of the ASUS motherboards are supported
> 
> The new ASUS motherboards can be hard to spoof and require newer AMIDEWIN, you can try to google for a newer version or one that work for your motherboard.

> [!IMPORTANT]
> Most of the MSI motherboards are supported
> 
> The new MSI motherboards can be hard to spoof and require newer AMIDEWIN, you can try to google for a newer version or one that work for your motherboard.

# Trusted Platform Module (TPM)
> [!CAUTION]
> You **must disable the Trusted Platform Module (TPM)** in your BIOS.  
> TPM keys are **unique per system** and can be used by anti-cheat systems to instantly identify and ban you.  
> Leaving TPM enabled is one of the fastest ways to get flagged, even if everything else is spoofed.
>
> You can check if TPM is enabled by opening powershell and running this query:

```
get-tpm
```

This should be the console output if disabled:
```
PS C:\Windows\system32> get-tpm


TpmPresent                : False
TpmReady                  : False
TpmEnabled                : False
TpmActivated              : False
TpmOwned                  : False
RestartPending            : False
ManufacturerId            : 0
ManufacturerIdTxt         :
ManufacturerVersion       :
ManufacturerVersionFull20 :
ManagedAuthLevel          : Full
OwnerAuth                 :
OwnerClearDisabled        : True
AutoProvisioning          : NotDefined
LockedOut                 : False
LockoutHealTime           :
LockoutCount              :
LockoutMax                :
SelfTest                  :
```

# Ram modules without (Serial number)
> [!CAUTION]
> You must have Ram that does not have a unique serial number.

**Open cmd.exe** and write this command
```
wmic memorychip get SerialNumber
```

if it reports `00000000` or something that does not look unique, you are good to continue.

> [!IMPORTANT]
> We recommend using Corsair Vengeance, all their modules (DDR4 and DDR5) does not have a serial number 

> [!TIP]
> 📝 We're working on a tool that will do all the requirement checks for you so you dont need to do manual labour. For now you can use [MaybeSpoofed](https://github.com/goofynest/maybespoofed)
> 
> 📝 We're working on a document listing **components that don't include a serial number**, so you can buy spoof-safe hardware without guessing.

# 🎮 Graphic card (GPU) spoofing

EasyAntiCheat does not log your graphics card’s serial number since GPUs are frequently resold, tracking serials would cause many false bans. 
However, it’s worth mentioning that the anticheat does log the name/model of your graphics card.

# 🔌 USB Adapter spoofing

If you're concerned about USB device serials such as:

- Headset
- Keyboard
- Mouse
- RGB devices (CPU fans, etc.)

You can choose to buy Chinese or unbranded USB peripherals, or simply stick with [Razer](https://www.razer.com/)

All Razer products—headsets, mice, keyboards—come with no serial numbers from the factory, making them ideal for spoofing purposes.

# 📶 Router / Network Adapter spoofing

EasyAntiCheat/Vanguard can use ARP and nearby device scanning to catch players in games like Fortnite tournaments. 
If you’re worried about your MAC address leaking through ARP or nearby device detection, I recommend getting a separate router for your cheating setup, isolating it from your normal devices.

Keep in mind, even if your router supports MAC spoofing, it doesn’t always mean the spoofed MAC is actually reported to your connected devices.

While I haven’t personally seen this method used against Rust players on EasyAntiCheat, it’s definitely something to consider if you want to stay legit.

# MAC Spoofing
> [!TIP]
> Anti-cheats often **flag MAC addresses for about a week after a ban**.  
> To avoid being tracked or temporarily blocked, we recommend:
>
> - Replacing your **new USB Ethernet adapter** after each ban
> - **or**  
> - Replacing your **WiFi chip** after each ban
>
> Swapping either one will give you a fresh MAC address and prevent network-based detection.

> [!WARNING]
> Make sure to **disable your onboard Ethernet (LAN) adapter** in your BIOS.  
> Leaving it enabled can expose your real MAC address even if you're using a new adapter.

### Recommended products:
[TP link UE300](https://www.tp-link.com/nordic/home-networking/computer-accessory/ue300/) around 9$

[Amazon Basics USB 3.0 to 10/100/1000 Ethernet](https://www.amazon.se/Amazon-Basics-Gigabit-Ethernet-internetadapter/dp/B00M77HMU0) around 10$

# Disable Trusted PlatForm Module (TPM)
## 🏷️ TPM can have many names, some are listed below:
- 🔹 ASUS
  - Trusted Computing
  - TPM Device Selection → Discrete / Firmware
  - PTT (for Intel boards)

- 🔹 MSI
  - Security Device Support
  - AMD fTPM or Intel PTT

- 🔹 Gigabyte
  - Trusted Computing
  - Intel Platform Trust Technology (PTT)

- 🔹 ASRock
  - Security → Intel PTT / AMD fTPM

- 🔹 HP / Dell / Lenovo (OEM)
  - Embedded Security Device
  - TPM State
  - Security Chip
  - TPM On/Off
 
# Disable or Unplug WiFi and Bluetooth card
> [!CAUTION]
> You **must disable WiFi and Bluetooth** in your BIOS or physically remove them from your system.  
> These modules contain **unique MAC addresses and device IDs** that can be used to track and ban you.  
> **Leaving them enabled leaks real hardware data**, even if everything else is spoofed.  
>  
> ✅ You can ignore this warning **only if you replace your WiFi chip after every ban**, as this resets the identifiers.


# Disk Serial spoofing (Raid 0)
**RAID 0** is a storage setup that combines two or more drives into a single "virtual" drive using a method called striping. 

While it’s traditionally used for performance, in ban evasion, the goal is different:

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

Type | NVMe RAID 0 | SATA SSD RAID 0
--- | --- | --- | 
Works for spoofing? | ✅ Yes | ✅ Yes
Setup Difficulty | 🔧 Moderate–Hard | 🔧 Easy–Moderate
Controller Needed | Intel VMD / AMD RAIDXpert2 | Basic RAID controller

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
