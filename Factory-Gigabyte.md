# 🏭 Clean Gigabyte motherboard dump (Never spoofed)

> [!TIP]
> Gigabyte is the easiest motherboard to spoof, the only thing that is Unique is UUID and EasyAntiCheat does not log it.

# [Type 000] -- BIOS Information

## BIOS Vendor (/IVN)
```
American Megatrends Inc.
```

## BIOS Version (/IV)
```
F12
```

## BIOS Release Date (/ID)
```
01/18/2021
```

# [Type 001] -- System Information

## Manufacturer (/SM)  			
```
Gigabyte Technology Co., Ltd.
```

## Product Name (/SP)
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
```
B550 GAMING X V2
``` 

## Version (/SV)      			
```
Default string
```

## Serial Number (/SS)  			
```
Default string
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

## SKUNumber (/SK)
```
Default string
```

## Family (/SF)
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field start with the model of your motherboard such as `B550` followed by `MB`
```
B550 MB
```

# [Type 002] -- Base Board/Module information
## Manufacturer (/BM)    	
> [!CAUTION]
> Same as Type 001 Manufacturer
```
Gigabyte Technology Co., Ltd.
```


## Product Name (/BP)  	
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
```
B550 GAMING X V2
```

## Version (/BV)        			
```
x.x
```

## Serial Number (/BS)  			
```
Default string
```

## Asset Tag (/BT)      			
```
Default string
```

## Location in Chassi (/BLC)         
```
Default string
```

# [Type 003] -- System Enclosure or Chassis
## Manufacturer (/CM)     			
```
Default string
```

## Version (/CV)         			
```
Default string
```

## Serial Number (/CS)        		
```
Default string
```

## Asset Tag (/CA)        			
```
Default string
```

## SKU Number (/CSK)				
```
Default string
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

## Asset Tag (/PAT)					
```
To Be Filled By O.E.M.
```
### or
```
Unknown
```

## Part Number (/PPN)				
```
To Be Filled By O.E.M.
```
### or
```
Unknown
```
							
# [Type 011] -- OEM Strings
## String #1 (/OS)					
```
Default string
```

# [Type 012] -- System Configuration Options
## String #1 (/SCO)
```
Default string
```
