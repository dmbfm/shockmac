SOURCE CODE STRUCTURE
=====================

This directory contains the source code for the game itself, as opposed to the helper libraries that are found elsewhere.

The source code is made up of the following files. (This README is in progress; I have not characterized all of the files yet.)

* AI / Critters
  * [ai.c](AI.C)              - Lowlevel monster control, death, loot tables, etc.
  * [newai.c](NEWAI.C)        - Monster AI states, path finding, combat decisions
  * [pathfind.c](PATHFIND.C)  - Finds paths from point A to point B, accounting for complex terrain
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
  * [gamestrn.c](GAMESTRN.C)  - Game strings
* Combat
  * [combat.c](COMBAT.C)      - hit-scan weapon handling
  * [weapons.c](WEAPONS.C)    - projectile/beam weapon handling: shooting, reloading, etc.
  * [damage.c](DAMAGE.C)      - process taking damage for all kinds of things
* UI
  * [status.c](STATUS.C)      - "Biorhythm" display logic & rendering
  * [wrapper.c](WRAPPER.C)    - Front-end-ish stuff (options etc), but (maybe) not main menu
  * [movekeys.c](MOVEKEYS.C)  - player movement keyboard controls
  * [hkeyfunc.c](HKEYFUNC.C)  - Game hotkeys/shortcuts (including cheat keys)
  * [hud.c](HUD.C)            - Various hud elements: compass, stats, damage feedback
  * [hudobj.c](HUDOBJ.C)      - Set HUDOBJ_INST flag tested by IS_HUDOBJ() used to clip object rendering to hud
  * [invent.c](INVENT.C)      - Inventory manipulation / display (trigger actions, use patches, activate grenade, etc)
  * [olh.c](OLH.C)            - On-line help, gives hints during med lab section
  * [olhscan.c](OLHSCAN.C)    - Searches screen for "best" (centermost?) object to give hint
  * [screen.c](SCREEN.C)      - Top-level 2D UI screen display/mananagement
  * [popups.c](POPUPS.C)      - Make cursor from dynamic text (hover popups?)
  * [vmail.c](VMAIL.C)        - Video Mail feedback about plot advances (mining laser, groves, etc)
  * [sideicon.c](SIDEICON.C)  - Side icon (at left & right side of top half of screen) rendering & interaction
  * Multi-Function Display
    * [mfdfunc.c](MFDFUNC.C)  - MFD for weapons, shield, ammo, grenades, hardware, drugs, misc objects
    * [ammomfd.c](AMMOMFD.C)  - MFD center display with list of weapons and ammo for each
    * [mfdgump.c](MFDGUMP.C)  - MFD for container inventory (e.g. corpses)
    * [mfdpanel.c](MFDPANEL.C)- MFD for access panels (mini-puzzles + solvers)
    * [fixtrmfd.c](FIXTRMFD.C)- MFD for fixtures--brought up when clicking on buttons in the world that display something in MFD
    * [cybermfd.c](CYBERMFD.C)- MFD Cyberspace display
    * [bark.c](BARK.C)        - MFD Spontaneous messages from Shodan etc.
    * [cardmfd.c](CARDMFD.C)  - MFD with Access card list
    * [email.c](EMAIL.C)      - MFD and inventory display of email
    * [target.c](TARGET.C)    - MFD for targetware
    * [view360.c](VIEW360.c)  - MFD for 360-view: 3D canvases & rendering, MFD support, ware-interaction
    * [biohelp.c](BIOHELP.C)  - MFD for Bioscan upgrade, configure which "biorhythms" are displayed by [status.c]
    * [gearmfd.c](GEARMFD.C)  - MFD for "gear", whatever that is
    * [viewhelp.c](VIEWHELP.C)- MFD for "View Help" (?!?)
    * [mfdgames.c](MFDGAMES.C)- MFD minigames
    * [newmfd.c](NEWMFD.C)    - manager of MFDs
    * [minimax.c](MINIMAX.C)  - Minimax solver for Tic-Tac-Toe minigame
    * [hflip.c](HFLIP.C)      - Flip bitmap horizontally
    * [plotware.c](PLOTWARE.C)- Feedback about ??? in inventory panel (need to watch let's play to refresh my memory)
    * [mfdgadg.c](MFDGADG.C)  - MFD "gadgets" (widgets)
* Audio
  * [audiolog.c](AUDIOLOG.C)  - Audio log player
  * [airupt.c](AIRUPT.C)      - Music mixing AI, music transition AI
  * [musicai.c](MUSICAI.C)    - Music transition AI
  * [digifx.c](DIGIFX.C)      - Audio sound triggers, 3d spatializion via volume/pan, etc.
  * [sndcall.c](SNDCALL.C)    - Update audio & handle callbacks
  * [mlimbs.c](MLIMBS.C)      - Dynamic music handling
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
    * [star.c](STAR.C)          - Draw stars seen through windows in space station (w/optional gamma-corrected anti-aliasing)
    * [rendtool.c](RENDTOOL.C)  - Misc utility functions for rendering
  * Overlays 
    * [gamerend.c](GAMEREND.C)  - Special effects dealty/life overlays, player beam weapon, handart (gun etc), emp effects(?), Shodan end-game screen-takeover
    * [handart.c](HANDART.C)    - Compute & manage hand art (i.e. gun at bottom)
    * [hand.c](hand.c)          - hand art (gun) animation
    * [vitals.c](VITALS.C)      - Draw health & energy bars, and "status arrows"???
    * [leanmetr.c](LEANMETR.C)  - Interactive posture indicator ("lean meter")
  * Graphics effects
    * [effects.c](EFFECTS.C)    - Create & update animations
    * [palfx.c](PALFX.C)        - Palette effects
  * [render.c](RENDER.C)      - Draw "hack" cameras (POV view from camera in mfd/fullscreen), handle 360-ware in some form, cyberspace game-of-life?
  * [gr2ss.c](GR2SS.C)        - System Shock wrappers around 2D "gr" graphics functions
  * [objload.c](OBJLOAD.C)    - Load art for objects (e.g. preload for level)
* Simulation
  * [gametime.c](GAMETIME.C)  - Update game time & run physics
  * [shodan.c](SHODAN.C)      - Track shodan's "opinion" of you based on what you've destroyed
  * [froslew.c](FROSLEW.C)    - Move the camera through the world
  * [gamesys.c](GAMESYS.C)    - various sims: do nearby-object sim (sound, music AI, shodan-appearing-on-displays), player fatigue, shodan-overlay sim, run continuous triggers, check player in hazards, close panel mfds after leaving, sim once-a-second stuff
  * [grenades.c](GRENADES.C)  - Do grenade timing, all explosions
  * [physics.c](PHYSICS.C)    - player physics + throwing physics, interface to EDMS 
  * [schedule.c](SCHEDULE.C)  - Delayed event management including all processing of outcomes
  * [drugs.c](DRUGS.C)        - Dermal patches - general processing, ticking, and specific effects
  * [wares.c](WARES.C)        - Simulation of loadable wares & upgrades
  * "Terrain Function" (physics representation of terrain)
    * [faceobj.c](FACEOBJ.C)  - Objects that behave like map faces
    * [tfdirect.c](TFDIRECT.C)- Terrain-map-data-to-polygon conversion
    * [tfutil.c](TFUTIL.C)    - Interface to physics?
* Top-level
  * Main loop
     * [mainloop.c](MAINLOOP.C)  - Loop over frames, dispatching to current mode's fullscreen mainloop function (amaploop, gameloop)
     * [gameloop.c](GAMELOOP.C)  - Main game loop, runs or doesn't run other once-per-frame systems
  * [init.c](INIT.C)          - Central place calling all other initialization functions; fade-in splash screen; exit message
  * [player.c](PLAYER.C)      - Initialize player data structure, plus misc player updating
  * [setup.c](SETUP.C)        - Difficulty-setting screen
  * [input.c](INPUT.C)     - Keyboard input, mouse interactions in 3D, input from VR headsets & Spaceball
  * [cyber.c](CYBER.C)        - Enter/exit cyberspace
  * [map.c](MAP.C)            - Allocate & manange game map
  * [fullscrn.c](FULLSCRN.C)  - Fullscreen game mode management - handlers, overlays, double buffer
* Game objects
  * [objapp.c](OBJAPP.C)      - Tables for introspecting object data for save/load and editor(?)
  * [objects.c](OBJECTS.C)    - object array management: alloc/free slots etc.
  * [objprop.c](OBJPROP.C)    - convert between triples and subclass+offset
  * [objsim.c](OBJSIM.C)      - full-fledged object creation/destruction; determine art/model for rendering in 3D
  * [objuse.c](OBJUSE.C)      - player interaction with objects
* Serialization
  * [gamewrap.c](GAMEWRAP.C)  - High-level save/load
  * [saveload.c](SAVELOAD.C)  - Low-level save/load
* Utilities
  * [cybrnd.c](CYBRND.C)      - Random number generators
  * [criterr.c](CRITERR.C)    - Critical error handling
  * [tools.c](TOOLS.C)        - Utility functions, mostly for displaying 2D UI
