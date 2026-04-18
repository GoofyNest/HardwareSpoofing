---
description: MSI = Maybe Send Itback
icon: '3'
---

# MSI

Tools used can be found on the GitHub in [release section](https://github.com/GoofyNest/HardwareSpoofing/releases), if you have issues sometimes its required to downgrade bios version or reinstall windows.

It can be super weird, but you can reach out to us in Discord for free support.

{% hint style="warning" icon="megaphone" %}
This is just a example dump of a real MSI SMBios that has never been modified.
{% endhint %}

## \[Type 000] -- BIOS Information

***

### BIOS Vendor (/IVN)

{% hint style="danger" %}
Do not change this, it should always be `American Megatrends International, LLC.` across the board
{% endhint %}

```
American Megatrends International, LLC.
```

**Command prompt:**

```
AMIDEWINx64.exe /IVN "American Megatrends International, LLC."
```

### BIOS Version (/IV)

{% hint style="danger" %}
Logged by EAC, but flashing your BIOS can change this without permanent spoofing
{% endhint %}

```
1.70
```

**Command prompt:**

```
AMIDEWINx64.exe /IV "1.70"
```

### BIOS Release Date (/ID)

{% hint style="danger" %}
Logged by EAC, but flashing your BIOS can change this without permanent spoofing
{% endhint %}

```
03/25/2024
```

**Command prompt:**

```
AMIDEWINx64.exe /ID "03/25/2024"
```

## \[Type 001] -- System Information

***

### Manufacturer (/SM)

```
Micro-Star International Co., Ltd.
```

**Command Prompt**:

```
AMIDEWINx64.exe /SM "Micro-Star International Co., Ltd."
```

### Product Name (/SP)

{% hint style="danger" %}
Your motherboard should have a `MS-MODELNUMBER` if you cannot find it, then google it and ensure its correct. Do not change this if your values are already good.
{% endhint %}

```
MS-7D95
```

**Command Prompt:**

```
AMIDEWINx64.exe /SP "MS-7D95"
```

### Version (/SV)

```
1.0
```

**Command Prompt:**

```
AMIDEWINx64.exe /SV "1.0"
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

```
Micro-Star International Co., Ltd.
```

**Command Prompt:**

```
AMIDEWINx64.exe /BM "Micro-Star International Co., Ltd."
```

### Product Name (/BP)

{% hint style="danger" %}
Do not change this unless your motherboard is misidentified or has issues.

This field should match the exact model printed on your motherboard.
{% endhint %}

```
PRO B550M-P GEN3 (MS-7D95)
```

**Command Prompt:**

```
AMIDEWINx64.exe /BP "PRO B550M-P GEN3 (MS-7D95)"
```

### Version (/BV)

```
1.0
```

**Command Prompt:**

```
AMIDEWINx64.exe /BV "1.0"
```

### Serial Number (/BS)

{% hint style="info" %}
If you are lazy and dont wanna change it ever again just set it to `To Be Filled By O.E.M.`
{% endhint %}

{% hint style="warning" %}
Remember that you should not copy this serial number, use the one present on your board and randomize that one

Keep the same start `07D9X40_` and the same size, but randomize the serial after the underline.
{% endhint %}

```
07D9X40_J19K6852MC
```

**Command Prompt:**

```
AMIDEWINx64.exe /BS "07D9X40_J19K6852MC"
```

### Asset Tag (/BT)

```
To be filled by O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /BT "To be filled by O.E.M."
```

### Location in Chassi (/BLC)

```
To be filled by O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /BLC "To be filled by O.E.M."
```

## \[Type 003] -- System Enclosure or Chassis

***

### Manufacturer (/CM)

```
Micro-Star International Co., Ltd.
```

**Command Prompt:**

```
AMIDEWINx64.exe /CM "Micro-Star International Co., Ltd."
```

### Version (/CV)

```
1.0
```

**Command Prompt:**

```
AMIDEWINx64.exe /CV "1.0"
```

### Serial Number (/CS)

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /CS "To Be Filled By O.E.M."
```

### Asset Tag (/CA)

```
To Be Filled By O.E.M.
```

**Command Prompt:**

```
AMIDEWINx64.exe /CA "To Be Filled By O.E.M."
```

### SKU Number (/CSK)

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

