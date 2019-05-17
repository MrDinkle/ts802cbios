# TeleVideo TS-802 CBIOS
The source code of the CBIOS for the Televideo TS-802, one of the many CP/M business computers released in the early 1980s.
Each revision of the CBIOS should contain these files:
```
802HBIOS.MAC - (Includes all MAC files except 802HBOOT.MAC)
802HBASE.MAC - (BIOS main routine)
802HCONS.MAC - (BIOS console and printer driver)
802HHARD.MAC - (BIOS hard disk driver)
802HFLOP.MAC - (BIOS floppy disk driver)
802HBOOT.MAC - (BIOS boot program)
CPM59.COM - (BDOS and CCP routine)
MAKESYS.COM - (Writes CP/M to the system track)
```
You will also need Microsoft Macro-80 to compile the code, which I provided in the repository.

### Compiling

Here's the entireity of Appendix O lifted straight from the Installation and User's guide of the machine.

To modify CBIOS, you must have:

The diskette labeled CBIOS (included with the TS B02), which contains the following files:
```
802FBIOS.MAC    802FBOOT.MAC    802FCONS.MAC    802FDISK.MAC
802FSUBS.MAC    802FEQU.MAC     802DATA.MAC     MAKESYS.COM 
CPM62.COM       802FBOOT.COM 
```
A second diskette containing M8O.COM, L8O.COM, CREF8O.COM (or equivalents), and an editor.

The procedure used to modify the CBIOS is as follows:
1. Insert the diskette labeled CBIOS in Drive B.
2. Insert the diskette containing M8O in Drive A
3. Set the default drive to B: by typing B:.
4. Modify CBIOS source modules on the diskette in Drive B using an editor of your choice.
5. Assemble 802FBIOS.MAC using the M8O assembler, as follows:

**B)A:M80 = 802FBIOS/C**

This will create two files:

B:802FBIOS.REL

B:802FBIOS.CRF

6. Run CREF8O as follows:

**A)A:CREF80 = 802FBIOS**

This will create a cross reference listing in file B:B02FBIOS.PRN.

7. Link 802FBIOS.REL using L8O as follows:

**A)A:L80/P:100, 802FBIOS/N,802FBIOS/E**

This creates the file B:802FBIOS.COM, which contains your modifications to CBIOS.

Now you are ready to build a new user CP/M diskette which will incorporate your modifications.

8. Insert the diskette which will contain the new system into Drive A.

9. Run MAKESYS as follows:

B)**MAKESYS**

Destination Drive? **A**

Bootstrap Filename? **802FBOOT**

BDOS Filename? **CPM59**

BIOS Filename? **802FBIOS**

MAKESYS COMPLETED

The new system is now on the diskette in Drive A Reset the system and run it.

Note: These instructions may differ a little depending on which revision of the CBIOS you decide to compile, so keep that in mind.
