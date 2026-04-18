---
description: >-
  Gigabyte is the easiest motherboard to spoof, the only thing that is Unique is
  UUID and EasyAntiCheat does not log it.
icon: '1'
---

# Gigabyte

Tools used can be found on the GitHub in [release section](https://github.com/GoofyNest/HardwareSpoofing/releases), if you have issues sometimes its required to downgrade bios version or reinstall windows.

It can be super weird, but you can reach out to us in Discord for free support.

{% hint style="warning" icon="megaphone" %}
This is just a example dump of a real Gigabyte SMBios that has never been modified.
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
F12
```

**Command prompt:**

```
AMIDEWINx64.exe /IV "F12"
```

### BIOS Release Date (/ID)

{% hint style="danger" %}
Logged by EAC, but flashing your BIOS can change this without permanent spoofing
{% endhint %}

```
01/18/2021
```

**Command prompt:**

```
AMIDEWINx64.exe /ID "01/18/2021"
```

## \[Type 001] -- System Information

***

### Manufacturer (/SM)

```
Gigabyte Technology Co., Ltd.
```

**Command Prompt**:

```
AMIDEWINx64.exe /SM "Gigabyte Technology Co., Ltd."
```

### Product Name (/SP)

{% hint style="danger" %}
Do not change this unless your motherboard is misidentified or has issues.

This field should match the exact model printed on your motherboard.
{% endhint %}

```
B550 GAMING X V2
```

**Command Prompt:**

```
AMIDEWINx64.exe /SP "B550 GAMING X V2"
```

### Version (/SV)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /SV "Default string"
```

### Serial Number (/SS)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /SS "Default string"
```

### UUID (/SU)

{% hint style="danger" %}
The UUID is normally tied to your NIC on your motherboard and other stuff, the easiest option is setting it to **Gigabyte Default** or just nulling it with **0's**
{% endhint %}

```
03000200-0400-0500-0006-000700080009
```

**Command Prompt:**

```
AMIDEWINx64.exe /SU 03000200040005000006000700080009
```

### SKUNumber (/SK)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /SK "Default string"
```

### Family (/SF)

{% hint style="danger" %}
Only change this if its incorrect.
{% endhint %}

This field start with the model of your motherboard such as `B550` followed by `MB`

```
B550 MB
```

**Command Prompt:**

```
AMIDEWINx64.exe /SF "B550 MB"
```

## \[Type 002] -- Base Board/Module information

***

### Manufacturer (/BM)

{% hint style="danger" %}
Same as Type 001 Manufacturer
{% endhint %}

```
Gigabyte Technology Co., Ltd.
```

**Command Prompt:**

```
AMIDEWINx64.exe /BM "Gigabyte Technology Co., Ltd."
```

### Product Name (/BP)

{% hint style="danger" %}
Do not change this unless your motherboard is misidentified or has issues.

This field should match the exact model printed on your motherboard.
{% endhint %}

```
B550 GAMING X V2
```

**Command Prompt:**

```
AMIDEWINx64.exe /BP "B550 GAMING X V2"
```

### Version (/BV)

```
x.x
```

**Command Prompt:**

```
AMIDEWINx64.exe /BV "x.x"
```

### Serial Number (/BS)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /BS "Default string"
```

### Asset Tag (/BT)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /BT "Default string"
```

### Location in Chassi (/BLC)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

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

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /CM "Default string"
```

### Version (/CV)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /CV "Default string"
```

### Serial Number (/CS)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /CS "Default string"
```

### Asset Tag (/CA)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /CA "Default string"
```

### SKU Number (/CSK)

{% hint style="danger" %}
Do not change this, it should always be `Default string` across the board
{% endhint %}

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /CSK "Default string"
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

### String #1 (/OS)

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /OS "Default string"
```

## \[Type 012] -- System Configuration Options

***

### String #1 (/SCO)

```
Default string
```

**Command Prompt:**

```
AMIDEWINx64.exe /SCO "Default string"
```

