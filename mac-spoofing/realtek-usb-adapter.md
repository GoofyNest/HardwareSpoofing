---
description: Thanks to @lena6168 at discord
icon: '1'
---

# Realtek USB adapter

Are you planning to purchase "spoofable" USB network card? Read this before you do. Cheap ass 10$ dongle from Temu might work just as good as "spoofable" network cards sold for hundreds of dollars.

Every USB network card from literally any brand is most likely based on controllers from these three makers: Realtek, ASIX, SMSC. We'll take a general look on spoofing those and then spoof a real Belkin USB-C Network Adapter built on top of a Realtek controller.

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

Generally, every USB NIC runs off a controller - a special chip that runs firmware providing the device with actual NIC functionality. This firmware is stored in ROM - memory chip, that's available for write operations only in factory environments. Thanks to our chink friends leaking to public everything they touch, we can simulate that factory environment by just running firmware flashing software on our PC. Generally, your actions would look like:

* Google "%my usb network card name% controller" - look up which controller does your dongle use.\
  If you can't find any info - look up the USB NIC in your Device Manager,. If it did not require a specific driver, most probably it's running off a generic PnP Windows driver and is presented as "Realtek Family GbE Ethernet Controller" or so.
* Google up what software is used to flash these controllers. Keywords for the search: "flashing software/firmware", "mp tool" (mp is short for Mass Production"), "pg tool" (pg is short for Program Generation).
* Prepare a device you don't mind bricking - usually, these programs are not built with "press X to win" principle, but rather pretty complicated with lots of untold context, providing a low-level access to the controller. You can easily mess up the firmware to the point where your USB NIC will be bricked, especially if you don't have experience in messing with low-level controllers.\
  Most likely, you will find a program on some fishy-looking website or a chink github repo, so I'd recommend sandboxing the app while you are exploring it.

Once you've found out how to use the software - you're looking to change:

* MAC Address - absolute must. If you are not able to change the MAC Address, it's not worth continuing.
* Serial number - if present. Anticheats tend to fingerprint everything they can reach - even if it's just a NIC, doesn't mean your AC will only log its MAC Address.
* Firmware version/date - if present, at your caution. If you don't look to "officially" update the FW of your USB NIC in the future, you can freely mess with these values. If you are considering actually updating the FW - either update it first and then spoof the values, or don't mess with FW version/date at all - these values are still used for fingerprinting the device, but they are not unique to your particular device. Messing up FW version/date might lead to you being unable to update your USB NIC in the future.

Now, with a real-life example:\
I've got myself a Belkin USB-C to Ethernet Adapter from my work (I always forget to return these after I travel to our datacenter from our office, so I have plenty of these at home XD), I've found out it's built on Realtek RTL8153 controller.

***

So, to spoof a RTL8153-based USB NIC you'd need to:

* Download Realtek RTL8153 & RTL8152B PGTool Utility Version 2.0.26.0 [https://www.station-drivers.com/index.php/en/component/remository/Drivers/Realtek/Lan/RT\[…\]and--RTL8152B-PGTool-Utility-Version-2.0.26.0/lang,en-gb/](https://www.station-drivers.com/index.php/en/component/remository/Drivers/Realtek/Lan/RT\[%E2%80%A6]and--RTL8152B-PGTool-Utility-Version-2.0.26.0/lang,en-gb/)
* Disconnect the target USB NIC from the network (unplug Ethernet cable).
* Run the tool, press SEARCH button on the top. It will enumerate all compatible USB NICs. Select the device you are looking to spoof.
*

    <figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>


* Press Dump button, the tool will read device's firmware. Once done, you'll be displayed with a huge check mark and the tool will print firmware details.
*

    <figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

    Note that after successful dump, the tool will populate MAC ADDRESS->CURRENT field with your current MAC Address and MINIMUM and MAXIMUM fields. You will want to copy those.
* Select "Program NODEID only" in "Program Item" dropbox and paste your MAC Address from the previous step. At this point, edit your MAC Address to a random hexadecimal value. Press "Program".
*

    <figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

    Generally, you will want to have your new MAC address within MIN/MAX bounds from the previous step. These limits represent what MACs are expected from your device model. You can as well set your MAC to absolutely random hex value outside these bounds, but this might be a red flag for your anticheat.

Once done, reboot and check your NIC MAC Address with powershell:\
`Get-WmiObject win32_networkadapterconfiguration | select description, macaddress`

