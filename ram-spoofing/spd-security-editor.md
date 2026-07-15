---
description: Thanks to @zenoxoid at Discord
icon: '1'
---

# SPD Security Editor

## Spoofing RAM SPD Data with an SPD Programmer <a href="#spoofing-ram-spd-data-with-an-spd-programmer" id="spoofing-ram-spd-data-with-an-spd-programmer"></a>

***

{% hint style="success" icon="info" %}
Compatibility

G.SKILL memory modules bearing the **"TA" prefix** above the barcode are confirmed incompatible. All other 99% of memory modules are supported.
{% endhint %}

You can buy the SPD Programmer [here](https://www.aliexpress.com/item/1005010734907283.html), there is a couple of sellers all seemingly selling the same SPD Programmer, but this is the one I personally bought from and can confirm worked / provided software for it (i would assume the others sellers also provide the same software).

***

Every DDR4/DDR5 memory module has a small chip called the **SPD (Serial Presence Detect)** chip. Your system reads this chip at every boot to learn about the installed memory, things like manufacturer, part number, serial number, production date, capacity, and timing parameters. This chip holds all the information about your memory that is accessible to your computer.

***

Pretty much all DDR5 memory ships with this chip fully write-protected, meaning you can't modify it from within your running system hence needing an external SPD programmer like this one to do it properly.

***

A significant portion of DDR4 Ram however is **not** write-protected, which could allow you to change SPD data directly from software without any hardware programmer. This guide won't cover that path; it's a separate rabbit hole of finding working software for it and documentation on usage. Consider yourself warned if you go digging.

***

{% hint style="warning" icon="triangle-exclamation" %}
Thaiphoon Burner\
\
Thaiphoon Burner PAID version enables SPD writing (NOT DDR5) I believe, but the owner disappeared for several years, which ended up removing the paid access for all users. But has now after several years come back to maintain it at this link [https://files.fm/ThaiphoonBurner](https://files.fm/ThaiphoonBurner), hard to know if your DDR4 Ram would be able to be modified, so unless a paid version crack surfaces its not advised especially with the unreliable developer.
{% endhint %}

***

The original seller instructions and software download are hosted at [this link](https://ucn79adcrsoe.feishu.cn/docx/Mu88dLGk3oNhjPxsK6icDReTnqS) however the software requires an activation code that comes with your purchase. (Older Legacy versions does not seem to require an activation code, but the stability / usability can not be confirmed as its untested)

***

{% hint style="info" icon="download" %}
It's worth cracking and preserving a working offline copy of the tool in case the seller disappears or pulls support.
{% endhint %}

{% hint style="warning" %}
As with any closed-source Chinese tooling, run it sandboxed or on a throwaway Windows install. It's probably fine, but there's no reason not to be cautious if you are skeptical.
{% endhint %}

***

The good news is that unlike fiddling with most mp tools where you're clicking blind through undocumented interfaces, this programmer is genuinely straightforward. The software is simple and clearly built for ease of use.

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

***

### Using the SPD Programmer <a href="#using-the-spd-programmer" id="using-the-spd-programmer"></a>

#### 1. Driver Installation <a href="#id-1-driver-installation" id="id-1-driver-installation"></a>

On first launch you need to install a required driver, do this before anything else or the programmer won't detect your hardware.

#### 2. Connecting Your Memory <a href="#id-2-connecting-your-memory" id="id-2-connecting-your-memory"></a>

Make sure your Ram is seated in the programmer like in the image below. Make sure your USB-C cable is a **data cable** and not a charge-only cable. This is a common mistake. If everything is correct you'll see **"Hardware Connected"** along with some basic module info in the display.

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

#### 3. Read Memory <a href="#id-3-read-memory" id="id-3-read-memory"></a>

Hit **"Read Memory Bin"** this dumps the current SPD contents and populates all the fields with your module's real data. Do this before touching anything.

#### 4. Back Up First <a href="#id-4-back-up-first" id="id-4-back-up-first"></a>

Save a `.bin` backup of the original SPD before making any changes. You'll want this if something goes wrong or you need to restore original values later. Doing this is heavily advised, it's always smart to keep a backup of your original serials.

***

### What to Change and Why <a href="#what-to-change-and-why" id="what-to-change-and-why"></a>

#### 5. Brand <a href="#id-5-brand" id="id-5-brand"></a>

Leave this alone unless you're actively spoofing as a different brand. If your goal is just nulling serials, don't touch it.

#### 6. Manufacturing Date _(YEAR WEEK format)_ <a href="#id-6-manufacturing-date-year-week-format" id="id-6-manufacturing-date-year-week-format"></a>

The example image shows 2022 week 48. Nudge this by a small amount enough to differentiate your memory from its original value without it looking out of place.

#### 7. Serial Number <a href="#id-7-serial-number" id="id-7-serial-number"></a>

Clicking **"Clear"** nulls the serial. For most purposes this is exactly what you want, unless you intend to keep more legitimate ones, if so only change a few numbers at the end, more is not needed.

#### 8. Product Model <a href="#id-8-product-model" id="id-8-product-model"></a>

Don't change this unless you're spoofing as a different Ram kit/brand.

#### 9. Manufacturer <a href="#id-9-manufacturer" id="id-9-manufacturer"></a>

Same as above, leave it unless you're doing a full brand spoof.

#### 10. Writing Changes <a href="#id-10-writing-changes" id="id-10-writing-changes"></a>

Once you've set everything, click **"Write to Physical Chip"**. It takes a second or two. Done.

To verify your changes, use any preferred tools to view information. I recommend **DMI Edit** it shows more Ram data than most tools and lets you confirm everything was written correctly.

***

### Spoofing as Corsair Vengeance <a href="#spoofing-as-corsair-vengeance" id="spoofing-as-corsair-vengeance"></a>

Just nulling your serial might look odd depending on what your original module is, a blank serial on a Kingston or PNY stick isn't super weird, but can be seen as unusual. A better approach is spoofing into something where nulled serials are expected behavior.

Corsair Vengeance DDR4 and most DDR5 sticks ship from the factory with nulled serials. Some newer DDR5 units have started including serials, but that's easy to work around by setting the manufacturing date to before those were produced, the DDR5 Vengeance line launched late 2021, so you have a wide window to pick from.

On the brand field (point 5), you may notice it shows **"No Brand"**. There is a Corsair option in the software, but genuine nulled Corsair sticks typically show as **"Unknown Brand"** in windows, **"No Brand"** in the programmer is the same thing. Corsair apparently never bothered flashing brand data onto their memory, which is likely also why the serials are naturally blank.

All the meaningful identity information on Corsair sticks lives in the **Product Model** string. Here's how to read it, using `CMK32GX5M2B5600C36` as an example:

| Segment                                          | Meaning                          |
| ------------------------------------------------ | -------------------------------- |
| <mark style="background-color:pink;">CMK</mark>  | Vengeance / Vengeance LPX (DIMM) |
| <mark style="background-color:pink;">32</mark>   | Total kit capacity: 32GB         |
| <mark style="background-color:pink;">GX5</mark>  | DDR5                             |
| <mark style="background-color:pink;">M2</mark>   | 2 modules (2x16GB)               |
| <mark style="background-color:pink;">B</mark>    | Black                            |
| <mark style="background-color:pink;">5600</mark> | 5600 MT/s                        |
| <mark style="background-color:pink;">C36</mark>  | CL36                             |

So: a 2x16GB DDR5 Vengeance kit, black, 5600MHz CL36.

The tricky part is matching your actual Ram's speed. Check the Corsair catalogue and find a kit that matches your speed, capacity, and timings (check both RGB and non-RGB as there are different options for speed/timings).

* [Vengeance 32GB DDR5 5200 C40](https://www.corsair.com/us/en/p/memory/cmk32gx5m2b5200z40/vengeance-32gb-2x16gb-ddr5-dram-5200mt-s-cl40-amd-expo-memory-kit-cmk32gx5m2b5200z40)
* [Vengeance RGB 32GB DDR5 5200 C40](https://www.corsair.com/us/en/p/memory/cmh32gx5m2b5200c40/vengeance-rgb-32gb-2x16gb-ddr5-dram-5200mhz-c40-memory-kit-black-cmh32gx5m2b5200c40)

If you find a match, use that model string. If you don't have an exact match, you have three options: spoof it anyway using your real speed/timings in the model string (anticheats can query XMP/EXPO profiles and compare against the model string, very very unlikely that they do this but worth considering), or put in a speed/timing string that is mismatched from your real speed. (2nd option is probably not bad if you put a higher speed than your actual ram set, would try and match the timings tho)\
Third option is to use the programmer to rewrite your speed profiles down to match an existing Corsair Ram stick, though that's something I have little knowledge of and no experience in, so you're on your own there.

{% hint style="info" icon="lightbulb" %}
If you find a matching Corsair Kit, google it to see when it released so you don't set your manufacturing date 2 years before it's launch (this will probably never matter to an AC, but doesn't hurt to be thorough)
{% endhint %}

For adjusting your Product Model to your found Ram set:

| Chars              | Meaning                                       |
| ------------------ | --------------------------------------------- |
| `CMK` / `CMH`      | CMK = Vengeance (no RGB), CMH = Vengeance RGB |
| `32`               | Total kit capacity in GB                      |
| `GX4` / `GX5`      | GX4 = DDR4, GX5 = DDR5                        |
| `M1` / `M2` / `M4` | M1 = 1 stick, M2 = 2 sticks, M4 = 4 sticks    |
| `B` / `W`          | B = Black, W = White                          |
| `5200`             | Speed in MT/s                                 |
| `C` / `Z`          | C = Intel XMP only, Z = AMD EXPO + Intel XMP  |
| `40`               | CAS latency number                            |

{% hint style="info" %}
Intel XMP only is the more common variant, as the AMD EXPO was retroactively added later down the line to more popular kits, you can check in your Bios if you have EXPO profiles.
{% endhint %}

***

If any unexpected issues occur, you may refer to the original guide by the sellers, as they go into some troubleshooting with locked SPD and such which was not covered in this guide.\
There is also a 24 minute video in that guide that goes through the tools usage in greater length and depth than discussed here (aldo in chinese), It showcases some troubleshooting, and also shows the Modifcation of XMP profiles.
