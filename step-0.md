# What Are Hardware Bans?
Hardware bans are used by many anti-cheat systems to block repeat offenders from accessing a game or platform. Instead of just banning a user account, they ban the hardware itself specifically, they target unique serial numbers tied to different components of your system.

# What Is a Serial Number?
A serial number is a unique identifier assigned to a piece of hardware by its manufacturer. It’s primarily used for things like warranty claims, tracking, and inventory. Think of it as a digital fingerprint for each component you own.

# Examples of Hardware/Modules
- Motherboard unique serial numbers
- Trusted Platform Module (TPM)
- Monitor serial number
- RAM serial number
- MAC address (network interface)
- Disk drive serial number (HDD/SSD)
- Windows unique identifiers (Product ID, SID, etc.)
- Peripheral serial numbers (e.g., mouse, keyboard, headset)

# Why This Matters
Anti-cheat systems use these serial numbers to identify and ban players who are caught cheating. But this approach comes with serious downsides:
- Innocent people may unknowingly buy used or refurbished PCs that have banned components.
- Once a component is banned, it may be banned forever, even if it changes hands.
- There is no standard process for lifting these bans, which means people are locked out of games for hardware they didn’t misuse.

# What is Spoofing?
Spoofing is the act of faking or disguising something to trick a system, person, or software into thinking it's something else. In the context of computers and gaming, it usually refers to faking hardware or network identifiers to bypass bans, restrictions, or tracking systems.

# Two Types of Spoofing
There are two common forms of spoofing used in the context of bypassing hardware bans:

### 1. Temporary Spoofing
- What it does: Changes serial numbers or identifiers only while the system is running.
- Examples: Spoofing disk serial numbers, MAC addresses, or BIOS data in memory.
- Reverts on reboot: All changes are lost when the computer is restarted.
- Common in: Public spoofers or tools used for short-term ban evasion.

### 2. Permanent Spoofing
- What it does: Permanently modifies hardware identifiers stored in firmware.
- Tool used: Programs like AMIDEWIN can rewrite SMBIOS data such as:
  - Motherboard serial number
  - System UUID
  - Asset tags
- Persists after reboot: Changes remain until manually reset or reflashed.
- Used by: OEMs during production but also by advanced users to reset banned hardware.


# What Is AMIDEWIN?
AMIDEWIN is a legitimate utility developed by American Megatrends Inc. (AMI) one of the world’s leading BIOS/UEFI firmware vendors. It's primarily used by OEMs (Original Equipment Manufacturers) and system builders to read and write SMBIOS data on a motherboard.

# What Is SMBIOS Data?
SMBIOS (System Management BIOS) contains important system information that your operating system and diagnostic tools rely on. This includes:
- Motherboard serial number
- System UUID
- BIOS version
- Asset tags
- OEM branding
- Product and manufacturer name

This data is stored in a part of the firmware and can be accessed by tools like AMIDEWIN.

# What Is AMIDEWIN Used For?
AMIDEWIN is used to modify SMBIOS data during factory setup or system recovery. Typical uses include:
- Assigning serial numbers during manufacturing
- Injecting UUIDs for system tracking or licensing
- Standardizing brand information across a product line
- Correcting corrupted BIOS info after board replacement or repair

It's often used in factory automation e.g., when a PC is being assembled, AMIDEWIN can program the motherboard with a serial number that matches the production label.

# Is AMIDEWIN Legit?
Yes AMIDEWIN is 100% legitimate, but it's not typically meant for end users. It’s a low-level firmware tool with the ability to modify system-critical information. While powerful, it should be used responsibly, and usually only by:
- OEMs
- System integrators
- Authorized repair technicians

