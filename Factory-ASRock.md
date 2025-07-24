# 🏭 Clean ASRock motherboard dump (Never spoofed)

# [Type 001] -- System Information

## Manufacturer (/SM)
```
ASRock
```
**Command prompt:**
```
AMIDEWINx64.exe /SM "ASRock"
```

## Product Name (/SP)
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
```
H510M-HDV/M.2 SE
```
**Command prompt:**
```
AMIDEWINx64.exe /SP "H510M-HDV/M.2 SE"
```

## Version (/SV)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /SV "To Be Filled By O.E.M."
```

## Serial Number (/SS)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /SS "To Be Filled By O.E.M."
```


## UUID (/SU)
> [!CAUTION]
> On ASRock motherboards, the UUID is typically zeroed out after the first 6 bytes, which include the following fields:
> 
> - TimeLow:  9C 6B 00 76 (Little-endian → 76006B9C)
>   
> - TimeMid:  9C C4 (Little-endian → C49C)
>   
> These first 6 bytes (TimeLow + TimeMid) may be derived from a timestamp or manufacturing data, but are often static across systems, suggesting a non-unique UUID.
>
> The remaining 10 bytes (including TimeHiAndVersion, ClockSeq, and Node) are consistently filled with zeros.
```
9C 6B 00 76 9C C4 00 00 00 00 00 00 00 00 00 00
```
**Command prompt:**
```
AMIDEWINx64.exe /SU BF37DEFA314E00000000000000000000
```

## SKUNumber (/SK)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /SK "To Be Filled By O.E.M."
```

## Family (/SF)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /SF "To Be Filled By O.E.M."
```

# [Type 002] -- Base Board/Module information
## Manufacturer (/BM)
> [!CAUTION]
> Same as Type 001 Manufacturer
```
ASRock
```
**Command prompt:**
```
AMIDEWINx64.exe /BM "ASRock"
```

## Product Name (/BP)
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
```
H510M-HDV/M.2 SE
```
**Command prompt:**
```
AMIDEWINx64.exe /BP "H510M-HDV/M.2 SE"
```

## Version (/BV)
> [!CAUTION]
> Do not change this field. It typically consists of 22 space characters (0x20) across all ASRock motherboards.
> 
> This value appears to be intentional and consistent.
```
                      
```
**Command prompt:**
```
AMIDEWINx64.exe /BV "                      "
```

## Serial Number (/BS)
> [!CAUTION]
> Some users spoof this field to start with `M80-`, but based on my experience, all genuine ASRock motherboards I've encountered use serial numbers that begin with `BR80`.
> 
> You may set this to any value you like, but keep in mind:
> 
> Maximum length: 15 characters
> 
> Recommended prefix for ASRock boards: `BR80`
```
BR80YFDYZ68ICQ4
```
**Command prompt:**
```
AMIDEWINx64.exe /BS "BR80YFDYZ68ICQ4"
```

## Asset Tag (/BT)
> [!CAUTION]
> Do not change this field. It typically consists of 22 space characters (0x20) across all ASRock motherboards.
> 
> This value appears to be intentional and consistent.

```
                      
```
**Command prompt:**
```
AMIDEWINx64.exe /BT "                      "
```

## Location in Chassi (/BLC)
> [!CAUTION]
> Do not change this field. It typically consists of 22 space characters (0x20) across all ASRock motherboards.
> 
> This value appears to be intentional and consistent.
```
                      
```
**Command prompt:**
```
AMIDEWINx64.exe /BLC "                      "
```

# [Type 003] -- System Enclosure or Chassis
## Manufacturer (/CM)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /CM "To Be Filled By O.E.M."
```

## Version (/CV)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /CV "To Be Filled By O.E.M."
```

## Serial Number (/CS)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /CS "To Be Filled By O.E.M."
```

## Asset Tag (/CA)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /CA "To Be Filled By O.E.M."
```

## SKU Number (/CSK)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /CSK "To Be Filled By O.E.M."
```

# [Type 004] -- Processor information
## Serial Number (/PSN)
```
To Be Filled By O.E.M.
```
### or
```
Unknown
```
**Command prompt:**
```
AMIDEWINx64.exe /PSN "To Be Filled By O.E.M."
```

## Asset Tag (/PAT)
```
To Be Filled By O.E.M.
```
### or
```
Unknown
```
**Command prompt:**
```
AMIDEWINx64.exe /PAT "To Be Filled By O.E.M."
```

## Part Number (/PPN)
```
To Be Filled By O.E.M.
```
### or
```
Unknown
```
**Command prompt:**
```
AMIDEWINx64.exe /PPN "To Be Filled By O.E.M."
```
							
# [Type 011] -- OEM Strings
## String #1 (/OS)
```
To Be Filled By O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /OS 1 "To Be Filled By O.E.M."
```
