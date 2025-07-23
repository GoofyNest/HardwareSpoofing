# 🏭 Clean MSI motherboard dump (Never spoofed)

> [!IMPORTANT]
> Most of the MSI motherboards are supported
> 
> The new MSI motherboards can be hard to spoof and require newer AMIDEWIN, you can try to google for a newer version or one that work for your motherboard.

# [Type 001] -- System Information

### Manufacturer    			
```
Micro-Star International Co., Ltd.
```

### Product Name    			
```
MS-7D95
```

> [!IMPORTANT]
> Your motherboard should have a `MS-MODELNUMBER` if you cannot find it, then google it and ensure its correct.
> Do not change this if your values are already good.

### Version         			
```
1.0
```

### Serial Number   			
```
To be filled by O.E.M.
```

### UUID            			
```
3A D4 1B 77 C2 91 4F 2D 92 A3 E8 5C 74 0F D1 29
```

> [!IMPORTANT]
> What You Should Change:
> 
> TimeLow 0-3 bytes
> 
> TimeMid 4-5 bytes
> 
> TimeHi/Ver 6 bytes (Random but set version bits (typically 1 or 4)
> 
> ClockSq/Var 8 bytes (Random but set variant bits (must start with 10)
> 
> Node 10-5 bytes (Random)

### SKUNumber       			
```
To be filled by O.E.M.
```

### Family          			
```
To be filled by O.E.M.
```

# [Type 002] -- Base Board/Module information
### Manufacturer    			
```
Micro-Star International Co., Ltd.
```

> [!IMPORTANT]
> Same as Type 001 Manufacturer

### Product Name    			
```
PRO B550M-P GEN3 (MS-7D95)
```

> [!IMPORTANT]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.

### Version         			
```
1.0
```

### Serial Number   			
```
07D9X40_J19K6852MC
```

> [!IMPORTANT]
> Keep the same start `07D9` and the same size, but ranomize the numbers.

### Asset Tag       			
```
To be filled by O.E.M.
```

### Location in Chassi          
```
To be filled by O.E.M.
```

# [Type 003] -- System Enclosure or Chassis
### Manufacturer       			
```
Micro-Star International Co., Ltd.
```

### Version          			
```
1.0
```

### Serial Number          		
```
To be filled by O.E.M.
```

### Asset Tag          			
```
To be filled by O.E.M.
```

### SKU Number					
```
To be filled by O.E.M.
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

### Part Number					
```
To Be Filled By O.E.M.
```
### or
```
Unknown
```
							
# [Type 011] -- OEM String(s)
### String #1 -> #8			
```
To be filled by O.E.M.
```

# [Type 012] -- System Configuration Options
### String #1 -> #4			
```
To be filled by O.E.M.
```

