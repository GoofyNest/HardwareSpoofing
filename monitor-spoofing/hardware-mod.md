---
description: Found with research by @Goofy
icon: burst-new
---

# Hardware mod

{% embed url="https://blurbusters.com/zero-motion-blur/hardware-mod/" %}

### ⚠️ Warning

This is **not** a software override. It involves:

* Opening the monitor casing
* Desoldering or cutting a physical pin on the EDID EEPROM chip
* Reflashing the EEPROM with a modified EDID binary
* Voiding the warranty, with real risk of permanent damage or injury

**Proceed at your own risk.**

***

### Why Do This?

Modern tools like [hdmi-edid-emulator-adapter.md](hdmi-edid-emulator-adapter.md "mention")[dr-hdmi.md](dr-hdmi.md "mention")[dichen-5.md](dichen-5.md "mention") is all working however most of them lack something very important.

Keeping your monitor 4k res with max refresh rate.

On your monitor there is a _DVI I2C EEPROM chip an Atmel 24C02C_

There is normally 1 for DVI, 1 for HDMI and maybe even one for display-port.

***

## The guide

**1. Get organized.** You will need a Philips screwdriver. A soldering iron is highly recommended, however, an ultra-sharp large utility knife blade (fresh, new ‘exacto’ type blade) will also work if you are extremely careful (an accidental slip will do a lot of damage).

Make sure your work area is washed/cleaned, as you don’t want dirt getting into your monitor innards. You will be temporarily removing screws, so do not lose them! Get a few sandwich bags, small containers, or several cups, to store loose parts in.

**2. Make sure you don’t have static electricity.** Touch a grounded metal object (e.g., the metal surface at the back of your computer). Also, make sure your monitor has been unplugged for at least 15 minutes, so there’s no charge left in your monitor’s capacitors.

**3. Remove the plastic casing from the monitor.** This is called “de-bezelling” your monitor, which surround monitor users often do in order to reduce the gap between monitors during surround mode.

**4. Lay the the screen face down carefully**, with the metal rear of the monitor facing upwards. Make sure your surface is clean and completely clear of debris, so it does not scratch or damage the glass of your monitor.

<figure><img src="../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

**5. Remove the metal cover.** Do this by carefully removing all _tape pieces_ surrounding the large protruding metal cover (tape may be silver color instead of black). Then unscrew all _4 screws near video connectors_. And then _disconnect the speaker cable_. Once done, you can carefully lift the metal cover, revealing the green circuit board underneath:

<figure><img src="../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

**6. Unscrew the circuit board.** Remove the two screws that hold the main circuit board. Upon doing this, you can now see the chips sitting on your monitor circuit board.

<figure><img src="../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

**7. Find the correct EDID chip for DVI.** See attached image, with circle. The correct chip you want is immediately behind the DVI connector. It is a tiny 8-legged chip, and says “ATML” on it as the first few letters. _For the electronics geeks, this is the DVI I2C EEPROM chip, an Atmel 24C02C. There are two of them, one for HDMI, and one for DVI. However, we only need to modify the one for DVI._

<figure><img src="../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

**8. Disconnect the Write Protect Pin of the chip.** This is pin #7 of the Atmel chip. If you have the DVI port facing towards you, this leg is third from left. _Tip for Electronics newbies: Pin numbers are often_ [_counted counterclockwise from pin #1_](https://en.wikipedia.org/wiki/Dual_in-line_package#Orientation_and_lead_numbering) _indicated by a white dot on the chip. If you have the same chip as in the screenshot, the correct pin will be on the opposite edge as the white dot, and be right above the label “ATML”_

<figure><img src="../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

_Soldering Iron Method:_ The use of a electronics soldering iron, with a thin tip, is recommended. Heat the pin just enough until the solder melts, and bend the pin upwards using the soldering iron’s tip (or another pointy metal tool). Do not overheat.

_Utility/Exacto Knife Method:_ This method is accident prone, and easily does accidental damage. However, it works if you are careful with the knife method. Use a fresh, new utility kife blade. Carefully and slowly, with light pressure, cut pin #7, by sawing through it gently until it cuts through. Gentle cutting is less accident prone than a hard push (where a sudden slip accident can sever multiple circuits). Use a very sharp, fresh blade, so it is easy to cut the pin with just light pressure, minimizing the chance of a “slip” accident.

_Note for Electronics Geeks: The ATMEL 24C02C datasheet says the pin should ideally be connected to ground, however, leaving the pin unconnected works too._

**9. You’re Done.  Reassemble the monitor.** Reattach the circuit board (2 screws), reattach the metal cover (4 screws and tape, use new tape if necessary), and reassemble casing if desired (or keep it de-bezelled, during surround use).

***

Now you should be able to just write EDID to your monitor and it should just accept it and identify to whatever you want.

{% embed url="https://www.monitortests.com/forum/Thread-EDID-DisplayID-Writer" %}
