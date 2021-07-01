--------------------------------------------------------------------------------
Konami SCC Cartridge Repair Board v1.0
Copyright (c) 2021 RBSC
Portions (c) Jipe, Eric Boez and Eugene Brychkov
--------------------------------------------------------------------------------

About the project
-----------------

Konami SCC cartridges normally contain the 2212P003 chip, a 128kb or 256kb ROM chip, a resistor matrix and a couple of ceramic
capacitors. The Konami's SCC chip works as both mapper and sound card. The mapper supports up to 512kb games with K4/K5 mappers. It
may happen that the SCC chip gets fried or appears to be missing (if the cartridge was vandalized). The fact is, that it is impossible
to buy this chip separately, not even its clones exist. So, if your cartridge is damaged or vandalized, you normally won't be able to
restore it to the working condition without the special hardware addon.

In order to restore the cartridge to the working condition there could be 2 solutions: install the special board with an FPGA to fully
emulate the Konami's SCC chip or go for a much simplier and cheaper solution - just install the K4 mapper emulator. The FPGA solution
will be more costly - it will require an expensive FPGA chip and someone's skills to write the special firmware for it. Simple Altera
MAX chips won't be suitable for such a project because the chip should be rather powerful to emulate both mapper and SCC sound card.
And more complex chips are much more expensive and much larger in size, which is a blocker for a small MSX cartridge's case.

So, the only remaining reasonable solution is to install the K4 mapper emulator on the board that would be equal to the size of the
Konami's SCC chip. There are already available solutions for such mapper emulator that only require 3 SOIC chips, a few resistors and
capacitors. This board's design is based on  one of these solutions.

There's, however, a different problem - no SCC sound from the cartridge after modification. The workaround is to use some other MSX
cartridge that has or emulates SCC sounc card, for example MFR or Carnivore2. But the real problem is that most of Konami's games
will not look for SCC sound cards in any other MSX slots than its own, because they were designed to work with the SCC chip in the
same slot. Luckily, there's also a solution for this. A few skilled people in the MSX community can create special patches for
Konami's games to support using SCC sound card in a different slot. One of these persons is BiFi (http://bifi.msxnet.org/msxnet/).
For this release he has created the IPS patch for Nemesis3 cartridge. See the Patch folder for the IPS file.

The Konami SCC chip replacement board may also help to turn 1 or 2 megarom cartridge into a 4 megarom one. So, you can actually put
an improved (patched) bigger version of the game into the cartridge or to use a completely different game that needs K4 mapper. Not
all games will work with the repaired cartridge, so before doing the modification it's recommended to find our whether certain game
works (on MSX forums) or just temporarily install an IC socket for the EPROM to try different versions of the game or a new game's
ROM. And only after that solder the pre-programmed EPROM onto the board.


Important notes
---------------

If you plan to use the modified version of a game or a different game in the restored cartridge, please first choose the proper
EPROM chip that needs to be purchased. For a 1 megarom game you will need 27C010 EPROM, for a 2 megarom game you will need 27C020
EPROM and for the a 4 megarom game you will need 27C040 EPROM chip. These UV-erasable EPROM chips in DIP32 casing can be still
purchased from various electronic stores. If you plan to experiment with the game, make sure you also buy a 32-pin socket and a
UV chip eraser.

Before modding your cartridge please read the following notes carefully:

 - The broken SCC chip has to be removed, as well as the small 22pf ceramic capacitor near it

 - If you plan to use the original game with PSG sound, just leave the original ROM chip on the board

 - If you plan to use a patched game or a different game, remove the original ROM chip from the board

 - A few tracks have to be cut on the cartridge's board. See the pictures in the Pics folder for more info

   - Cut track between pins 32 and 31 of the EPROM on BOTH sides of the board
   - Cut track to EPROM pin 24 on the front side of the board
   - Cut EPROM pin 22's connection to the ground on the back side of the board

 - A few wires have to be soldered on the back side of the board. See the pictures in the Pics folder for more info

   - Pin 24 of EPROM (OE) should be connected to the RD signal coming from the slot
   - Pin 22 of EPROM (CE) should be connected to pin 10 of the replacement board (SLTSL signal)
   - Pin 40 of the replacement board (MA18) should be connected to pin 31 of the EPROM (A18 signal)

 - Do not use any sockets to install the SCC replacement board and the EPROM chip, otherwise it won't fit into the case

 - Use single row 2.54mm straight pin headers for the SCC replacement board's mounting

 - The pictures of the board have an additional 1k resistor and a wire from pin 40 to GND, those are not needed for the current
   board revision (the initial revision was missing that resistor)


IMPORTANT!
----------

The RBSC provides all the files and information for free, without any liability (see the disclaimer.txt file). The provided information,
software or hardware must not be used for commercial purposes unless permitted by the RBSC. Producing a small amount of bare boards for
personal projects and selling the rest of the batch is allowed without the permission of RBSC.

When the sources of the tools are used to create alternative projects, please always mention the original source and the copyright!


Contact information
-------------------

The members of RBSC group Tnt23, Wierzbowsky, Pencioner, Ptero, GreyWolf, SuperMax and DJS3000 can be contacted via the group's e-mail
address:

info@rbsc.su

The group's coordinator could be reached via this e-mail address:

admin@rbsc.su

The group's website can be found here:

https://rbsc.su/
https://rbsc.su/ru

The RBSC's hardware repository can be found here:

https://github.com/rbsc

The RBSC's 3D model repository can be found here:

https://www.thingiverse.com/groups/rbsc/things

-= ! MSX FOREVER ! =-
