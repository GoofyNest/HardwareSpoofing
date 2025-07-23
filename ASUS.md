# 🏭 Clean ASUS motherboard dump (Never spoofed)

> [!IMPORTANT]
> Most of the ASUS motherboards are supported
> 
> The new ASUS motherboards can be hard to spoof and require newer AMIDEWIN, you can try to google for a newer version or one that work for your motherboard.

# [Type 001] -- System Information

### Manufacturer    			
```
ASUS
```

### Product Name    			
```
System Product Name
```

### Version         			
```
System Version
```

### Serial Number   			
```
System Serial Number
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
ASUS_MB_CNL
```

### Family          			
```
To be filled by O.E.M.
```

# [Type 002] -- Base Board/Module information
### Manufacturer    			
```
ASUSTeK COMPUTER INC.
```

### Product Name    			
```
ROG STRIX Z390-E GAMING
```

> [!IMPORTANT]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.

### Version         			
```
Rev 1.xx
```

### Serial Number   			
```
190476921854307
```

> [!IMPORTANT]
> Keep the same start `1904` and the same size, but ranomize the numbers.

### Asset Tag       			
```
Default string
```

### Location in Chassi          
```
Default string
```

# [Type 003] -- System Enclosure or Chassis
### Manufacturer       			
```
Default string
```

### Version          			
```
Default string
```

### Serial Number          		
```
A51H0B3RA7T9
```

> [!IMPORTANT]
> Keep the same start `A51` and the same size, but ranomize the numbers.

### Asset Tag          			
```
A51H0B3RA7T9
```

> [!IMPORTANT]
> Keep the same start `A51` and the same size, but ranomize the numbers.

### SKU Number					
```
A51H0B3RA7T9
```

> [!IMPORTANT]
> Keep the same start `A51` and the same size, but ranomize the numbers.

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
Default string
```

# [Type 012] -- System Configuration Options
### String #1 -> #4			
```
Default string
```

