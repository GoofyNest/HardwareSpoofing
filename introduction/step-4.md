---
description: Spoofing your Motherboard
icon: '4'
---

# Step #4

## 🧬 SMBIOS Spoofing Guide (Unfinished)

Work in progress, we are creating tools to make this step more automated

* Make sure to DUMP your factory looking serials, so you have a backup of your factory settings.
* You’ll need the [binaries](https://github.com/GoofyNest/HardwareSpoofing/releases/tag/release) listed in the referenced repo (⚠️ I did not create these binaries)
* After spoofing all SMBIOS fields, you must reinstall your Operating System
* Reinstall using a clean Windows ISO bootable USB
* Delete all partitions or destroy the RAID pool before reinstalling

{% hint style="danger" %}
Do not run AMIDEWIN or DMIEDIT while an anti-cheat system is active.

These tools load a kernel-mode driver to access and modify firmware-level data.

Running them while anti-cheat is open can trigger detections, crashes, or even result in a permanent ban from certain games.
{% endhint %}

{% hint style="warning" %}
You might get away skipping some steps, but don’t blame me if you get banned.

Follow everything carefully for a fully clean slate.
{% endhint %}

## Instructions (DMI\_EDIT)

* Restart PC (Make sure all games/anticheats are closed, uninstall vanguard if running)
* Download [DMI\_EDIT](https://github.com/GoofyNest/HardwareSpoofing/releases/download/release/DMI_EDIT.rar)
* Open `DMIEDIT.EXE`

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

* Press `File` -> `Save All` -> `original`

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
**DO THIS BEFORE CHANGING ANY VALUES, ITS ALWAYS GOOD TO HAVE A BACKUP OF UR ORIGINAL SERIALS**

**REMEMBER TO SAVE THIS FILE ON A USB DRIVE OR SOMEWHERE YOU CAN ACCESS IT AFTER REINSTALLING WINDOWS**
{% endhint %}

## **Follow one of the guides, depending on your Motherboard**

* [gigabyte.md](../smbios-data/gigabyte.md "mention")
* [asrock.md](../smbios-data/asrock.md "mention")
* [msi.md](../smbios-data/msi.md "mention")
* [asus.md](../smbios-data/asus.md "mention")

## Head to **System Information**

* Double check that ur **Manufacturer**, **Product Name**, **Version**, **SKUNumber**, **Family** is the correct values and has not been destroyed by other spoofers.
* Change `Serial Number` if it has unique serial number, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
* Change `UUID` I recommend copying your UUID to chatgpt and asking it to generate you a new legit `UUID v4` based of ur `factory UUID`.
* Press `Update` => `ALL` between all steps

## Head to **Base Board/Module Information**

* Double check that ur **Manufacturer**, **Product**, **Version**, **Asset Tag** is the correct values and has not been destroyed by other spoofers.
* Change `Serial Number` if it has unique serial number, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
* Press `Update` => `ALL` between all steps

## Head to **System Enclosure or Chassis**

* Double check that ur **Manufacturer**, **Version**, **Asset Tag** is the correct values and has not been destroyed by other spoofers.
* Change `Serial Number` if it has a Unique identifier, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
* Change `Asset Tag` if it has a Unique identifier, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
* Change `SKU Number` if it has a Unique identifier, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
* Press `Update` => `ALL` between all steps

## Head to **Processor Information**

* Make sure **Serial Number**, **Asset Tag**, **Part Number** is `Unknown` or `To Be Filled By O.E.M.` and does not have a unique identifier.
* Press `Update` => `ALL` between all steps

## Head to **OEM Strings**

* Make sure all `String #` does not have a Unique identifier, make sure they are `Default string`, `To Be Filled By O.E.M.` or `Unknown`
* Press `Update` => `ALL` between all steps

## Head to **System Configuration Options** (If you have it)

* Make sure all `String #` does not have a Unique identifier, make sure they are `Default string`, `To Be Filled By O.E.M.` or `Unknown`
* Press `Update` => `ALL` between all steps

## What to-do if crashing?

{% hint style="danger" %}
If you're experiencing issues with `DMI_EDIT`, try updating the segments one at a time, rather than all at once.

In some cases, a system restart may be required after updating a field.

If you're using a newer-generation ASUS or MSI motherboard, you may need a more recent version of `AMIDEWINx64`. Please check the release page for more versions\
\
Downgrading bios can also help
{% endhint %}

