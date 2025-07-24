# 🏭 Clean MSI motherboard dump (Never spoofed)

> [!CAUTION]
> Most of the MSI motherboards are supported
> 
> The new MSI motherboards can be hard to spoof and require newer AMIDEWIN, you can try to google for a newer version or one that work for your motherboard.

# [Type 000] -- BIOS Information

## BIOS Vendor (/IVN)
```
American Megatrends International, LLC.
```

## BIOS Version (/IV)
```
1.70
```

## BIOS Release Date (/ID)
```
03/25/2024
```

# [Type 001] -- System Information

## Manufacturer (/SM)    			
```
Micro-Star International Co., Ltd.
```

## Product Name (/SP) 	
> [!CAUTION]
> Your motherboard should have a `MS-MODELNUMBER` if you cannot find it, then google it and ensure its correct.
> Do not change this if your values are already good.
```
MS-7D95
```

## Version (/SV)  			
```
1.0
```

## Serial Number (/SS)			
```
To be filled by O.E.M.
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

## SKUNumber (/SK)     			
```
To be filled by O.E.M.
```

## Family (/SF)         			
```
To be filled by O.E.M.
```

# [Type 002] -- Base Board/Module information
## Manufacturer (/BM)  
> [!CAUTION]
> Same as Type 001 Manufacturer
```
Micro-Star International Co., Ltd.
```

## Product Name (/BP)  	
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
```
PRO B550M-P GEN3 (MS-7D95)
```

## Version (/BV)     			
```
1.0
```

## Serial Number (/BS)  	
> [!CAUTION]
> Keep the same start `07D9` and the same size, but randomize the serial.
```
07D9X40_J19K6852MC
```

## Asset Tag (/BT)     			
```
To be filled by O.E.M.
```

## Location in Chassi (/BLC)        
```
To be filled by O.E.M.
```

# [Type 003] -- System Enclosure or Chassis
## Manufacturer (/CM)      			
```
Micro-Star International Co., Ltd.
```

## Version (/CV)        			
```
1.0
```

## Serial Number (/CS)        		
```
To be filled by O.E.M.
```

## Asset Tag (/CA)        			
```
To be filled by O.E.M.
```

## SKU Number (/CSK)				
```
To be filled by O.E.M.
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
							
# [Type 011] -- OEM String(s)
## String #1 -> #8 (/OS)			
```
To be filled by O.E.M.
```

# [Type 012] -- System Configuration Options
## String #1 -> #4 (/SCO)			
```
To be filled by O.E.M.
```

