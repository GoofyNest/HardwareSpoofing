---
description: ASUS = A Surprisingly Unreliable System
icon: '4'
---

# ASUS

Tools used can be found on the GitHub in [release section](https://github.com/GoofyNest/HardwareSpoofing/releases), if you have issues sometimes its required to downgrade bios version or reinstall windows.

{% hint style="warning" %}
After a lot of testing it seems that ASUS boards reset the Serial Number after computer restart when spoofing with DMI\_EDIT

Ensure that your serial number that you change stays after computer restart. (It's highly likely that it won't, and you'll have to follow this guide below.
{% endhint %}

## The Voodoo

This guide is specifically intended for **ASUS motherboards** that support the ability to **force downgrade via USB Flashback** to BIOS revisions from **April 2023** or earlier. For optimal results, it is strongly advised to downgrade to the **earliest compatible BIOS version** available, as this will provide the best compatibility for the process outlined here.

**Please ensure that your motherboard supports USB Flashback** and that you are working with a compatible BIOS version before proceeding. Following this guide on unsupported BIOS versions may result in undesirable outcomes, including failure to apply the modifications correctly.

{% hint style="info" %}
PLEASE MAKE SURE THAT YOU HAVE READ THIS. YOU MIGHT HAVE SUCCESS WITH IT EVEN IF YOU CANT DOWNGRADE, BUT I WOULDNT BET ON IT.&#x20;

\
EXAMPLE SERIALS ARE BELOW THE GUIDE!
{% endhint %}



For this you will need 4 things:&#x20;

1. The AFUWIN linked in the releases. It MUST be this version specifically.
2. DMI EDIT, also linked in the releases.
3. HxD.
4. The ability to follow instructions and use a brain.



You may also need to:

1. Disable Secure Boot
2. Enable CSM
3. Disable Fast Boot

## Step 1

Download and unzip AFUWIN, then open cmd as admin and insert the following commands:

1. `cd "AFUWIN path"`
2. `AFUWINx64.exe DUMP.rom /O`

Your mouse will stop working and everything will freeze besides the cmd. That's normal. After some time you will see the DUMP.rom in the directory.\
Create a copy of DUMP.rom, and name it SPOOF.rom. This is so you have a backup of a 100% working flash, in case of major issues. That is highly unlikely but possible, better to be safe than sorry.

## Step 2

Lets modify the System UUID first.

1. **Open DMIEdit**\
   Navigate to the **"\[Type 001] — System Information"** section in DMIEdit.
2. **Locate Your Current UUID**\
   Double-click on **"UUID"** to open the field.\
   Copy the value under **"Hexadecimal Value"** to your clipboard.
3. **Prepare HxD**\
   Open **HxD** hex editor and select SPOOF.rom\
   Press **CTRL + R** to open the "Replace" window.
4. **Set Up the Replace Window**
   * In the "Replace" window, set **Search for** to "Hex-values".
   * Paste your current UUID in the **"Search for"** field.
5. **Generate a New UUID**\
   You can use ChatGPT for this, randomise some numbers yourself also. However, try to **retain the first few numbers** of the original UUID and only modify the latter part, ensuring it still looks like a valid UUID. If you don't really care that much you can just auto generate one in DMI EDIT and use that.
6. **Replace the Old UUID with the New One**\
   Return to HxD, and in the **"Replace with:"** field, paste your new UUID.\
   Set **Search direction** to "All" and press **"Replace All"**.
7. **Save Your Changes**\
   Press **CTRL + S** to save the file with the updated UUID.
8. **IF YOU GET A WARNING THAT THE FILE SIZE HAS CHANGED YOU HAVE DONE SOMETHING WRONG. STOP THERE AND START AGAIN. MAKE A TICKET IF YOU ARE CONFUSED. DO NOT FLASH THAT BIOS.**

## Step 3

{% hint style="info" %}
Your new serial number must be the same length as the original. Again try to keep the starting numbers.
{% endhint %}

Now let's spoof the serial number.

1. **Locate the Current Serial Number**\
   In DMIEdit, go to **"\[Type 002] — Base Board/Module Information"**.\
   Double-click **"Serial Number"** and copy the value.
2. **Open HxD for Editing**\
   With your **bios.rom** file loaded in HxD, press **CTRL + R** to open the "Replace" window.
3. **Replace the Serial Number**
   * Set **Search for** to "Text-string" and paste your current Serial Number in the **"Search for:"** field.
   * In **"Replace with:"**, type a new Serial Number of the same length as the original (refer to the example above).
4. **Apply the Change**\
   Set **Search direction** to "All" and click **"Replace All"**.\
   Press **CTRL + S** to save the changes.

## Step 4

Repeat the above step for any other identifiers that you may have. It so happens that on my ASUS board I only have those 2, but you may have more. If you are unsure about which ones you need to change. Make a ticket and I will help you.

## Step 5

Once you've successfully modified all the necessary serial numbers for your board, the final step is to **flash** the updated BIOS to your system. This step is essential because it writes the changes directly to your system's firmware, making them permanent. Without flashing, the new serial numbers won't be stored, and your system will revert to using the old values.

From a technical standpoint, it seems that **ASUS stores two copies of each ID in the flash memory**. This could explain why the changes need to be written to the firmware and saved properly, without flashing, the IDs may not be updated correctly, and the system will restore the previous serials from a copy stored in the flash. That is just my theory, I'm not 100% sure why that is.

In any case, flashing the BIOS ensures that the changes are fully applied and stored, preventing any issues with persistent, outdated serial numbers.

{% hint style="info" %}
Once again a warning. If you at any point got the file size change warning in HxD. DO NOT FLASH.
{% endhint %}

1. Open cmd as admin and do `cd "AFUWIN directory"`
2. `AFUWINx64.exe SPOOF.rom /GAN`

Once you reboot, you should see that all your spoof serials have stuck. You can now carry on with the rest of the guide.\
You can even update your BIOS version again if you would like. There's not much reason to do so anyway though.

I'd also recommend restoring those BIOS settings we changed in step 1 to the settings you had, if you changed them. It will be required for some games as they enforce secure boot.



If you have any problems, reach me directly on Discord @exclusi0n or make a ticket.



{% hint style="warning" icon="megaphone" %}
This is just a example dump of a real ASUS SMBios that has never been modified.
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
