---
description: Written by @Fundryi/HWID-Privacy
icon: ethernet
---

# Realtek NICs

{% hint style="danger" %}
I do not promote or condone spoofing onboard NICs, I added it here cause people was asking me to complete my guide.
{% endhint %}

{% hint style="danger" %}
Use at own risk, this has not been tested personally by us.
{% endhint %}

{% file src="../.gitbook/assets/realtek_efuse_prog.zip" %}

{% file src="../.gitbook/assets/RealTecNicPgW2.7.5.0.zip" %}

#### Programming Steps



1. You need a config file based of your NIC
2. The config file can be obtained by dry running the .exe first or/and when you download the correct NIC .cfg
3. Modify MAC Address:
   * Open `8168FEF.CFG` file
   *   Edit the first line to set your desired MAC address:

       ```bat
       NODEID = 00 E0 4C 88 00 18
       ;ENDID = 00 E0 4C 68 FF FF
       ```
4. Run the Programming Script:
   * Execute `WINPG64.BAT`
   *   A successful rewrite will show output similar to:

       ```bat
       ****************************************************************************
       *       EEPROM/EFUSE/FLASH Windows Programming Utility for                 *
       *    Realtek RTL8136/RTL8168/RTL8169/RTL8125 Family Ethernet Controller  *
       *   Version : 2.69.0.3                                                    *
       * Copyright (C) 2020 Realtek Semiconductor Corp.. All Rights Reserved.    *
       ****************************************************************************

       PG EFuse is Successful!!!
       NodeID = 00 E0 4C 88 00 18
       EFuse Remain 61 Bytes!!!
       ```
5. Verify MAC Address Change:
   * Open PowerShell
   * Run `ipconfig /all`
   * Look for your network adapter's Physical Address
   * It should match your programmed MAC address
