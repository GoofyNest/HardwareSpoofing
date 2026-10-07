---
description: Written by @goofy
icon: microchip
---

# Not for ASUS

Download tools: [Here](https://github.com/GoofyNest/Automatic-SMBIOS-Manager/archive/refs/heads/main.zip)

## Requirements

* Ability to open Powershell application
* Ability to extract files to a seperate folder
* Ability to paste 1 command
* Ability to click 1 button

Highly recommended to use a USB-flashstorage to have this files inside so you can always revert back to original serials.

***

## Step 1:

Download & Extract tools so they are in **Downloads/Automatic-SMBIOS-Manager-main**

***

## Step 2:

Open Powershell normally

<figure><img src=".gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

***

## Step 2:

Paste this command:

```powershell
cd "$env:USERPROFILE\Downloads\Automatic-SMBIOS-Manager-main"
```

<figure><img src=".gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

***

## Step 3

Paste this command:<br>

```powershell
powershell.exe -ExecutionPolicy Bypass -File .\spoof.ps1
```

<figure><img src=".gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

***

## Step 4 (<mark style="color:pink;">optional</mark>)

It is very highly recommended to disable UAC prompts

<figure><img src=".gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

Otherwise you will get a lot of spam.

***

The application should set everything automatically, if your motherboard is missing I recommend using the [add-mobo.ps1](https://github.com/GoofyNest/Automatic-SMBIOS-Manager/blob/main/add-mobo.ps1) and then add your motherboard to the **mobo.json** file.

***

## Step 5

When the correct settings are selected (should be automatic) you Press **"Continue"**

> If you get errors about Anticheats running please close the game/steam you are playing / uninstall vanguard, faceit

> We will not be providing a guide on how to uninstall the anticheats, you should know this yourself.

<figure><img src=".gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

It will ask you to make a backup always press **"Yes"**

A new prompt will appear:

<figure><img src=".gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

If you are scared press **"No",** the program will dump all the AMIDEWINx64.exe commands you can run manually if you dont trust the automation.

In this example we will be pressing **"Yes"**

Your computer might lag when the commands are running, this is normal.

You should see this in PowerShell when completed:

<figure><img src=".gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

## Step 6

Confirm you are spoofed by comparing Before and After.txt

<figure><img src=".gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

If you see serial numbers have changed, you are good to continue our guide.

## Step 7

Its highly recommended after you are done spoofing that you follow [reinstall.md](windows/reinstall.md "mention")
