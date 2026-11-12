---
description: Written by @goofy
icon: microchip
---

# SMBIOS-OEM-Reference

## SMBIOS OEM Reference: Observed Layouts and Validation

> The SMBIOS information documented below is based on **firsthand hardware research conducted using physical motherboards purchased and tested by us.**\
> \
> The UUID structures, serial number formats, and manufacturer-specific behaviors were observed through direct examination of real motherboard hardware and firmware.\
> \
> These findings reflect actual hardware observations rather than randomly generated examples or assumptions based solely on software.\
> \
> **Important:** Manufacturer implementations may vary depending on motherboard model, hardware revision, BIOS version, and production date. The documented patterns should not be considered universal across every motherboard from the same manufacturer.

### Scope

SMBIOS Type 0 (BIOS), Type 1 (System), Type 2 (Baseboard), Type 3 (Chassis), and Type 4 (Processor). The DMTF specification defines field locations and data types; OEMs decide most string values and provisioning procedures. There is no universal manufacturer-wide serial algorithm.

***

### Vendor comparison from hardware research

The following information is based on physical motherboards purchased, examined, and tested by me. The documented SMBIOS layouts and UUID structures reflect observations from real hardware.

These patterns may differ between motherboard models, hardware revisions, and BIOS versions.

These patterns may differ between motherboard models, hardware revisions, and BIOS versions.

| Vendor   | Type 1 system manufacturer           | Type 1 system serial     | Type 2 baseboard manufacturer        | Type 2 serial format                                                      | Type 3 chassis serial                                       | UUID structure                                                        |
| -------- | ------------------------------------ | ------------------------ | ------------------------------------ | ------------------------------------------------------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------------- |
| Gigabyte | `Gigabyte Technology Co., Ltd.`      | `Default string`         | `Gigabyte Technology Co., Ltd.`      | `Default string`                                                          | `Default string`                                            | Commonly observed mask `03000200040005000006000700080009`             |
| ASUS     | `ASUS`                               | `System Serial Number`   | `ASUSTeK COMPUTER INC.`              | Observed `1904` prefix followed by 11 digits                              | Observed `A51` prefix followed by 9 alphanumeric characters | Last 6 bytes contain onboard Ethernet MAC                             |
| MSI      | `Micro-Star International Co., Ltd.` | `To Be Filled By O.E.M.` | `Micro-Star International Co., Ltd.` | Manufacturer-specific serial format, separate from MS product code        | `To Be Filled By O.E.M.`                                    | Last 6 bytes contain onboard Ethernet MAC                             |
| ASRock   | `ASRock`                             | `To Be Filled By O.E.M.` | `ASRock`                             | Observed `BR80` or `M80-` prefixes followed by 11 alphanumeric characters | `To Be Filled By O.E.M.`                                    | First 6 bytes contain onboard Ethernet MAC, followed by 10 zero bytes |

***

#### MSI product code vs. serial number

MSI motherboards use product identifiers commonly beginning with `MS-`, such as `MS-7D75`.

**The MS-code is a product or motherboard model identifier, not a unique motherboard serial number.**

* **MS-code:** Identifies a motherboard product or model family. Multiple motherboards of the same model can share this identifier.
* **Serial number:** Identifies an individual motherboard and is generally assigned during manufacturing.
* **SMBIOS Type 2 Product:** May contain a motherboard model name or product identifier.
* **SMBIOS Type 2 Serial Number:** Contains the motherboard serial number or an OEM-defined placeholder.

These fields should not be confused or treated as interchangeable.

***

#### UUID generation

The documented UUID structures are based on hardware observations from the tested motherboards.

For ASUS and MSI, the final six UUID bytes have been observed to correspond to the onboard Ethernet MAC address.

For ASRock, the first six UUID bytes have been observed to contain the onboard Ethernet MAC address, followed by ten zero bytes.

For Gigabyte, the hexadecimal pattern `03000200040005000006000700080009` has been observed across tested hardware. This pattern should be treated as a manufacturer-specific reference rather than a universal UUID standard.

**Note:** UUID byte ordering matters. Raw SMBIOS bytes and UUIDs displayed by Windows may represent the same identifier differently.

***

#### About AUTO

`AUTO` refers to the automatic UUID generation functionality provided by **AMI's AMIDEWINx64** utility.

When `AUTO` is specified, AMIDEWINx64 generates a UUID automatically instead of requiring the user to provide one manually.

However, the automatically generated UUID does not necessarily follow the original manufacturer's UUID structure.

For example, ASUS, MSI, ASRock, and Gigabyte motherboards may use manufacturer-specific UUID layouts that differ from those produced by AMIDEWINx64.

**Important:** While using `AUTO` generally produces a UUID, it does not guarantee that the resulting identifier matches the factory UUID format of the motherboard.

**Research scope:** The documented OEM UUID patterns are based on firsthand hardware testing conducted by the GoofyNest project maintainer. Results may vary depending on motherboard model, chipset, hardware revision, and BIOS version.

***

#### Hardware Flags vs. Detection

Using an automatically generated UUID does not automatically mean you will receive a permanent game ban.

Anti-cheat systems may evaluate multiple hardware characteristics when assessing a device. An unusual SMBIOS UUID, serial number, or manufacturer prefix could potentially contribute to a hardware consistency check, but this does not necessarily indicate cheating or trigger enforcement.

**A hardware flag is not the same as a detection.**

A flag generally refers to an indicator that a system considers unusual or worth evaluating. Detection refers to identifying activity or software that violates the anti-cheat's rules.

It is also important to understand that motherboard manufacturers are not always consistent with their SMBIOS implementations. Serial number formats, UUID structures, placeholder values, and manufacturer prefixes can vary considerably between models and BIOS revisions.

Because of these inconsistencies, an unusual SMBIOS value alone is not reliable evidence of cheating.

**Important:** There is no publicly verified universal anti-cheat hardware flagging system or threshold. The actual detection and enforcement mechanisms vary between anti-cheat providers.

For hardware research, factory-provisioned SMBIOS data should be preserved as a reference when comparing original and modified system identifiers.

***

#### Maintaining OEM Consistency

We recommend using your motherboard's original factory SMBIOS information as a base rather than relying entirely on automatically generated values.

When modifying your SMBIOS information, keeping the original manufacturer's formatting and structure helps maintain consistency. Small byte changes can preserve the overall format, provided the fields are not dependent on checksums or other hardware identifiers.

Manufacturers are notoriously inconsistent with their SMBIOS implementations. UUID structures, serial number prefixes, and placeholder values can differ even between motherboards from the same manufacturer.

**Remember:** A hardware flag does not mean detection. An unusual UUID or serial number does not automatically result in a permanent ban.
