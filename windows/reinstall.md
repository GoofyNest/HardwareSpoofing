---
description: >-
  You must always reinstall windows per ban, there is no getting away from this
  step.
icon: '1'
---

# Reinstall

### Operating system

{% hint style="warning" %}
You must have a working USB device minimum of 8GB of size
{% endhint %}

<mark style="background-color:$primary;">These ones are highly recommended to use</mark>

* [Windows 10](https://www.microsoft.com/en-us/software-download/windows10?msockid=3296b6ab2f5264701651a0622eaa6532)&#x20;
* [Windows 11](https://learn.microsoft.com/en-us/answers/questions/3895752/where-can-i-download-windows-11-iso)

***

### Rufus

1. [Open the **Rufus** website](https://rufus.ie/).
2. Click the link to download the latest version under the “Download” section.
3. Double-click the **Rufus** executable file to launch the tool.
4. Select the flash drive to create a Windows 10/11 bootable USB drive in the “Device” section.
5.  Click the **Select** button.<br>

    <figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>
6. Select the **Windows 10/11 ISO** file.
7. Click **Start**
8.  Check the **“Remove requirement for 4GB+ RAM, Secure Boot and TPM 2.0”** option to install version 25H2 on unsupported hardware.\
    <br>

    <figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>
9.  Check the **“Remove requirement for an online Microsoft account”**<br>

    <figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>
10. Select the **“Create a local account with username”** option, then specify the account name to install the operating system with a local account.\
    `user`
11. Check the **“Set regional options to the same values as this user’s”** option to use the current language as the default for new installations.
12. Check the **“Disable data collection”** option to prevent Microsoft from collecting certain data.
13. Check the **“Disable BitLocker automatic device encryption”** option.
14. Click the **OK** button.

***

### Finding your RAID driver

Google your motherboard manufacturer + motherboard product name on google

Example: Gigabyte B550 AORUS ELITE V2

<figure><img src="../.gitbook/assets/{F957BCD8-E79F-4E63-8391-58DA0ACEFC98}.png" alt=""><figcaption></figcaption></figure>

Go to Support ⇒ Driver

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

Select your Windows version if the website has it.

Search for Raid Driver

<figure><img src="../.gitbook/assets/{8B6702CC-E4F7-435C-9A3F-539B7669994C}.png" alt=""><figcaption></figcaption></figure>

Download and extract this to your freshly made WIndows USB in a folder called `Raid`

***

### Destroy raid array

<mark style="background-color:violet;">**Only for AMD**</mark>\ <mark style="background-color:violet;">**Only for specific motherboards**</mark>\ <mark style="background-color:violet;">**Check your Manufacturer website if your motherboard supports NVME raid 0**</mark>

{% hint style="info" %}
Skip if you are using a spoofable NVME
{% endhint %}

1. Restart pc
2. Press your BIOS key, if you dont know it google your manufacturer.
3.  Press F2 for **Advanced mode**

    <figure><img src="../.gitbook/assets/{EC639499-06FD-44C3-9830-0D735A1A11F3}.png" alt=""><figcaption></figcaption></figure>
4.  Click **Settings**

    <figure><img src="../.gitbook/assets/{C68C132B-C1AC-4673-8B2A-E5666DB61E59}.png" alt=""><figcaption></figcaption></figure>


5.  Click **IO Ports**

    <figure><img src="../.gitbook/assets/{7D28C49C-38E2-4009-8681-87D7F534E57E}.png" alt=""><figcaption></figcaption></figure>


6.  Click **Sata Configuration**<br>

    <figure><img src="../.gitbook/assets/{327ADE46-D20D-4E63-B3BF-3127496A238B}.png" alt=""><figcaption></figcaption></figure>


7.  Copy paste my settings<br>

    <figure><img src="../.gitbook/assets/{0085CF36-D1A0-49F6-A890-06275E6851D2}.png" alt=""><figcaption></figcaption></figure>


8. Save settings and restart PC (**First time only**)
9. Go into **BIOS again**
10. Navigate to Settings ⇒ IO Ports ⇒ You should now see **RAIDXpert2 Configuration Utility**
11. Press **Array Managment**<br>

    <figure><img src="../.gitbook/assets/{208F17E9-65D2-4771-A1DB-4509DBF1AE74}.png" alt=""><figcaption></figcaption></figure>


12. Click **Delete Array**\
    <i class="fa-wind-warning" style="color:$danger;">:wind-warning:</i> **`This will erase your files on your disks, this step should only be done when you have done all your spoofing`**<br>

    <figure><img src="../.gitbook/assets/{3263EF6E-556F-4D25-BD92-740A9529A6EF}.png" alt=""><figcaption></figcaption></figure>


13. Click **Create Array**<br>

    <figure><img src="../.gitbook/assets/{F236F00C-5EB3-4EFD-90AA-9ED8F6C315AB}.png" alt=""><figcaption></figcaption></figure>


14. Click **Raid Level**<br>

    <figure><img src="../.gitbook/assets/{B07EC599-EACB-493B-A2EB-3A4DCFD64510}.png" alt=""><figcaption></figcaption></figure>

    \
    Use RAIDABLE for 1 DISK raid setup\
    Use RAID 0 for multiple disk setup<br>
15. Click **Select physical disks**<br>

    <figure><img src="../.gitbook/assets/{56818BCC-2B27-4288-BA4C-4EF3EA4199A0}.png" alt=""><figcaption></figcaption></figure>


16. Click **Check All**<br>

    <figure><img src="../.gitbook/assets/{1510511D-2029-489C-96C0-1212564FACFA}.png" alt=""><figcaption></figcaption></figure>


17. Click **Apply Changes**
18. Click **Create Array**\
    <br>

    <figure><img src="../.gitbook/assets/{79CBBF08-B3C2-4F85-B4AF-7C1E3A65D89E}.png" alt=""><figcaption></figcaption></figure>


19. You are done with your Raid setup, nice!

***

### Installing Windows

1. Plug in your Windows USB you created
2. Restart PC
3. Hit your boot key\
   Normally F12 on Gigabyte\
   Normally F8 on ASUS, MSI
4.  Select the USB name partition 1<br>

    <figure><img src="../.gitbook/assets/{1B2BBC2E-EE78-4E60-95AF-8B8C299865DB} (1).png" alt=""><figcaption></figcaption></figure>


5.  Select your Windows language<br>

    <figure><img src="../.gitbook/assets/{5A523AD5-80DD-4E83-856A-CA1ED88E277D}.png" alt=""><figcaption></figcaption></figure>


6.  Select keyboard input<br>

    <figure><img src="../.gitbook/assets/{EC4CDE37-DEE4-48C7-8F95-50692BCA0BE4}.png" alt=""><figcaption></figcaption></figure>



1.  Click **I dont have product key**<br>

    <figure><img src="../.gitbook/assets/{BEA36942-60F2-456A-8877-CFE37A75017E}.png" alt=""><figcaption></figcaption></figure>


2.  Select first option<br>

    <figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>


3.  Agree to having no privacy<br>

    <figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>


4.  A preview of disks you can install Windows on, DO not select one<br>

    <figure><img src="../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>



***

### Removing partitions (<mark style="color:$primary;">Skip if using RAID setup</mark>)

Press delete on every partition until you only have 1 Disk, 1 Partition and the full disk size is available.

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

^ This is how its suppose to look if you did it correctly.

***

### Loading raid driver (<mark style="color:$primary;">Skip if using spoofable NVME</mark>)

1.  Click Load Driver<br>

    <figure><img src="../.gitbook/assets/{00ADFE27-9169-4779-A3A0-8C4CF128918E}.png" alt=""><figcaption></figcaption></figure>


2.  Select the **NVME\_CC ⇒ AMD-RAID Bottom Device (rcbottom.inf)**<br>

    <figure><img src="../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>


3. Click Load Driver
4. Accept the Terms of service shit
5.  Select **NVME\_DID** ⇒ **AMD-RAID controller \[storport] (rcraid.inf)**<br>

    <figure><img src="../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>


6. Click Load Driver
7.  **NVME\_CC** ⇒ **AMD-RAID Config Device (rccfg.inf)**<br>

    <figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>


8.  Now your raid array should show up in Windows<br>

    <figure><img src="../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>



***

### Finishing up

1.  Install<br>

    <figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
When the text appears which says "Your PC is re-starting soon" un-plug your USB to avoid leaking banned USB disk serial on your freshly installed PC.
{% endhint %}

Enjoy fresh gaming!
