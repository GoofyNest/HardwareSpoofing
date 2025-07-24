# 🏭 Clean ASUS motherboard dump (Never spoofed)

> [!CAUTION]
> Most of the ASUS motherboards are supported
> 
> The new ASUS motherboards can be hard to spoof and require newer AMIDEWIN, you can try to google for a newer version or one that work for your motherboard.

# [Type 001] -- System Information

## Manufacturer (/SM)   			
```
ASUS
```
**Command prompt:**
```
AMIDEWINx64.exe /SM "ASUS"
```

## Product Name (/SP)   			
```
System Product Name
```
**Command prompt:**
```
AMIDEWINx64.exe /SP "System Product Name"
```

## Version (/SV)     			
```
System Version
```
**Command prompt:**
```
AMIDEWINx64.exe /SV "System Version"
```

## Serial Number (/SS)  			
```
System Serial Number
```
**Command prompt:**
```
AMIDEWINx64.exe /SS "System Serial Number"
```

## UUID (/SU)     
> [!CAUTION]
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
```
3A D4 1B 77 C2 91 4F 2D 92 A3 E8 5C 74 0F D1 29
```
**Command prompt:**
```
AMIDEWINx64.exe /SU 3AD41B77C2914F2D92A3E85C740FD129
```

## SKUNumber (/SK)      			
```
ASUS_MB_CNL
```
**Command prompt:**
```
AMIDEWINx64.exe /SK "ASUS_MB_CNL"
```

## Family (/SF)        			
```
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /SF "To be filled by O.E.M."
```

# [Type 002] -- Base Board/Module information
## Manufacturer (/BM) 			
```
ASUSTeK COMPUTER INC.
```
**Command prompt:**
```
AMIDEWINx64.exe /BM "ASUSTeK COMPUTER INC."
```

## Product Name (/BP)		
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
```
ROG STRIX Z390-E GAMING
```
**Command prompt:**
```
AMIDEWINx64.exe /BP "ROG STRIX Z390-E GAMING"
```

## Version (/BV)        			
```
Rev 1.xx
```
**Command prompt:**
```
AMIDEWINx64.exe /BV "Rev 1.xx"
```

## Serial Number (/BS)  
> [!CAUTION]
> Keep the same start `1904` and the same size, but ranomize the numbers.
```
190476921854307
```
**Command prompt:**
```
AMIDEWINx64.exe /BS "190476921854307"
```

## Asset Tag (/BT)      			
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /BT "Default string"
```

## Location in Chassi (/BLC)        
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /BLC "Default string"
```

# [Type 003] -- System Enclosure or Chassis
## Manufacturer (/CM)    			
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /CM "Default string"
```

## Version (/CV)        			
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /CV "Default string"
```

## Serial Number (/CS)     
> [!CAUTION]
> Keep the same start `A51` and the same size, but ranomize the numbers.
```
A51H0B3RA7T9
```
**Command prompt:**
```
AMIDEWINx64.exe /CS "A51H0B3RA7T9"
```

## Asset Tag (/CA)   
> [!CAUTION]
> Serial Number, Asset Tag and SKU should have the same serial number
```
A51H0B3RA7T9
```
**Command prompt:**
```
AMIDEWINx64.exe /CA "A51H0B3RA7T9"
```

## SKU Number (/CSK)	
> [!CAUTION]
> Serial Number, Asset Tag and SKU should have the same serial number
```
A51H0B3RA7T9
```
**Command prompt:**
```
AMIDEWINx64.exe /CSK "A51H0B3RA7T9"
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
							
# [Type 011] -- OEM String(s)
## String #1 -> #8 (/OS)			
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /OS 1 "Default string"
```
```
AMIDEWINx64.exe /OS 2 "Default string"
```
```
AMIDEWINx64.exe /OS 3 "Default string"
```
```
AMIDEWINx64.exe /OS 4 "Default string"
```
```
AMIDEWINx64.exe /OS 5 "Default string"
```
```
AMIDEWINx64.exe /OS 6 "Default string"
```
```
AMIDEWINx64.exe /OS 7 "Default string"
```
```
AMIDEWINx64.exe /OS 8 "Default string"
```

# [Type 012] -- System Configuration Options
## String #1 -> #4 (/SCO)	
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /SCO 1 "Default string"
```
```
AMIDEWINx64.exe /SCO 2 "Default string"
```
```
AMIDEWINx64.exe /SCO 3 "Default string"
```
```
AMIDEWINx64.exe /SCO 4 "Default string"
```

