# 🏭 Clean Gigabyte motherboard dump (Never spoofed)

> [!CAUTION]
> Reminder, please do not use the serials in here, this is just an example over how default or factory serials are looking like.
> 
> You should use your own serials and randomize them, if you are not sure how to then wait for me to release tools.
> 

> [!TIP]
> Gigabyte is the easiest motherboard to spoof, the only thing that is Unique is UUID and EasyAntiCheat does not log it.


# [Type 000] -- BIOS Information

## BIOS Vendor (/IVN)
```
American Megatrends Inc.
```
**Command prompt:**
```
AMIDEWINx64.exe /IVN "American Megatrends Inc."
```

## BIOS Version (/IV)
```
F12
```
**Command prompt:**
```
AMIDEWINx64.exe /IV "F12"
```

## BIOS Release Date (/ID)
```
01/18/2021
```
**Command prompt:**
```
AMIDEWINx64.exe /ID "01/18/2021"
```

# [Type 001] -- System Information

## Manufacturer (/SM)  			
```
Gigabyte Technology Co., Ltd.
```
**Command prompt:**
```
AMIDEWINx64.exe /SM "Gigabyte Technology Co., Ltd."
```

## Product Name (/SP)
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
```
B550 GAMING X V2
```
**Command prompt:**
```
AMIDEWINx64.exe /SP "B550 GAMING X V2"
```

## Version (/SV)      			
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /SV "Default string"
```

## Serial Number (/SS)  			
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /SS "Default string"
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
A3 9D 4B 72 C1 D8 44 9A B7 82 1F A9 D0 2E 67 41
```
**Command prompt:**
```
AMIDEWINx64.exe /SU A39D4B72C1D8449AB7821FA9D02E6741
```

## SKUNumber (/SK)
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /SK "Default string"
```

## Family (/SF)
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field start with the model of your motherboard such as `B550` followed by `MB`
```
B550 MB
```
**Command prompt:**
```
AMIDEWINx64.exe /SF "B550 MB"
```

# [Type 002] -- Base Board/Module information
## Manufacturer (/BM)    	
> [!CAUTION]
> Same as Type 001 Manufacturer
```
Gigabyte Technology Co., Ltd.
```
**Command prompt:**
```
AMIDEWINx64.exe /BM "Gigabyte Technology Co., Ltd."
```


## Product Name (/BP)  	
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
```
B550 GAMING X V2
```
**Command prompt:**
```
AMIDEWINx64.exe /BP "B550 GAMING X V2"
```

## Version (/BV)        			
```
x.x
```
**Command prompt:**
```
AMIDEWINx64.exe /BV "x.x"
```

## Serial Number (/BS)  			
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /BS "Default string"
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
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /CS "Default string"
```

## Asset Tag (/CA)        			
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /CA "Default string"
```

## SKU Number (/CSK)				
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /CSK "Default string"
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
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /OS 1 "Default string"
```

# [Type 012] -- System Configuration Options
## String #1 (/SCO)
```
Default string
```
**Command prompt:**
```
AMIDEWINx64.exe /SCO 1 "Default string"
```
