# Instructions

These instructions explain how to set up the tools required to build The Legend of Zelda: Link's Awakening, 
which help assemble the source files into a ROM.


## Windows

To run the batch file in each folder, you first need the program [**vDos**](https://www.vdos.info/download.html).
This is due to the INTELLIGENT SYSTEMS Assembler & Linker programs being 16-bit which aren't supported on current
64-bit systems like Windows 10. Run setup and choose to install in whatever location that is easiest for you.

Once installed, run vDos for the first time and a test program will begain automatically. If said test works,
copy the desired folder to the location of vDos (default is **C:/vDos**) then ```cd``` to it. e.g ```cd DMG_Zelda_US_v2```.
Run the batch file using ```GAL```. 

The output should be a .gb and .sym file.


Congrats! You just built from the Link's Awakening source. Now you can play the ROM on any 
Nintendo Game Boy emulator. 


## HEX Files

The HEX Files are the sound data files for the game, which are formatted into Intel Hex.
They can be converted to Binary for assembling the ROM using **objcopy** on any Linux machine
using the following command: ```objcopy -I ihex -O binary --gap-fill 0xFF file.hex file.bin```,
"file" being the name of what you're converting (File names: bgm_1 / bgm_1F / bgm_1G.bin, bgm_2.bin, se.bin).
After doing as such, pad the files to 16.0 KB (or 16,384 bytes) in a hex editor with 0xFF until you reach
the end of offset **00003FF0**. The default Hex files have been converted already for your convenience but if
you want to change the sound data, this is how you would convert.


## Debug Build

You can make debug builds of each ROM by editing *line 42* in ZMA.DMG from ``DB	$00`` to ``DB	$01``.
See the [**Cutting Room Floor article**](https://tcrf.net/The_Legend_of_Zelda:_Link%27s_Awakening#Debug_Utilities) for more infomation on how to use each function. 

If done correctly, you should have ROMs with the following hashes:

- us_v2.gb `sha1: 76a0487834866da3a4d06ddca37c395391560664`
- jp_v1.gb `sha1: 3d6e652dc431e9e5746352a09f24e95627f7836f`
- de_v0.gb `sha1: c2bb60f11645979dc43a1ff88a35a88cfb818b23`
- fr_v0.gb `sha1: 0d503a09e4fcf21709ba93b9a24ed44900efab9e`


## Other File Types

ISX - Raw Intelligent Systems ROM output

DMG - Assembly code

ISO - Object files assembled from Assembly Code

BAT - Main batch file 

CHR - 2BPP GFX 
