# 🏭 ASRock Factory Settings Reference

# [Type 001] -- System Information

### Manufacturer    			
```
ASRock
```

### Product Name    			
```
H510M-HDV/M.2 SE
```

> [!IMPORTANT]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
       

### Version         			
```
To Be Filled By O.E.M.
```

### Serial Number   			
```
To Be Filled By O.E.M.
```

### UUID            			
```
9C 6B 00 76 9C C4 00 00 00 00 00 00 00 00 00 00
```

> [!IMPORTANT]
> On ASRock motherboards, the UUID is typically zeroed out after the first 6 bytes, which include the following fields:
> - TimeLow:  9C 6B 00 76 (Little-endian → 76006B9C)
> - TimeMid:  9C C4 (Little-endian → C49C)
> These first 6 bytes (TimeLow + TimeMid) may be derived from a timestamp or manufacturing data, but are often static across systems, suggesting a non-unique UUID.
> The remaining 10 bytes (including TimeHiAndVersion, ClockSeq, and Node) are consistently filled with zeros.

### SKUNumber       			
```
To Be Filled By O.E.M.
```

### Family          			
```
To Be Filled By O.E.M.
```

# [Type 002] -- Base Board/Module information
### Manufacturer    			
```
ASRock
```

> [!IMPORTANT]
> Same as Type 001 Manufacturer

### Product Name    			
```
H510M-HDV/M.2 SE
```

> [!IMPORTANT]
> Do not change this unless your motherboard is misidentified or has issues.
> This field should match the exact model printed on your motherboard.

### Version         			
```
                      
```

> [!IMPORTANT]
> Do not change this field. It typically consists of 22 space characters (0x20) across all ASRock motherboards.
> This value appears to be intentional and consistent.

### Serial Number   			
```
BR80YFDYZ68ICQ4
```

> [!IMPORTANT]
> Some users spoof this field to start with `M80-`, but based on my experience, all genuine ASRock motherboards I've encountered use serial numbers that begin with `BR80`.
> You may set this to any value you like, but keep in mind:
> Maximum length: 15 characters
> Recommended prefix for ASRock boards: `BR80`

### Asset Tag       			
```
                      
```

> [!IMPORTANT]
> Do not change this field. It typically consists of 22 space characters (0x20) across all ASRock motherboards.
> This value appears to be intentional and consistent.

### Location in Chassi          
```
                      
```

> [!IMPORTANT]
> Do not change this field. It typically consists of 22 space characters (0x20) across all ASRock motherboards.
> This value appears to be intentional and consistent.

# [Type 003] -- System Enclosure or Chassis
### Manufacturer       			
```
To Be Filled By O.E.M.
```

### Version          			
```
To Be Filled By O.E.M.
```

### Serial Number          		
```
To Be Filled By O.E.M.
```

### Asset Tag          			
```
To Be Filled By O.E.M.
```

### SKU Number					
```
To Be Filled By O.E.M.
```

# [Type 004] -- Processor information
### Serial Number				
```
To Be Filled By O.E.M.
```
### or
```
Unknown
```

### Asset Tag					
```
To Be Filled By O.E.M.
```
### or
```
Unknown
```

###Part Number					
```
To Be Filled By O.E.M.
```
### or
```
Unknown
```
							
# [Type 011] -- OEM Strings
### String #1					
```To Be Filled By O.E.M.```
