# Donkey King (Color Computer) Disassembly

This is sloppy as shit. My eventual goal is to understand this game enough to make a few modifications to it, in order to make it play a bit closer to the arcade version. However, I honestly know virtually nothing about 6809 development, nor the CoCo itself (I have multiple browser tabs open to modern and historical CoCo documentation). But damn it, this is *fun*.

## Things I would like to change
* Player speed per frame is a bit low, would like to speed this up
* Barrel and fireball behavior is completely inaccurate

## Things I'm not worried about
* The flicker. This game, from my analysis so far, seems to have two graphics buffers (the one that isn't displayed seems to overlap with the text screen, since they're not used at the same time, perhaps it's only used to store the blank level without objects). AFAIK Sailor Man, which Latham developed after this game, was *triple* buffered.
* The speed oscillation. 6809 is a new processor for me, I understand this is just due to processing multiple objects and updating either the offscreen buffer or the main one, and it's less advanced than Sailor Man.
* Bonus scoring. I kind of like that the hammer/jump/rivet/item bonuses track the hundreds digit of the timer, as it adds additional skill for point chasers. There *is* a difference between items and everything else, when the hundreds digit is 0 I believe that the items give 500 but hammer destroys and jumps only give you 100.

I welcome any pull requests from more experienced CoCo coders. If Chris Latham himself happens to come across this repo, do you have the source code in your possession still? Cheeky move there when you wrote to Rainbow about adding hiscore saving to the game lmao.

Binary disassembled with f9dasm using the crafted .info file that is present in the repo. If you add any labels or code/data definitions, please add them to the .info so that the f9disasm output is the best possible starting point. If you edit the .asm directly, please note your changes in a separate document or in a detailed commit message. I'm marking this as MIT license out of convenience. For any of the executables found in the repo, please visit their repo to determine their license. I have not modified any of them, so the source is available in those repos.

## Important files
* donkymod.asm - the current state of the disassembly, as of now direct output from f9dasm
* donkey.dsk - the disk image with the game on it, as used in a CoCo emulator or written to a disk
* donkey.bin - the extracted file, with LOADM/CLOADM preamble and postamble
* donkey-memmap.txt - a basic memory map of the game
* donkey.info - the file that gives f9dasm hints about labels and code/data separation
* donkey.mem - this *should* be a RAM dump of an emulator running the game. The text and graphics buffers seem to line up, but the entry point seems to be 0x20 bytes off, no idea what's up there.
* donkey.raw - the game file extracted from the disk image, with preamble and postabmle stripped
* theking.dsk - a copy of the game after the name was changed from "Donkey King" to "The King"
* lwar.exe, lwasm.exe, lwcc-cpp.exe, lwlink.exe, lwobjdump.exe - files generated from the [LWTOOLS](http://www.lwtools.ca) project
* ar2.exe, cecb.exe, decb.exe, makewav.exe, mamou.exe, os9.exe, and tocgen.exe - files generated from the [ToolShed](https://github.com/n6il/toolshed) project
* bin2mot.exe, mot2bin.exe - tools for going between binry and Motorola S-Record files, if it becomes handy
* f9dasm.exe - the actual disassembler, from the [f9dasm](https://github.com/Arakula/f9dasm) project