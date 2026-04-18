---
description: 'DICHEN 5 GEN FUSER - MODEL: DC240HZ5D-2'
icon: '1'
---

# Dichen 5

<mark style="color:purple;">**It is very annoying to get the spoofing for Dichen 5 to work properly**</mark>

{% hint style="warning" %}
You need the Dichen fuser that has the programmable port
{% endhint %}

<figure><img src="../.gitbook/assets/image (19).png" alt="" width="375"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (20).png" alt="" width="375"><figcaption></figcaption></figure>

<mark style="color:purple;">Dichen comes with a USB-C programmable port that is using to flash EDID files to your Fuser, this port is normally only utilized if your fuser does not automatically support your monitor itself.</mark>

The guide I found working was from [Phoenix-DMA](https://phoenixdma.com/dichen-6th-gen-hdmi-setup/?srsltid=AfmBOoq7nSsI_g_wnKhGIfPVLoH6qzl4yM36B1ax8OEHarLj5d3jnrXJ), however they do not cover how to spoof monitor serials and that something I will walk you through.

{% hint style="danger" %}
If you are doing this on your gaming-pc you will have to reinstall after doing this.
{% endhint %}

I recommend doing this from a secondary pc like a Laptop for example.

## Step 1

Unplug all your monitors from the Fuser and plug in the USB-C connector and power to your pc.

<figure><img src="../.gitbook/assets/image (21).png" alt="" width="375"><figcaption></figcaption></figure>

Plugin your monitor to your Graphics card using HDMI or DPI, does not matter.

## Step 2

Download the [Dichen Programming zip](https://mega.nz/folder/aNcFVLpR#B40bYCE3cmLwnXs2gxQ69g) and extract it to a folder.

Also install the CH driver from the folder so you can re-program the Dichen fuser.

## Step 3

Download [Custom Resolution Utility](https://customresolutionutility.net/#download-custom-resolution-utility) and extract it.

* Run Reset.exe
* Change your refresh rate back to what you always have
* Open CRU.exe



**Follow this:**

* In the drop-down list at the top left, select each monitor (including inactive ones)
* Click Edit (top right)

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

🔹 Device ID Section

* ID: Leave as default
* ID Serial #: Clear the field until the box is empty

🔹 Serial Number Section

* Clear the field until the box is empty
* Check “Include if slot available”
* Click OK

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

After this is completed, do Export and you will get a **.bin** file that you can flash to your Fuser.

## Step 4

Open the EDID Flash Tool.exe and follow below:

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

Very important to pick the right **COM** port, you can check in device manager the Fuser should appear as **CH** something.\
\
Also very important to set your targeted Resolution.

1. <mark style="color:yellow;">**YELLOW**</mark><mark style="color:yellow;">:</mark> Select the COM port for the dichen fuser, this can be found in device manager under ports (COM).
2. <mark style="color:blue;">**BLUE**</mark><mark style="color:blue;">:</mark> Select your target resolution
3. <mark style="color:$success;">**Green**</mark><mark style="color:$success;">:</mark> Check the radio button the the RIGHT and then click the button that enables after checking the radio button. Locate your monitor file you saved from able and open it in DC Injector.&#x20;
4. <mark style="color:$danger;">**RED**</mark><mark style="color:$danger;">:</mark> Click this button last to send the EDID to the fuser.

Some Chinese Mao Zedong message should appear if done.

<figure><img src="../.gitbook/assets/image (25).png" alt="" width="375"><figcaption></figcaption></figure>

## Step 5

Unplug your monitor from GPU and setup the monitor through the Fuser box again.

Open the **Custom Resolution Utility** extracted folder and run **reset.exe**

Restart your PC and run this to verify that your serial is NULL:

```powershell
Get-CimInstance -Namespace root\wmi -ClassName WmiMonitorID | ForEach-Object {
    [PSCustomObject]@{
        Manufacturer = ($_.ManufacturerName -ne 0 | ForEach-Object {[char]$_}) -join ""
        Model        = ($_.UserFriendlyName -ne 0 | ForEach-Object {[char]$_}) -join ""
        SerialNumber = ($_.SerialNumberID -ne 0 | ForEach-Object {[char]$_}) -join ""
    }
}
```

If they appear as **null** or all **0's** you are fine.
