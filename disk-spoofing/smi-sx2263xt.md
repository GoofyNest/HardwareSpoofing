---
description: Thanks to @lena6168 at discord
icon: '1'
---

# SMI SX2263XT

### Changing serial number and ouid (euid64) on SMI SX2263XT-based NVMe SSDs <a href="#changing-serial-number-and-ouid-euid64-on-smi-sx2263xt-based-nvme-ssds" id="changing-serial-number-and-ouid-euid64-on-smi-sx2263xt-based-nvme-ssds"></a>

This manual covers how to change all IDs on a NVMe SSD built on SMI SM2263XT controller, including OUID (EUID64).

<mark style="color:$danger;">CAUTION</mark>\
This manual covers how to alter the firmware of your SSD drive. This might lead to permanent damage to your drive or its failure. Prepare yourself a drive you don't mind bricking - cheap chink C-grade drives are 30-40$ these days, cheap enough to learn how to fuck around with them.

My drive has SMI S2263XT controller and all further manual will be specific to this controller. Though, generally, the approach from this manual is valid for any SSD - if you know what you are doing.

***

#### Part 0. Install a Windows on a different drive <a href="#part-0-install-a-windows-on-a-different-drive" id="part-0-install-a-windows-on-a-different-drive"></a>

Install Windows to a SATA drive, Win 10 is preferred. You will need it to install it to a SATA drive because you'll be installing a specific NVMe drivers and booting with your NVMe in ROM mode that will prevent your system from normally working with these SSDs.

***

#### Part 1. Figuring out your SSD controller <a href="#part-1-figuring-out-your-ssd-controller" id="part-1-figuring-out-your-ssd-controller"></a>

Controller is a chip that runs small program called firmware, that regulates how system interats with your drive and, most importantly, holds identification information. It's usually located somewhere near M2 connector, few examples are below:

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

Sometimes it's located under vendor's sticker:

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

<mark style="color:$danger;">Removing/damaging the sticker usually voids the warranty. To avoid this, disconnect your NVMe from the system and warm it up to 60-70 degrees with a blowdryer or something (don't worry, it won't damage it) - that will soften the glue and you will be able to gently lift the sticker to look at its controller.</mark>

Sometimes chink OEM makers mill the controllers to remove any possibility to identify them. Then your controller looks like a blank chip, sometimes with visible milling paths. In this case, you'll have to rely on information from hwinfo or the Internet.

My drive has SMI S2263XT controller, this means I will need SMI's MP Tool (MP stands for Mass Production) - a special software used in factories to flash SSDs on conveyor amounts.

***

#### Part 2. Figuring out memory type of your SSD <a href="#part-2-figuring-out-memory-type-of-your-ssd" id="part-2-figuring-out-memory-type-of-your-ssd"></a>

Properly figuring out your memory type is crucial to properly flash your SSD. Depending on circumstances, makers might change memory suppliers even between different batches of one SSD model, so there's no "press X to win".

For SMI controllers, you'll want to download a utility that queries SSD for information about its memory chips. There are few options, but one of most common [is the utility made by Vadim "vlo"](http://vlo.name:3000/tmph/smi_nvme_flash_id.rar). This utility also requires a special driver, the utility maker has conveniently provided these [drivers here](http://vlo.name:3000/tmph/smi_nvme_drv.rar).

Start with installing drivers: unarchive the drivers archive, right click on `nvme_MP.inf` file and click "Install"

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

Once installed, reboot your system and unarchive the flash\_id utility. Run it as administrator.

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

Once running, the utility will display a console window with a list of detected drives. Select your target drive by pressing corresponding number on your keyboard and press enter. Utility will display technical details, you'll want to save these for further use.

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

***

#### Part 3. Find your MP tool <a href="#part-3-find-your-mp-tool" id="part-3-find-your-mp-tool"></a>

Depending on your controller and memory type, find a corresponding MP tool from your vendor. Those tools are never officially released by vendors as they're intended for in-house use. Thanks to our chink friends from factories where the SSDs are produced, we can find those tool on enthusiasts websites. You can find MP Tool for SMI SM2263XT [on this website](https://www.usbdev.ru/files/smi/sm2263xtmptool/).

Take memory type you've noted in the previous step and find corresponding MP Tool version on the website. On this particular website tools are organized per memory types. As our particular SSD is built on Micron 176L (B47R) memory, you will want to look at B47R category. You will need to test every tool from your category to find one that suits your particular SSD because these tools are leaked from different manufacturers and even though their products are based on the same controller and memory, their internal architecture might be different and thus tool leaked from maker "A" might not work for maker "B", etc. You get the idea.

<figure><img src="../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

For my particular SSD, `SM2263XT_Micron_B47R_T_PKGX0304_FWX0304B0.rar` works great.

\
Download the tool and unarchive it.

***

#### Part 4. Boot up with your SSD in ROM mode <a href="#part-4-boot-up-with-your-ssd-in-rom-mode" id="part-4-boot-up-with-your-ssd-in-rom-mode"></a>

ROM mode is a special mode of NVMe SSD that allows altering its firmware. Usually its achieved by shorting two pin holes on drive's board.

Prepare yourself a piece of wire with two exposed ends or a pair of metal tweezers. Also, set up your BIOS in a way that it will boot up to Windows installed on SATA drive in case you have several operating systems installed.

Turn off your PC and find your NVMe. Locate your ROM pin holes, usually they're located at the end of the SSD board or on its side as a pair of pin holes. Sometimes, one pin hole has square lithography pattern around it and the other has round pattern. Sometimes both ROM pinholes have round lithography pattern.\
Some vendors print pin names by their sides:

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

If you are unsure what are your ROM pins, DO NOT short random pins - this might cause electrical shock and permanent damage to your SSD. Instead, look up information on the Internet - most likely, some enthusiasts have already figured what pins are in charge of ROM mode.

Once you have located ROM pins - short them with a pair of tweezers or piece of wire and turn on your PC. Keep pins shorted until your OS fully boots up. Once booted, you can release the pins - the SSD will stay in ROM mode until next reboot.

***

Once running, the utility will display list of compatible detected SSDs. Check that your target SSD has booted in ROM mode.

<figure><img src="../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

Go to "Parameter" tab and press "Edit config". The utility will promt a password - the password is " " `two spaces, without quotes`.

Once config page is unblocked, press "Auto" by "Flash Select" dropdown, the utility will auto-detect your memory type. Always check auto-detected memory type against actual memory type from `Step 2` to avoid bricking your SSD.

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

Next, update your IDs to desired values. Don't null your serials. The best approach is to look up a real SSD on the Internet, and take its IDs as example - name, serial, model, etc. Paste example serial to the "Begin SN", "End SN" and "SN Mask" fields and delete last few characters. In "Begin SN" replace deleted characters with 0's and in "End SN" replace deleted characters with 9's. In "SN Mask" put mask symbols (`###### symbols`) instead of deleted characters, and the utility will generate a random serial within your mask.

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

You will want to also edit your Extension Identifier and OUI - those stand for OUID (EUID64), that are displayed by `get-disk | select serialnumber` command. Those are usually non-editable in most of controllers, so it's crucial to change these values for spoofing, if they're available. For my particular SSD, `Extension Identifier` and `OUI` fields are responsible for resulting EUID64.

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

Once filled all the values, you might want to save your config to do the whole thing faster the next time. To do this, press "Save Config As" and save your config. To select your config, click on "Config List" dropdown and choose your config.

Once done, press "Save" - the configuration page should go back to locked state. Double check that values have not changed after this (these utilities tend to have buggy saving functionality), If changed - fix them by pressing "Edit config" again.

After saving your config, go back to "Main" tab and press "Start". The flashing process will start.

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

Once successfully flashed, your SSD will change its state to "ISP" (usual work mode) and the utility will print updated info about the disk.

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

Once done, you will want to install a fresh Windows on your freshly flashed SSD.

You're done spoofing your SSD! Hooray!
