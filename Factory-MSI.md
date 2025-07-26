# 🏭 Clean MSI motherboard dump (Never spoofed)

> [!CAUTION]
> Reminder, please do not use the serials in here, this is just an example over how default or factory serials are looking like.
> 
> You should use your own serials and randomize them, if you are not sure how to then wait for me to release tools.
> 
> Most of the MSI motherboards are supported
> 
> The new MSI motherboards can be hard to spoof and require newer AMIDEWIN, you can try to google for a newer version or one that work for your motherboard.

# [Type 000] -- BIOS Information

## BIOS Vendor (/IVN)
```
American Megatrends International, LLC.
```
**Command prompt:**
```
AMIDEWINx64.exe /IVN "American Megatrends International, LLC."
```

## BIOS Version (/IV)
```
1.70
```
**Command prompt:**
```
AMIDEWINx64.exe /IV "1.70"
```

## BIOS Release Date (/ID)
```
03/25/2024
```
**Command prompt:**
```
AMIDEWINx64.exe /IV "03/25/2024"
```

# [Type 001] -- System Information

## Manufacturer (/SM)    			
```
Micro-Star International Co., Ltd.
```
**Command prompt:**
```
AMIDEWINx64.exe /SM "Micro-Star International Co., Ltd."
```

## Product Name (/SP) 	
> [!CAUTION]
> Your motherboard should have a `MS-MODELNUMBER` if you cannot find it, then google it and ensure its correct.
> Do not change this if your values are already good.
```
MS-7D95
```
**Command prompt:**
```
AMIDEWINx64.exe /SP "MS-7D95"
```

## Version (/SV)  			
```
1.0
```
**Command prompt:**
```
AMIDEWINx64.exe /SV "1.0"
```

## Serial Number (/SS)			
```
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /SS "To be filled by O.E.M."
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
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /SK "To be filled by O.E.M."
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
> [!CAUTION]
> Same as Type 001 Manufacturer
```
Micro-Star International Co., Ltd.
```
**Command prompt:**
```
AMIDEWINx64.exe /BM "Micro-Star International Co., Ltd."
```

## Product Name (/BP)  	
> [!CAUTION]
> Do not change this unless your motherboard is misidentified or has issues.
> 
> This field should match the exact model printed on your motherboard.
```
PRO B550M-P GEN3 (MS-7D95)
```
**Command prompt:**
```
AMIDEWINx64.exe /BP "PRO B550M-P GEN3 (MS-7D95)"
```

## Version (/BV)     			
```
1.0
```
**Command prompt:**
```
AMIDEWINx64.exe /BV "1.0"
```

## Serial Number (/BS)  	
> [!CAUTION]
> Remember that you should not copy this serial number, use the one present on your board and randomize that one
> Keep the same start `07D9X40_` and the same size, but randomize the serial after the underline.
```
07D9X40_J19K6852MC
```
**Command prompt:**
```
AMIDEWINx64.exe /BS "07D9X40_J19K6852MC"
```

## Asset Tag (/BT)     			
```
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /BT "To be filled by O.E.M."
```

## Location in Chassi (/BLC)        
```
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /BLC "To be filled by O.E.M."
```

# [Type 003] -- System Enclosure or Chassis
## Manufacturer (/CM)      			
```
Micro-Star International Co., Ltd.
```
**Command prompt:**
```
AMIDEWINx64.exe /CM "Micro-Star International Co., Ltd."
```

## Version (/CV)        			
```
1.0
```
**Command prompt:**
```
AMIDEWINx64.exe /CV "1.0"
```

## Serial Number (/CS)        		
```
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /CS "To be filled by O.E.M."
```

## Asset Tag (/CA)        			
```
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /CA "To be filled by O.E.M."
```

## SKU Number (/CSK)				
```
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /CSK "To be filled by O.E.M."
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
AMIDEWINx64.exe /PSN "To be filled by O.E.M."
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
AMIDEWINx64.exe /PAT "To be filled by O.E.M."
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
AMIDEWINx64.exe /PPN "To be filled by O.E.M."
```
							
# [Type 011] -- OEM String(s)
## String #1 -> #8 (/OS)			
```
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /OS 1 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /OS 2 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /OS 3 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /OS 4 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /OS 5 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /OS 6 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /OS 7 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /OS 8 "To be filled by O.E.M."
```

# [Type 012] -- System Configuration Options
## String #1 -> #4 (/SCO)			
```
To be filled by O.E.M.
```
**Command prompt:**
```
AMIDEWINx64.exe /SCO 1 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /SCO 2 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /SCO 3 "To be filled by O.E.M."
```
```
AMIDEWINx64.exe /SCO 4 "To be filled by O.E.M."
```

