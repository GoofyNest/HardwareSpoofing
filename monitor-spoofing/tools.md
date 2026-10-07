---
description: Used to dump/edit monitor EDI
icon: burst-new
---

# Tools

## Use these to dump/edit:

{% embed url="https://customresolutionutility.net/" %}

{% embed url="https://www.entechtaiwan.com/util/moninfo.shtm" %}

{% embed url="https://www.analogway.com/products/aw-edid-editor" %}

{% embed url="https://mh-nexus.de/en/hxd/" %}

***

## Tools made by me

```powershell
# Edit-EDID.ps1
# Edits specific EDID fields in a binary file and fixes the checksum.

param(
    [Parameter(Mandatory)][string]$InputFile,
    [string]$OutputFile,

    [int]$Week       = -1,   # Manufacturing week (1-53)
    [int]$Year       = -1,   # Manufacturing year (e.g. 2024)
    [int]$SerialNum  = -1,   # Numeric serial, bytes 12-15 (e.g. 31126)
    [string]$SerialStr = ""  # Serial string up to 13 chars (e.g. UK02428031126)
)

# --- Load file ---
$bytes = [System.IO.File]::ReadAllBytes($InputFile)
if ($bytes.Length -lt 128) { Write-Error "File too small to be a valid EDID."; exit 1 }

# --- Manufacturing Week (byte 16) ---
if ($Week -ge 0) {
    if ($Week -lt 1 -or $Week -gt 53) { Write-Error "Week must be 1-53."; exit 1 }
    $bytes[16] = [byte]$Week
    Write-Host "Set manufacturing week -> $Week (0x$($Week.ToString('X2')))"
}

# --- Manufacturing Year (byte 17) ---
if ($Year -ge 0) {
    if ($Year -lt 1990 -or $Year -gt 2245) { Write-Error "Year must be 1990-2245."; exit 1 }
    $bytes[17] = [byte]($Year - 1990)
    Write-Host "Set manufacturing year -> $Year (offset $($Year - 1990), 0x$(($Year-1990).ToString('X2')))"
}

# --- Numeric Serial Number (bytes 12-15, little-endian) ---
if ($SerialNum -ge 0) {
    $bytes[12] = [byte]($SerialNum -band 0xFF)
    $bytes[13] = [byte](($SerialNum -shr 8) -band 0xFF)
    $bytes[14] = [byte](($SerialNum -shr 16) -band 0xFF)
    $bytes[15] = [byte](($SerialNum -shr 24) -band 0xFF)
    Write-Host "Set numeric serial -> $SerialNum (0x$($SerialNum.ToString('X8')))"
}

# --- Serial String in 0xFF descriptor block ---
if ($SerialStr -ne "") {
    if ($SerialStr.Length -gt 13) { Write-Error "Serial string max 13 characters."; exit 1 }

    # Find the 0xFF descriptor block (search offsets 54, 72, 90, 108)
    $found = $false
    foreach ($offset in @(54, 72, 90, 108)) {
        if ($bytes[$offset+3] -eq 0xFF) {
            # Bytes 0-4: header (keep as-is), bytes 5-17: 13 chars of text
            # Pad with 0x20 (space), terminate with 0x0A if shorter than 13
            $padded = [byte[]]::new(13)
            for ($i = 0; $i -lt 13; $i++) { $padded[$i] = 0x20 }  # fill spaces

            $strBytes = [System.Text.Encoding]::ASCII.GetBytes($SerialStr)
            for ($i = 0; $i -lt $strBytes.Length; $i++) { $padded[$i] = $strBytes[$i] }
            if ($strBytes.Length -lt 13) { $padded[$strBytes.Length] = 0x0A }  # newline terminator

            for ($i = 0; $i -lt 13; $i++) { $bytes[$offset + 5 + $i] = $padded[$i] }

            Write-Host "Set serial string in 0xFF descriptor at byte $offset -> '$SerialStr'"
            $found = $true
            break
        }
    }

    if (-not $found) {
        # No existing 0xFF block — replace the first 0x10 (dummy) block
        foreach ($offset in @(54, 72, 90, 108)) {
            if ($bytes[$offset+3] -eq 0x10) {
                $bytes[$offset]   = 0x00
                $bytes[$offset+1] = 0x00
                $bytes[$offset+2] = 0x00
                $bytes[$offset+3] = 0xFF
                $bytes[$offset+4] = 0x00

                $padded = [byte[]]::new(13)
                for ($i = 0; $i -lt 13; $i++) { $padded[$i] = 0x20 }
                $strBytes = [System.Text.Encoding]::ASCII.GetBytes($SerialStr)
                for ($i = 0; $i -lt $strBytes.Length; $i++) { $padded[$i] = $strBytes[$i] }
                if ($strBytes.Length -lt 13) { $padded[$strBytes.Length] = 0x0A }
                for ($i = 0; $i -lt 13; $i++) { $bytes[$offset + 5 + $i] = $padded[$i] }

                Write-Host "Created new 0xFF descriptor at byte $offset -> '$SerialStr'"
                $found = $true
                break
            }
        }
    }

    if (-not $found) { Write-Warning "No 0xFF or 0x10 descriptor slot available for serial string." }
}

# --- Fix checksum (byte 127) ---
# Sum of all 128 bytes must be 0 mod 256
$sum = 0
for ($i = 0; $i -lt 127; $i++) { $sum += $bytes[$i] }
$bytes[127] = [byte]((256 - ($sum % 256)) % 256)
Write-Host "Recalculated checksum -> 0x$($bytes[127].ToString('X2'))"

# --- Save output ---
if (-not $OutputFile) { $OutputFile = $InputFile }
[System.IO.File]::WriteAllBytes($OutputFile, $bytes)
Write-Host "Saved to: $OutputFile"
```

Example usage:

```powershell
PowerShell -ExecutionPolicy Bypass -File .\Edit-EDID.ps1 -InputFile test.bin -OutputFile out.bin -Week 28 -Year 2024 -SerialNum 31126 -SerialStr "UK02428031126"
```

> You must dump your existing monitor EDID as "test.bin" in order for it to work.

You can even join our Discord and we have our own system information tool, when uploaded in a ticket you get your current monitor(s) EDID.

{% embed url="https://discord.com/invite/JtU8FxQnN5" %}
