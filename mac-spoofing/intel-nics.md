---
description: Written by @Fundryi/HWID-Privacy
icon: burst-new
---

# Intel NICs

{% hint style="danger" %}
Not tested personally by us.
{% endhint %}

{% file src="../.gitbook/assets/EEupdate_5.35.12.0.zip" %}

#### Setup Steps

1. Create Bootable DOS USB:
   * Download Rufus ([https://rufus.ie](https://rufus.ie/))
   * Insert your USB drive
   * Select "MS-DOS" as the boot selection
   * Create the bootable drive
2.  Prepare Files:

    * Copy EEUPDATE.exe to your bootable USB
    * Create changemac.bat with the following content:



    ```bat
    @echo Off
    echo Update your current mac?
    pause
    echo Current MAC
    Eeupdate.exe /NIC=1 /MAC_DUMP
    echo Updating MAC
    Eeupdate.exe /NIC=1 /mac=REPLACEMEWITHMAC
    echo Updated MAC
    Eeupdate.exe /NIC=1 /MAC_DUMP
    echo If the above did not work type the following manually:
    echo EEUPDATE /NIC=1 /mac=REPLACEMEWITHMAC
    echo EEUPDATE /NIC=1 /MAC_DUMP
    echo Last command will display the current MAC(if it worked, should display new one)
    pause
    ```

* Example MAC: `AA:BB:CC:DD:EE:11`
  * Do not use this mac, it will brick your network...

3. BIOS Setup:
   * Enter BIOS (usually F2 or Delete key during startup)
   * Disable Secure Boot
   * Enable CSM (Compatibility Support Module) mode
   * Save changes and restart

***

#### Running the Script

1. Boot from USB:
   * Insert the USB drive
   * Boot into DOS (may require selecting boot device during startup)
   * At the DOS prompt (A:> or similar)
   * Type the first few letters of "changemac" and press TAB
     * In DOS, TAB will auto-complete the filename
     * Press Enter to run the script
   * Follow the prompts
2.  Manual Commands (if script fails):<br>

    ```
    EEUPDATE /NIC=1 /mac=AABBCCDDEE11
    EEUPDATE /NIC=1 /MAC_DUMP
    ```
3. After Completion:
   * Remove the USB drive
   * Restart the system
   * Boot back into Windows to verify the change
   * Revert your secure boot and CMS settings.

***

#### Important Notes

* Replace `AABBCCDDEE11` with your desired MAC address
* Keep your original MAC address noted down
* The `/NIC=1` parameter targets the first network adapter
  * If you have multiple make sure either to change both or disable the one you dont need/use.
  * `EEUPDATE /LIST_NIC` will list you the NIC's installed.
* Some systems may require specific versions of EEUPDATE
* Not all Intel NICs support MAC address modification
* Incorrect MAC address format can cause network issues
