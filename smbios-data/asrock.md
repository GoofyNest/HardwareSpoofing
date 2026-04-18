---
description: ASRock only has 2 unique identifiers, BaseSerial and UUID
icon: '2'
---

# ASRock

Tools used can be found on the GitHub in [release section](https://github.com/GoofyNest/HardwareSpoofing/releases), if you have issues sometimes its required to downgrade bios version or reinstall windows.

It can be super weird, but you can reach out to us in Discord for free support.

{% hint style="warning" icon="megaphone" %}
This is just a example dump of a real ASRock SMBios that has never been modified.
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
P1.60
```

**Command prompt:**

```
AMIDEWINx64.exe /IV "P1.60"
```

### BIOS Release Date (/ID)

{% hint style="danger" %}
Logged by EAC, but flashing your BIOS can change this without permanent spoofing
{% endhint %}

```
05/05/2023
```

**Command prompt:**

```
AMIDEWINx64.exe /ID "05/05/2023"
```

## \[Type 001] -- System Information

***

### Manufacturer (/SM)

```
ASRock
```

**Command Prompt**:

```
AMIDEWINx64.exe /SM "ASRock"
```

### Product Name (/SP)

{% hint style="danger" %}
Do not change this unless your motherboard is misidentified or has issues.

This field should match the exact model printed on your motherboard.
{% endhint %}

```
H510M-HDV/M.2 SE
```

**Command Prompt:**

```
AMIDEWINx64.exe /SP "H510M-HDV/M.2 SE"
```

### Version (/SV)

{% hint style="danger" %}
Do not change this, it should always be `To Be Filled By O.E.M.` across the board
{% endhint %}

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /SV "To Be Filled By O.E.M."
```

### Serial Number (/SS)

{% hint style="danger" %}
Do not change this, it should always be `To Be Filled By O.E.M.` across the board
{% endhint %}

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /SS "To Be Filled By O.E.M."
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

{% hint style="danger" %}
Do not change this, it should always be `To Be Filled By O.E.M.` across the board
{% endhint %}

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /SK "To Be Filled By O.E.M."
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

{% hint style="danger" %}
Same as Type 001 Manufacturer
{% endhint %}

```
ASRock
```

**Command Prompt:**

```
AMIDEWINx64.exe /BM "ASRock"
```

### Product Name (/BP)

{% hint style="danger" %}
Do not change this unless your motherboard is misidentified or has issues.

This field should match the exact model printed on your motherboard.
{% endhint %}

```
H510M-HDV/M.2 SE
```

**Command Prompt:**

```
AMIDEWINx64.exe /BP "H510M-HDV/M.2 SE"
```

### Version (/BV)

{% hint style="danger" %}
Do not change this field. It typically consists of 22 space characters (0x20) across all ASRock motherboards.
{% endhint %}

```
                      
```

**Command Prompt:**

```
AMIDEWINx64.exe /BV "                      "
```

### Serial Number (/BS)

{% hint style="info" %}
If you are lazy and dont wanna change it ever again just set it to `To Be Filled By O.E.M.`
{% endhint %}

```
BR80YFDYZ68ICQ4
```

**Command Prompt:**

```
AMIDEWINx64.exe /BS "BR80YFDYZ68ICQ4"
```

### Asset Tag (/BT)

{% hint style="danger" %}
Do not change this field. It typically consists of 22 space characters (0x20) across all ASRock motherboards.
{% endhint %}

```
                      
```

**Command Prompt:**

```
AMIDEWINx64.exe /BT "                      "
```

### Location in Chassi (/BLC)

{% hint style="danger" %}
Do not change this field. It typically consists of 22 space characters (0x20) across all ASRock motherboards.
{% endhint %}

```
                      
```

**Command Prompt:**

```
AMIDEWINx64.exe /BLC "                      "
```

## \[Type 003] -- System Enclosure or Chassis

***

### Manufacturer (/CM)

{% hint style="danger" %}
Do not change this, it should always be `To Be Filled By O.E.M.` across the board
{% endhint %}

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /CM "To Be Filled By O.E.M."
```

### Version (/CV)

{% hint style="danger" %}
Do not change this, it should always be `To Be Filled By O.E.M.` across the board
{% endhint %}

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /CV "To Be Filled By O.E.M."
```

### Serial Number (/CS)

{% hint style="danger" %}
Do not change this, it should always be `To Be Filled By O.E.M.` across the board
{% endhint %}

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /CS "To Be Filled By O.E.M."
```

### Asset Tag (/CA)

{% hint style="danger" %}
Do not change this, it should always be `To Be Filled By O.E.M.` across the board
{% endhint %}

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /CA "To Be Filled By O.E.M."
```

### SKU Number (/CSK)

{% hint style="danger" %}
Do not change this, it should always be `To Be Filled By O.E.M.` across the board
{% endhint %}

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /CSK "To Be Filled By O.E.M."
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
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /OS "To Be Filled By O.E.M."
```

## \[Type 012] -- System Configuration Options

***

### String #1 (/SCO)

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /SCO "To Be Filled By O.E.M."
```

