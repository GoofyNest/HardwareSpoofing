---
description: Written by @Goofy
icon: burst-new
---

# Spoof order

{% hint style="info" %}
This guide can be overwhelming, but I hope this will help people
{% endhint %}

## Bios

```mermaid
flowchart TD
    A["📍 You are here"] --> B[Enter your BIOS]

    B --> G[CSM]
    G --> G1[Disable]

    B --> C[Secure Boot]
    C --> C1[Disable]

    B --> D[TPM]
    D --> D1[Disable]

    B --> E[Bluetooth]
    E --> F1

    B --> F[Wi-Fi]
    F --> F1["Can you disable it?"]
    F1 --> F11[Yes]
    F1 --> F12[No]
    F12 --> F22["Physically remove chip"]

    C1 --> H[Save Changes]
    D1 --> H
    F11 --> H
    G1 --> H
    F22 --> H

    H --> I[Restart]
```

***

## USB Serials

{% hint style="warning" %}
Not confirmed if this cause issues, but you might as well replace USB devices with serials
{% endhint %}

{% embed url="https://www.nirsoft.net/utils/usbdeview-x64.zip" %}

Replace anything that has serial, you can find part list here:

{% embed url="https://goofynest.gitbook.io/spoof/part-list/devices" %}

***

## Graphic card

{% hint style="warning" %}
Not confirmed if this cause issues
{% endhint %}

<mark style="color:$danger;">NVIDIA Graphic cards have serial numbers</mark> that at the moment is not perm-spoofable.

I highly recommend you to get a <mark style="color:green;">AMD graphic card from Gigabyte</mark>.

***

## Motherboard spoofing

```mermaid
flowchart TD
    A["📍 You are here"] --> B{"Do you want to use our automatic tool?"}

    B -->|Yes| C{"What's your motherboard?"}
    B -->|No| D["Manual Tools"]

    C --> E["ASUS"]
    C --> F["ASRock"]
    C --> G["Gigabyte"]
    C --> H["MSI"]
    
    E --> EE["Newer generation"]
    E --> EE1["Older generation"]

    click EE1 "https://goofynest.gitbook.io/spoof/asus" "Manual ASUS"
    click EE "https://goofynest.gitbook.io/spoof/ch341a" "Manual ASUS"
    click F "https://goofynest.gitbook.io/spoof/step-1" "Automatic ASRock"
    click G "https://goofynest.gitbook.io/spoof/step-1" "Automatic Gigabyte"
    click H "https://goofynest.gitbook.io/spoof/step-1" "Automatic MSI"
    click D "https://goofynest.gitbook.io/spoof/tools" "Spoofing tools"
```

***

## Mac spoofing

```mermaid
flowchart TD
    A["📍 You are here"] --> B{"Do you want to spoof onboard?"}

    B -->|Yes| C{"What's your onboard NIC?"}
    B -->|No| D["USB Network Adapter"]

    C --> E["Realtek NICs"]
    C --> F["Intel NICs"]

    D --> G["TP-Link UE300"]
    D --> H["Realtek USB Adapter"]
    D --> I["Captain USB Adapter"]

    click E "https://goofynest.gitbook.io/spoof/mac-spoofing/realtek-nics" "Realtek spoofing"
    click F "https://goofynest.gitbook.io/spoof/mac-spoofing/intel-nics" "Intel spoofing"
    click G "https://goofynest.gitbook.io/spoof/mac-spoofing/tp-link-ue300" "TP-Link spoofing"
    click H "https://goofynest.gitbook.io/spoof/mac-spoofing/realtek-usb-adapter" "Realtek USB"
    click I "https://goofynest.gitbook.io/spoof/mac-spoofing/captain-usb-adapter" "Captain USB"
```

***

## Disk spoofing

```mermaid
flowchart TD
    A["📍 You are here"] --> B{"Do you want a cheap solution?"}

    B -->|Yes| C{"Are you okay with it possibly not working forever?"}
    B -->|No| D{"Choose an SSD"}

    C -->|Yes| E["Sabrent EC-SVNE"]
    C -->|No| D

    D --> F["SMI SM2263XT"]
    D --> G["KingSpec SSD"]

    click E "https://goofynest.gitbook.io/spoof/disk-spoofing/sabrent-ec-svne" "Sabrent EC-SVNE"
    click F "https://goofynest.gitbook.io/spoof/disk-spoofing/smi-sx2263xt" "SMI SX2263XT"
    click G "https://goofynest.gitbook.io/spoof/disk-spoofing/kingspec-ssd" "KingSpec SSD"
```

***

## Ram spoofing

```mermaid
flowchart TD
    A["📍 You are here"] --> B{"Do you know how to open CMD?"}

    B -->|No| C["💀"]
    B -->|Yes| D["Open CMD"]

    D --> E["Run:<br/>wmic memorychip get serialnumber"]

    E --> F{"Does your RAM have a non-unique serial number?"}

    F -->|Yes| G["Good 👍"]
    F -->|No| H["SPD Security Editor"]
    
    click H "https://goofynest.gitbook.io/spoof/ram-spoofing/spd-security-editor" "Ram spoofing"
```

```bash
wmic memorychip get serialnumber
```

***

## Arp spoofing

```mermaid
flowchart TD
    A["📍 You are here"] --> B{"Do you have a modern router?"}

    B -->|Yes| C["Check if your router supports OpenWRT firmware"]
    B -->|No| D["Alternative Ways"]

    D --> E["Do you have 2 computers?"] 
    E --> DDD["Yes"]
    DDD --> DDDD["Windows internet sharing"]
    D --> EE["GL.iNet GL-SFT1200"]
    D --> EEE["Raspberry Pi 4 Model B"]

    C --> G["Continue to next section"]

    click EE "https://goofynest.gitbook.io/spoof/arp-spoofing/gl.inet-gl-sft1200" "New router"
    click EEE "https://goofynest.gitbook.io/spoof/arp-spoofing/raspberry-pi-4-model-b" "Alternative method"

```

***

## Monitor spoofing

```mermaid
flowchart TD
    A["📍 You are here"] --> B{"Do you know how to open PowerShell?"}

    B -->|No| C["💀"]
    B -->|Yes| D["Open PowerShell"]

    D --> E["Run the command below"]

    E --> F{"Does your monitor have a non-unique serial number?"}

    F -->|Yes| G["Good 👍"]
    F -->|No| H{"Choose an option"}

    H --> I["EDID Emulator Adapter"]
    H --> J["DR HDMI"]
    H --> K["Dichen 5"]
    H --> L["Hardware mod"]

    click I "https://goofynest.gitbook.io/spoof/monitor-spoofing/hdmi-edid-emulator-adapter" "Alt 1"
    click J "https://goofynest.gitbook.io/spoof/monitor-spoofing/dr-hdmi" "Alt 2"
    click K "https://goofynest.gitbook.io/spoof/monitor-spoofing/dichen-5" "Alt 3"
    click L "https://goofynest.gitbook.io/spoof/monitor-spoofing/hardware-mod" "Alt 4"
```

```powershell
    Get-CimInstance -Namespace root\wmi -ClassName WmiMonitorID | ForEach-Object {
    [PSCustomObject]@{
        Manufacturer = ($_.ManufacturerName -ne 0 | ForEach-Object {[char]$_}) -join ""
        Model        = ($_.UserFriendlyName -ne 0 | ForEach-Object {[char]$_}) -join ""
        SerialNumber = ($_.SerialNumberID -ne 0 | ForEach-Object {[char]$_}) -join ""
        }
    }
```

***

## Clear NVRAM

{% embed url="https://goofynest.gitbook.io/spoof/nvram-spoofing/efivars" %}

***

## Reinstall windows

{% embed url="https://goofynest.gitbook.io/spoof/windows/reinstall" %}

***

## Misc stuff

> You might wonder why I said disable CSM / Secure boot?

### Yes?

> Does this mean our spoofer does not support CSM / Secure boot?

### No

### The reasoning we are disabling CSM is to avoid issues when spoofing your motherboard with DMI edit or AMIDEWINx64

### The reasoning we are disabling Secure boot is to allow you to use our tool for editing NVRAM, Efivars from [efivars.md](../nvram-spoofing/efivars.md "mention")

After you have reinstalled Windows you can enable all security features if you want again.

* Secure boot
* CSM
* IOMMU
* Virtualization

<mark style="color:$danger;">**Just do not enable TPM if your fTPM key was banned before**</mark>**&#x20;**<mark style="color:$primary;">**because if you do that then you have to redo clearing NVRAM and reinstalling Windows again.**</mark>

<mark style="color:$danger;">**And remember that**</mark> [step-3.md](step-3.md "mention") <mark style="color:$danger;">always applies</mark>

<mark style="color:$primary;">**Right now I really recommend people using dTPM (Discrete trusted platform module) instead of spoofing their fTPM.**</mark>

{% embed url="https://discord.com/invite/JtU8FxQnN5" %}

Always remember that you can join our discord for help, just do not waste our time.

> Read <mark style="color:pink;">**#create-a-ticket**</mark> before opening a ticket.

And avoid asking us questions like

* Can you recommend me a spoofer
