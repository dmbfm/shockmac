SOURCE CODE STRUCTURE
=====================

This directory contains the source code for the game itself, as opposed to the helper libraries that are found elsewhere.

The source code is made up of the following files. (This README is in progress; I have not characterized all of the files yet.)

* AI / Critters
  * [ai.c](AI.C)              - Lowlevel monster control, death, loot tables, etc.
  * [newai.c](NEWAI.C)        - Monster AI states, path finding, combat decisions
* Automap
  * [amap.c](AMAP.C)          - Automap bitmap rendering
  * [amaploop.c](AMAPLOOP.C)  - Automap interactive processing for fullscreen
  * [fullamap.c](FULLAMAP.C)  - Fullscreen automap setup and interfacing
  * [automap.c](AUTOMAP.C)    - MFD minimap automap view
* Resource management
  * [citres.c](CITRES.C)      - Load bitmaps from Resource system
  * [cybmem.c](CYBMEM.C)      - Manages dynamic memory & resource files
  * [statics.c](STATICS.C)    - Static memory allocations
  * [textmaps.c](TEXTMAPS.C)  - Terrain texture management
  * [gamestrn.c)(GAMESTRN.C)  - Game strings
* Combat
  * [combat.c](COMBAT.C)      - hit-scan weapon handling
  * [weapons.c](WEAPONS.C)    - projectile/beam weapon handling: shooting, reloading, etc.
  * [damage.c](DAMAGE.C)      - process taking damage for all kinds of things
* UI
  * [status.c](STATUS.C)      - "Biorhythm" display logic & rendering
  * [wrapper.c](WRAPPER.C)    - Front-end-ish stuff (options etc), but (maybe) not main menu
  * [movekeys.c](MOVEKEYS.C)  -- player movement keyboard controls
  * Multi-Function Display
    * [ammomfd.c](AMMOMFD.C)  - Display panel with list of weapons and ammo for each
    * [bark.c](BARK.C)        - Spontaneous messages from Shodan etc.
    * [biohelp.c](BIOHELP.C)  - If you have Bioscan upgrade, configure which "biorhythms" are displayed by [status.c]
    * [cardmfd.c](CARDMFD.C)  - Access card list
    * [cybermfd.c](CYBERMFD.C)- Cyberspace MFD display
    * [email.c](EMAIL.C)      - Email MFD and inventory display
    * [mfdgames.c](MFDGAMES.C)- MFD minigames
    * [hflip.c](HFLIP.C)        - Flip bitmap horizontally
* Audio
  * [audiolog.c](AUDIOLOG.C)  - Audio log player
  * [airupt.c](AIRUPT.C)      - Music mixing AI, music transition AI
  * [musicai.c](MUSICAI.C)    -- Music transition AI
  * [digifx.c](DIGIFX.C)      - Audio sound triggers, 3d spatializion via volume/pan, etc.
  * [sndcall.c](SNDCALL.C)    - Update audio & handle callbacks
* Trap/Trigger system, i.e. designer-created actions that respond to player/world/game events
  * "Trigger"   - An object that reacts when it detects player is in a certain place, has done a certain action, etc.
  * "Trap"      - Behaviors that designers can make happen in reaction to triggers
  * [trigger.c](TRIGGER.C)    - Trap implementations, some trigger detection, "comparator" system for conditional execution of traps
* Rendering
  * 3D view
    * [frmain.c](FRMAIN.C)      - Top-level function to call functions to render 3D scene, draw overlays, add SFX
    * [frcamera.c](FRCAMERA.C)  - Computer what 3D camera position/orientation to render from
    * [frclip.c](FRCLIP.C)      - Call CONE.C to find map tiles in frustum, then conservatively determine which are occluded
    * [cone.c](CONE.C)          - Determine which map grid cells are within a view frustum ("cone")
    * [frcompil.c](FRCOMPIL.C)  - Minor initialization & deal with map changing size (which never happens with the game, maybe could only happen in the integrated editor)
    * [gamesort.c](GAMESORT.C)  - Sort objects in a single map tile for rendering (complicated because of e.g. force bridge partitioning into top & bottom halves)
    * [frobj.c](FROBJ.C)        - Draw all objects in a single map tile using GAMESORT.C and GAMEOBJ.C
    * [gameobj.c](GAMEOBJ.C)    - 3D rendering of all object types
    * [frpipe.c](FRPIPE.C)      - Top-level terrain rendering functions, traverse map (along diagonals?), call draw_tile
    * [frpts.c](FRPTS.C)        - Allocate a 3D point, and incrementally compute its viewspace 3D coordinate
    * [frsetup.c](FRSETUP.C)    - Top-level terrain & overlay rendering
    * [frtables.c](FRTABLES.C)  - Tables describing the vertices & normals & etc of all the different terrain slope shapes
    * [frutil.c](FRUTIL.C)      - Utilities for helping with reading from id buffer
    * [frterr.c](FRTERR.C)      - Make and dispatch the terrain polygons 
    * [stars.c](STARS.C)        - Draw stars seen through windows in space station (w/optional gamma-corrected anti-aliasing)
  * Overlays
    * [handart.c](HANDART.C)    - Compute & manage hand art (i.e. gun at bottom)
    * [vitals.c](VITALS.C)      - Draw health & energy bars, and "status arrows"???
    * [leanmetr.c](LEANMETR.C)  - Interactive posture indicator ("lean meter")
  * Graphics effects
    * [effects.c](EFFECTS.C)    - Create & update animations
    * [palfx.c](PALFX.C)        - Palette effects
  * [render.c](RENDER.C)      - Draw "hack" cameras (POV view from camera in mfd/fullscreen), handle 360-ware in some form, cyberspace game-of-life?
  * [gr2ss.c](GR2SS.C)        - System Shock wrappers around 2d "gr" graphics functions
* Simulation
  * [gametime.c](GAMETIME.C)  - Update game time & run physics
  * [shodan.c](SHODAN.C)      - Track shodan's "opinion" of you based on what you've destroyed
* Uncategorized
  * [criterr.c](CRITERR.C)    - Critical error handling
  * [cyber.c](CYBER.C)        - Enter/exit cyberspace
  * [cybrnd.c](CYBRND.C)      - Random number generators
  * [drugs.c](DRUGS.C)        - Dermal patches - general processing, ticking, and specific effects
  * [saveload.c](SAVELOAD.C)  -- Saving & loading the game
  * [wares.c](WARES.C)        -- Management for loadable wares & upgrades
  * [hkeyfunc.c](HKEYFUNC.C)  -- Simple hotkey definitions
  * [map.c](MAP.C)            - Allocate & manange game map
* Unprocessed
  * faceobj.c
  * fixtrmfd.c
  * froslew.c
  * fullscrn.c
  * gameloop.c
  * gamerend.c
  * gamesys.c
  * gametime.c
  * gamewrap.c
  * gearmfd.c
  * grenades.c
  * hkeyfunc.c
  * hud.c
  * hudobj.c
  * init.c
  * input.c
  * invent.c
  * mainloop.c
  * mfdfunc.c
  * mfdgadg.c
  * mfdgump.c
  * mfdpanel.c
  * minimax.c
  * mlimbs.c
  * newmfd.c
  * objapp.c
  * objects.c
  * objload.c
  * objprop.c
  * objsim.c
  * objus.c
  * olh.c
  * olhscan.c
  * palx.c
  * pthfind.c
  * physics.c
  * player.c
  * plotware.c
  * popups.c
  * rendtool.c
  * schedule.c
  * screen.c
  * setup.c
  * sideicon.c
  * status.c
  * target.c
  * tfdirect.c
  * tfutil.c
  * tools.c
  * view360.c
  * viewhelp.c
  * vmail.c
