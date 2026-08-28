This Ghidra processor module is based on reverse-engineering the instruction set from a BQ40Z50 binary firmware dump.
I do not have any specs for the processor. Some instructions may be decoded incorrectly.
There's still a lot of work to be done, but it already produces meaningful decompiled code.

Other BQ chips may use different architectures, like CoolRisc816 in BQ20Z80 with its 22-bit instructions. For details on these, see:

https://media.blackhat.com/bh-us-11/Miller/BH_US_11_Miller_Battery_Firmware_Public_WP.pdf  
https://media.blackhat.com/bh-us-11/Miller/BH_US_11_Miller_Battery_Firmware_Public_Slides.pdf  
https://www.karosium.com/2016/08/smbusb-hacking-smart-batteries.html  

# Installation and usage

Copy the **BQ** directory into **$GHIDRA_DIR/Ghidra/Processors/**, then run Ghidra.

The *code* and *data* parts of the flash image have to be loaded separately. First load *code* (0xE000 bytes max., located at 0x100000 in the .srec file) to **CODE:0**,
then use *File/Add To Program...* (not *File/Import File...*!!!) to add *data* (0x2000 bytes max., located at 0x4000) to **DATA:0x4000**. In memory map, set **CODE**
as read-only.
