---
description: Written by @Fundryi/HWID-Privacy
icon: burst-new
---

# Realtek NICs

{% hint style="danger" %}
Not tested personally by us.
{% endhint %}

{% file src="../.gitbook/assets/realtek_efuse_prog.zip" %}

{% file src="../.gitbook/assets/RealTecNicPgW2.7.5.0.zip" %}

#### Programming Steps

1. Modify MAC Address:
   * Open `8168FEF.CFG` file
   *   Edit the first line to set your desired MAC address:

       ```bat
       NODEID = 00 E0 4C 88 00 18
       ;ENDID = 00 E0 4C 68 FF FF
       ```
2. Run the Programming Script:
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
3. Verify MAC Address Change:
   * Open PowerShell
   * Run `ipconfig /all`
   * Look for your network adapter's Physical Address
   * It should match your programmed MAC address
