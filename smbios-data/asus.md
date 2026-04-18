---
description: ASUS = A Surprisingly Unreliable System
icon: '4'
---

# ASUS

Tools used can be found on the GitHub in [release section](https://github.com/GoofyNest/HardwareSpoofing/releases), if you have issues sometimes its required to downgrade bios version or reinstall windows.

It can be super weird, but you can reach out to us in Discord for free support.

{% hint style="warning" icon="megaphone" %}
This is just a example dump of a real ASUS SMBios that has never been modified.
{% endhint %}

### Credits to @exclusi0n for finding ASUS proper spoof method

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
After a lot of testing it seems that ASUS boards reset the Serial Number after computer restart when spoofing with DMI\_EDIT

Ensure that ur serial number that u change stays after computer restart.
{% endhint %}

## \[Type 000] -- BIOS Information

***

### BIOS Vendor (/IVN)

{% hint style="danger" %}
Do not change this, it should always be `American Megatrends Inc.` across the board
{% endhint %}

```
American Megatrends Inc.
```

**Command prompt:**

```
AMIDEWINx64.exe /IVN "American Megatrends Inc."
```

### BIOS Version (/IV)

{% hint style="danger" %}
Logged by EAC, but flashing your BIOS can change this without permanent spoofing
{% endhint %}

```
1903
```

**Command prompt:**

```
AMIDEWINx64.exe /IV "1903"
```

### BIOS Release Date (/ID)

{% hint style="danger" %}
Logged by EAC, but flashing your BIOS can change this without permanent spoofing
{% endhint %}

```
07/08/2021
```

**Command prompt:**

```
AMIDEWINx64.exe /ID "07/08/2021"
```

## \[Type 001] -- System Information

***

### Manufacturer (/SM)

```
ASUS
```

**Command Prompt**:

```
AMIDEWINx64.exe /SM "ASUS"
```

### Product Name (/SP)

```
System Product Name
```

**Command Prompt:**

```
AMIDEWINx64.exe /SP "System Product Name"
```

### Version (/SV)

```
System Version
```

**Command Prompt:**

```
AMIDEWINx64.exe /SV "System Version"
```

### Serial Number (/SS)

```
System Serial Number
```

**Command Prompt:**

```
AMIDEWINx64.exe /SS "System Serial Number"
```

### UUID (/SU)

{% hint style="danger" %}
The UUID is normally tied to your NIC on your motherboard and other stuff, the easiest option is setting it to **Default** or just nulling it with **0's**
{% endhint %}

```
03000200-0400-0500-0006-000700080009
```

**Command Prompt:**

```
AMIDEWINx64.exe /SU 03000200040005000006000700080009
```

### SKUNumber (/SK)

```
ASUS_MB_CNL
```

**Command Prompt:**

```
AMIDEWINx64.exe /SK "ASUS_MB_CNL"
```

### Family (/SF)

{% hint style="danger" %}
Only change this if its incorrect.
{% endhint %}

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /SF "To Be Filled By O.E.M."
```

## \[Type 002] -- Base Board/Module information

***

### Manufacturer (/BM)

```
ASUSTeK COMPUTER INC.
```

**Command Prompt:**

```
AMIDEWINx64.exe /BM "ASUSTeK COMPUTER INC."
```

### Product Name (/BP)

{% hint style="danger" %}
Do not change this unless your motherboard is misidentified or has issues.

This field should match the exact model printed on your motherboard.
{% endhint %}

```
ROG STRIX Z390-E GAMING
```

**Command Prompt:**

```
AMIDEWINx64.exe /BP "ROG STRIX Z390-E GAMING"
```

### Version (/BV)

```
Rev 1.xx
```

**Command Prompt:**

```
AMIDEWINx64.exe /BV "Rev 1.xx"
```

### Serial Number (/BS)

{% hint style="info" %}
If you are lazy and dont wanna change it ever again just set it to `To Be Filled By O.E.M.`
{% endhint %}

{% hint style="danger" %}
Keep the same start `1904` and the same size, but randomize the numbers.
{% endhint %}

```
190476921854307
```

**Command Prompt:**

```
AMIDEWINx64.exe /BS "190476921854307"
```

### Asset Tag (/BT)

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /BT "Default string"
```

### Location in Chassi (/BLC)

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /BLC "Default string"
```

## \[Type 003] -- System Enclosure or Chassis

***

### Manufacturer (/CM)

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /CM "Default string"
```

### Version (/CV)

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /CV "Default string"
```

### Serial Number (/CS)

{% hint style="danger" %}
Keep the same start `A51` and the same size, but randomize the numbers.
{% endhint %}

```
A51H0B3RA7T9
```

**Command Prompt:**

```
AMIDEWINx64.exe /CS "A51H0B3RA7T9"
```

### Asset Tag (/CA)

{% hint style="danger" %}
Serial Number, Asset Tag and SKU should have the same serial number
{% endhint %}

```
A51H0B3RA7T9
```

**Command Prompt:**

```
AMIDEWINx64.exe /CA "A51H0B3RA7T9"
```

### SKU Number (/CSK)

{% hint style="danger" %}
Serial Number, Asset Tag and SKU should have the same serial number
{% endhint %}

```
A51H0B3RA7T9
```

**Command Prompt:**

```
AMIDEWINx64.exe /CSK "A51H0B3RA7T9"
```

## \[Type 004] -- Processor information

***

### Serial Number (/PSN)

```
To Be Filled By O.E.M.
```

or

```
Unknown
```

**Command Prompt:**

```
AMIDEWINx64.exe /PSN "To Be Filled By O.E.M."
```

### Asset Tag (/PAT)

```
To Be Filled By O.E.M.
```

or

```
Unknown
```

**Command Prompt:**

```
AMIDEWINx64.exe /PAT "To Be Filled By O.E.M."
```

### Part Number (/PPN)

```
To Be Filled By O.E.M.
```

or

```
Unknown
```

**Command Prompt:**

```
AMIDEWINx64.exe /PPN "To Be Filled By O.E.M."
```

## \[Type 011] -- OEM Strings

***

### String #1 (/OS) (might have multiple OS strings)

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /OS "To Be Filled By O.E.M."
```

## \[Type 012] -- System Configuration Options

***

### String #1 (/SCO) (might have multiple SCO strings)

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /SCO "To Be Filled By O.E.M."
```

