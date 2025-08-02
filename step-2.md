# 🧬 SMBIOS Spoofing Guide (Unfinished)
Work in progress

- Make sure to DUMP your factory looking serials, so you have a backup of your factory settings.
- You’ll need the [binaries](https://github.com/GoofyNest/HardwareSpoofing/releases/tag/release) listed in the referenced repo (⚠️ I did not create these binaries)
- After spoofing all SMBIOS fields, you must reinstall your Operating System
- Reinstall using a clean Windows ISO bootable USB
- Delete all partitions or destroy the RAID pool before reinstalling

> [!CAUTION]
> Do not run AMIDEWIN or DMIEDIT while an anti-cheat system is active.
>
> These tools load a kernel-mode driver to access and modify firmware-level data.
>
> Running them while anti-cheat is open can trigger detections, crashes, or even result in a permanent ban from certain games.

> [!WARNING]
> You might get away skipping some steps — but don’t blame me if you get banned.
> 
> Follow everything carefully for a fully clean slate.

# Instructions (DMI_EDIT)
- Restart PC (Make sure all games/anticheats are closed, uninstall vanguard if running)
- Download [DMI_EDIT](https://github.com/GoofyNest/HardwareSpoofing/releases/download/release/DMI_EDIT.rar)
- Open `DMIEDIT.EXE`
- <img width="521" height="212" alt="image" src="https://github.com/user-attachments/assets/4fa378f3-5dc8-4601-9b63-5bcf665753eb" />
- Press `File` -> `Save All` -> `original`
- <img width="364" height="128" alt="image" src="https://github.com/user-attachments/assets/d528c076-3b06-4450-9a12-49ba6257c49b" />
- <img width="567" height="470" alt="image" src="https://github.com/user-attachments/assets/6a3e408e-4854-4a45-a33c-87240497b4ac" />

> [!CAUTION]
> DO THIS BEFORE CHANGING ANY VALUES, ITS ALWAYS GOOD TO HAVE A BACKUP OF UR ORIGINAL SERIALS
>
> REMEMBER TO SAVE THIS FILE ON A USB DRIVE OR SOMEWHERE YOU CAN ACCESS IT AFTER REINSTALLING WINDOWS

# **Follow one of the guides, depending on your Motherboard**
- [ASRock](https://github.com/GoofyNest/HardwareSpoofing/blob/main/Factory-ASRock.md)
- [ASUS](https://github.com/GoofyNest/HardwareSpoofing/blob/main/Factory-ASUS.md)
- [Gigabyte](https://github.com/GoofyNest/HardwareSpoofing/blob/main/Factory-Gigabyte.md)
- [MSI](https://github.com/GoofyNest/HardwareSpoofing/blob/main/Factory-MSI.md)

# Head to **System Information**
- Double check that ur **Manufacturer**, **Product Name**, **Version**, **SKUNumber**, **Family** is the correct values and has not been destroyed by other spoofers.
- Change `Serial Number` if it has unique serial number, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
- Change `UUID` I recommend copying your UUID to chatgpt and asking it to generate you a new legit `UUID v4` based of ur `factory UUID`.
- Press `Update` => `ALL` between all steps

# Head to **Base Board/Module Information**
- Double check that ur **Manufacturer**, **Product**, **Version**, **Asset Tag** is the correct values and has not been destroyed by other spoofers.
- Change `Serial Number` if it has unique serial number, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
- Press `Update` => `ALL` between all steps

# Head to **System Enclosure or Chassis**
- Double check that ur **Manufacturer**, **Version**, **Asset Tag** is the correct values and has not been destroyed by other spoofers.
- Change `Serial Number` if it has a Unique identifier, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
- Change `Asset Tag` if it has a Unique identifier, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
- Change `SKU Number` if it has a Unique identifier, **ignore to change** if its `blank`, `Default string`, `System Serial Number` or `To Be Filled By O.E.M.`
- Press `Update` => `ALL` between all steps

# Head to **Processor Information**
- Make sure **Serial Number**, **Asset Tag**, **Part Number** is `Unknown` or `To Be Filled By O.E.M.` and does not have a unique identifier.
- Press `Update` => `ALL` between all steps

# Head to **OEM Strings**
- Make sure all `String #` does not have a Unique identifier, make sure they are `Default string`, `To Be Filled By O.E.M.` or `Unknown`
- Press `Update` => `ALL` between all steps

# Head to **System Configuration Options** (If you have it)
- Make sure all `String #` does not have a Unique identifier, make sure they are `Default string`, `To Be Filled By O.E.M.` or `Unknown`
- Press `Update` => `ALL` between all steps

# What to-do if crashing?
> [!CAUTION]
> If you're experiencing issues with `DMI_EDIT`, try updating the segments one at a time, rather than all at once.
>
> In some cases, a system restart may be required after updating a field.
>
> If you're using a newer-generation ASUS or MSI motherboard, you may need a more recent version of `AMIDEWINx64`. Please check the release page for more versions
