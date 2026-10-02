---
description: Written by @Fundryi/HWID-Privacy
icon: burst-new
---

# KingSpec SSD

{% hint style="danger" %}
Not tested personally by us.
{% endhint %}

Required:

{% file src="../.gitbook/assets/SSD_SERIAL_CHANGE_TOOL.zip" %}

* **A SATA-to-USB with ASMT 2115 Chipset**

***

### Steps to Follow:



1.  Plug the SSD into a USB adapter.<br>

    <figure><img src="../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>
2.  Plug the USB adapter into your SECOND PC (**NO ANTICHEAT SHOULD BE INSTALLED**).<br>

    <figure><img src="../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>
3. Open the SSDToolKits.exe (previously downloaded from the link in Prerequisites).
4.  Check the **top dropdown** to see if your SSD is detected. If not, redo all previous steps.<br>

    <figure><img src="../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>
5. Set your preferred information as follows:
   * **Firmware Version**: Use only numbers (FW Version).
   * **Model Name**: Use only letters and numbers, max 20 characters.
   * **Serial Number**: Maximum length is **TARGET SN LENGTH** (default: 13).
   * **WWN**: Not needed, but you can edit.
6. Click "Save".
7.  Press "Update".<br>

    <figure><img src="../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>


8.  When the program shows **PASS** in the top right corner, everything succeeded.<br>

    <figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>


9. You should now see your updated **Model Name, Firmware Version, and Serial Number**.
10. **Unplug the USB adapter** from the PC.
11. **Shutdown** your **MAIN PC**.
12. **Unplug** your **MAIN PC** **completely** (remove the power cable).
13. **Reinstall** the **NORMAL SSD** back into your **MAIN PC**.
14. **Power on** your **MAIN PC**.
15. Verify that your Model Name, Firmware Version, and Serial Number have been updated.
