---
description: Very important before you move forward
icon: '3'
---

# Step #3

## <mark style="color:$warning;">⚠️ Read Before Proceeding: Device Restrictions</mark>

You must never plug in or use any devices from a previously banned computer or account. Unless you know it does not have a unique serial number or allowed by this guide.

This includes, but is not limited to: phones, keyboards, mice, headsets, disks, USB storage devices, RAM, monitors, and external hard drives.

You are also not allowed to use your mobile hotspot or share a network connection from any previously used device, as it may expose identifiable information such as a unique MAC address.

If you connect or use any device that has been associated with a banned account, you will be required to fully reinstall your Windows operating system <mark style="color:$danger;">or you risk your account to be banned again and your hardware</mark>.

If this happens whilst the anticheat is running that you are ban evading on, <mark style="color:$danger;">you can say goodbye to your account</mark>.

## 1. fTPM, PTT

On AMD systems it will say something like <mark style="color:purple;">**AMD CPU TPM**</mark>

On Intel systems it can be named <mark style="color:purple;">**PTT, INTEL CPU TPM**</mark>

#### TPM Device Selection:&#xD; → Discrete TPM ✅ (what you want)&#xD; → Firmware TPM ❌ (disable this)

you can verify if its disabled if you boot into Windows and write this in powershell (admin)<br>

```powershell
get-tpm
```

If you do not have a TPM module yet everything should say `False`

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

<mark style="color:$danger;">Very important note, even if you buy a new motherboard you cannot have fTPM enabled.</mark>&#x20;

<mark style="color:$danger;">Since fTPM is from the CPU and not your motherboard.</mark>

## 2. Onboard settings

#### Disable the following: <mark style="color:purple;">(Disable everything that is not used)</mark>

* Onboard sound
* Onboard ethernet
* Onboard graphics
* Bluetooth / Wifi chip
* Fast startup

<mark style="color:red;">On some motherboards you have to physically remove the WiFi chip to fully disable its functions, it is very annoying but there is no other way.</mark>

## 3. Monitors

This guide only supports 1 monitor unless you have monitors that does not have serial numbers, you can verify by running this PowerShell script below:

```powershell
Get-CimInstance -Namespace root\wmi -ClassName WmiMonitorID | ForEach-Object {
    [PSCustomObject]@{
        Manufacturer = ($_.ManufacturerName -ne 0 | ForEach-Object {[char]$_}) -join ""
        Model        = ($_.UserFriendlyName -ne 0 | ForEach-Object {[char]$_}) -join ""
        SerialNumber = ($_.SerialNumberID -ne 0 | ForEach-Object {[char]$_}) -join ""
    }
}
```

If they show up as like&#x20;

```
0000 or 0001
```

you are good to continue.

If you have serial numbers and still wanna use 2 monitors I recommend getting one monitor without serial from our [devices.md](../part-list/devices.md "mention") or getting x2 fusers.

Or remote play your PC from platforms like [Sunshine](https://github.com/lizardbyte/sunshine) or [Parsec](https://parsec.app/) but that is nothing we will cover in this guide, you will have to figure it out by urself.

