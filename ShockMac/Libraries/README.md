SOURCE CODE STRUCTURE
=====================

This subdirectory contains code that was used by multiple Looking Glass games.

The source code is divided into the following directories. This documentation
is in progress; none of the subdirectories named below have any documentation yet.
<!-- Each directory contains a readme documenting the files in that directory. --!>

* [2D](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/2D/Source) - Graphics code on 2D pixel grids, including texture mappers
* [3D](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/3D/Source) - Graphics code that operates on 3D points and objects, including transformations & BSP-tree-based object renderer
* [AFILE](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/AFILE/Source) - Movie player for cutscenes (supports multiple formats including a custom movie player for System Shock CD written by Rex Bradford)
* [DSTRUCT](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/DSTRUCT/Source) - General purpose data structures (array/homogenous heap, hash table, linked list, priority queue)
* [EDMS](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/EDMS/Source) - Physics engine
* [FIX](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/FIX/Source) - Fixed-point math library (floating point hardware was not universally available on x86 PCs in 1994)
* [H](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/H) - Shared headers with no corresponding source
* [INPUT](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/INPUT/Source) - Input device handling (keyboard, mouse)
* [LG](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/LG/Source) - Core library: logging, sprintf replacement, memory management
* [PALETTE](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/PALETTE/Source) - Palette fading/cycling effects
* [RES](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/RES/Source) - Data resource manager
* [RND](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/RND/Source) - Random number generation
* [SND](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/SND/Source) - Sound management. The original used John Miles' AIL for audio mixing, but that's commented out in this version in favor of a mac-specific solution.
* [UI](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/UI/Source) - User interface toolkit: cursor rendering, widget implementations, hotkey handling, etc.
* [VOX](https://github.com/nothings/shockmac/tree/master/ShockMac/Libraries/VOX/Source) - Voxel graphics library used for some of the enemies in cyberspace
