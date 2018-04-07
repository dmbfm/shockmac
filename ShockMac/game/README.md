SOURCE CODE STRUCTURE
=====================

This directory contains the source code for the game itself, as opposed to the helper libraries that are found elsewhere.

The source code is made up of the following files.The source code is divided into the following systems.

* AI / Critters
 * [ai.c](/nothings/shockmac/blob/master/ShockMac/game/AI.C)             - Lowlevel monster control, death, loot tables, etc.
 * [newai.c](/nothings/shockmac/blob/master/ShockMac/game/NEWAI.C)       - Monster AI states, path finding, combat decisions
 * [airupt.c](/nothings/shockmac/blob/master/ShockMac/game/AIRUPT.C)     - Music mixing AI, music transition AI
* Automap
 * [amap.c](/nothings/shockmac/blob/master/ShockMac/game/AMAP.C)         - Automap bitmap rendering
 * [amaploop.c](/nothings/shockmac/blob/master/ShockMac/game/AMAPLOOP.C) - Full screen automap processing
 * [automap.c](/nothings/shockmac/blob/master/ShockMac/game/AUTOMAP.C)   - MFD minimap automap view
* UI
 * [status.c](/nothings/shockmac/blob/master/ShockMac/game/STATUS.C)     - "Biorhythm" display logic & rendering
 * Multi-Function Display
  * [ammomfd.c](/nothings/shockmac/blob/master/ShockMac/game/AMMOMFD.C)  - Display panel with list of weapons and ammo for each
  * [bark.c](/nothings/shockmac/blob/master/ShockMac/game/BARK.C)        - Spontaneous messages from Shodan etc.
  * [biohelp.c](/nothings/shockmac/blob/master/ShockMac/game/BIOHELP.C)  - If you have Bioscan upgrade, configure which "biorhythms" are displayed by [status.c]
* Audio
 * [audiolog.c](/nothings/shockmac/blob/master/ShockMac/game/AUDIOLOG.C) - Audio log player

<!--done A*.c, B*.c--!>
