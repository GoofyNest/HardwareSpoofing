---
description: Written by @Goofy
icon: burst-new
---

# Spoof order

{% hint style="info" %}
This guide can be overwhelming, but I hope this will help people
{% endhint %}

## 1. Bios

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

## 2. Motherboard spoofing

```mermaid
flowchart TD
    A["📍 You are here"] --> B{"Do you want to use our automatic tool?"}

    B -->|Yes| C{"What's your motherboard?"}
    B -->|No| D["Manual Tools"]

    C --> E["ASUS"]
    C --> F["ASRock"]
    C --> G["Gigabyte"]
    C --> H["MSI"]

    click E "https://goofynest.gitbook.io/spoof/asus" "Manual ASUS"
    click F "https://goofynest.gitbook.io/spoof/step-1" "Automatic ASRock"
    click G "https://goofynest.gitbook.io/spoof/step-1" "Automatic Gigabyte"
    click H "https://goofynest.gitbook.io/spoof/step-1" "Automatic MSI"
    click D "https://goofynest.gitbook.io/spoof/tools" "Spoofing tools"
```

***

## 3. Mac spoofing

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

## 4. Disk spoofing

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

## 5. Ram spoofing

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

***

## 6. Arp spoofing

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

## 7. Monitor spoofing

```mermaid
flowchart TD
    A["📍 You are here"] --> B{"Do you know how to open PowerShell?"}

    B -->|No| C["💀"]
    B -->|Yes| D["Open PowerShell"]

    D --> E["Run the command below"]

    E --> F{"Does your monitor have a non-unique serial number?"}

    F -->|Yes| G["Good 👍"]
    F -->|No| H{"Choose an option"}

    H --> I["HDMI EDID Emulator Adapter"]
    H --> J["DR HDMI"]
    H --> K["Dichen 5"]

    click I "https://goofynest.gitbook.io/spoof/monitor-spoofing/hdmi-edid-emulator-adapter"
    click J "https://goofynest.gitbook.io/spoof/monitor-spoofing/dr-hdmi"
    click K "https://goofynest.gitbook.io/spoof/monitor-spoofing/dichen-5"
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
