# RetroArch module for hakchi

This is a hakchi/hakchi2 module which adds libretro cores and RetroArch front-end to your NES Mini.

It will automatically detect unsupported NES games and run them instead of the default emulator. Save states will work as usual.

It can also run games for other consoles. This pack already contains the following cores:
- fceumm (Famicom/Nintendo Entertainment System, many mappers, UNIF support)
- nestopia (Famicom/Nintendo Entertainment System, Famicom Disk System)

The following cores are available as additional modules (in core_modules / cores folder):
- snes9x2010 (Super Famicom/Super Nintendo)
- gambatte_libretro (Game Boy, Game Boy Color)
- mgba (Game Boy Advance)
- glupen64 (Nintendo 64)
- genesis_plus_gx (Sega Master System, Genesis/Mega Drive, Game Gear)
- stella (Atari 2600)
- mednafen_pce_fast (PC Engine/Turbografx 16)
- fb_alpha and fb_alpha_cps2 (various arcade machines)
- picodrive (Sega Master System, Genesis/Mega Drive, Game Gear, Sega 32X)

Extra RetroArch modules and modules created by other users (in core_modules_extra folder):
- mupen64plus (Nintendo 64)
- snes9x2002 (Super Famicom/Super Nintendo)
- snes9x2005 (Super Famicom/Super Nintendo)
- caprice32 (Amstrad CPC), fixed and built by D_Skywalk, provided by 1lokolo1/nesito
- fbalpha2012_neogeo (Neo-Geo), provided by 1lokolo1/nesito
- fuse (ZX Spectrum), fixed and built by D_Skywalk, provided by 1lokolo1/nesito
- dosbox (MS-DOS), provided by 1lokolo1/nesito  and asper
- mame2000 (various arcades machines), fixed and built by D_Skywalk, provided by 1lokolo1/nesito
- mame2003 (various arcades machines), provided by asper
- mednafen_ngp (Neo Geo Pocket), provided by asper
- gme (various game music formats), provided by asper
- handy (Atari Lynx), provided by asper (BIOS image required, consult module's readme.txt and libretro Wiki)
- pcsx_rearmed (Sony PlayStation), suggested by asper, built by D_Skywalk and provided by Jelmer (BIOS image required, consult module's readme.txt and libretro Wiki)
- emux_chip8 (CHIP-8), provided by asper
- fmsx (MSX, MSX 2), provided by asper (BIOS image required, consult module's readme.txt and libretro Wiki)
- mednafen_vb (Virtual Boy), provided by asper
- mednafen_wswan (WonderSwan, WonderSwan Color), provided by asper
- nxengine (Cave Story), provided by asper
- o2em (Odyssey2 / Videopac+), provided by asper (BIOS image required, consult module's readme.txt and libretro Wiki)
- prosystem (Atari 7800), provided by asper (BIOS image required, consult module's readme.txt and libretro Wiki)
- vecx (Vectrex), provided by asper
- yabause (Sega Saturn), provided by asper (BIOS image required, consult module's readme.txt and libretro Wiki)

## How to use this

If you are using hakchi2:
1. Make sure that you are using hakchi2 version 2.14 or newer.
2. Go to "releases" tab and download the newest retroarch_with_cores.zip.
3. Drag-and-drop it on hakchi2 window.
4. Press "OK" button and follow instructions.

That's all. You can play near all NES games now as well as SNES, Genesis, N64, etc.

### Important notes

- To use RetroArch for any NES game, just add "--retroarch" to command line arguments. Use it if some of your NES games glitches with original NES Mini's emulator.
- To open RetroArch settings menu press Select + Start in game.
- To add RetroArch shortcut to NES Mini's shell, download and drag-and-drop CloverApp.zip to hakchi2.
- You can re-enable bilinear filtering (smoothing) in RetroArch's settings (Settings —> Video —> Bilinear Filtering)
- Make sure that your FDS games have .fds extension (NOT .nes) if you want to run them with built-in emulator (kachikachi)

### Additional notes for expert users

- If you need to specify NES core, use "--retroarch --core fceumm" to use FCEUmm for this game or "--retroarch --core nestopia" to use Nestopia.
- To make your own RetroArch modules, use the structure from libretro_core_template.zip. Use exisiting modules as a reference.
- To add your own BIOS images for custom cores, use bios_template.zip (please read the readme.txt inside).
- If the file extension of your game is not supported by Hakchi2, you may need to change the path in command line arguments (in Hakchi2's game options) to make it point to the corresponding core.
- To load arcade games that come in the form of ZIP archives, you'll need to change /bin/zip in game's command line arguments to /bin/fba, /bin/mame2000, /bin/mame2003 or /bin/cps2 depending on the core needed for the game to run (look at "Additional Information" section for all avaiable /bin/<> commands). For some cores like Final Burn Alpha, BIOS image (e.g. neogeo.zip for Neo-Geo) must be in the game directory.
- Since version 0.5, you'll need to upload neogeo.zip only once. Just put neogeo.zip to any Neo-Geo game you want, synchronize and launch it once for every other game to work automatically or just upload neogeo.zip to RA's system folder using BIOS template. You won't have to include neogeo.zip anymore unless you uninstall hakchi and decide to install it again.
- To use Nestopia instead of FCEUmm, install use_nestopia.hmod module
- To use PicoDrive for all Genesis/Mega Drive games instead of Genesis Plus GX, install use_picodrive.hmod module. Make sure that picodrive module is installed before installing use_picodrive!
- To use SNES9x2005 for all SNES games instead of SNES9x2010, install use_snes9x2005.hmod module. Make sure that snes9x2005 module is installed before installing use_snes9x2005!
- To use SNES9x2002 for all SNES games instead of SNES9x2010, install use_snes9x2002.hmod module. Make sure that snes9x2002 module is installed before installing use_snes9x2002!
- To use Mupen64Plus for all N64 games instead of GLupeN64, install use_mupen64plus.hmod module. Make sure that mupen64plus module is installed before installing use_mupen64plus!
- If you want to use RetroArch's XMB UI instead of RGUI, install xmb_assets.hmod and change Menu Driver in Settings —> Driver —> Menu Driver to "xmb"

Executables and arguments for all available cores:

        - /bin/retroarch-clover <core> <rom> <clover_args>
          runs RetroArch with specified core,
          designed for executing from clover shell, 
          so it parses all clover arguments (saves, aspect ratio, etc.)
        - /bin/retroarch-mini [core] [rom] [args]
          runs RetroArch directly, without clover intergration
        - /bin/retroarch
          RetroArch binary
        - /bin/nes <rom> <clover_args>
          runs "fceumm" core or "nestopia" core
        - /bin/gb <rom> <clover_args>
          runs "gambatte" core
        - /bin/gbc <rom> <clover_args>
          runs "gambatte" core
        - /bin/gba <rom> <clover_args>
          runs "mgba" core
        - /bin/md <rom> <clover_args>
          runs "genesis_plus_gx" core
        - /bin/sms <rom> <clover_args>
          runs "genesis_plus_gx" core
        - /bin/gg <rom> <clover_args>
          runs "genesis_plus_gx" core
        - /bin/32x <rom> <clover_args>
          runs "picodrive" core
        - /bin/snes <rom> <clover_args>
          runs "snes9x2010", "snes9x2005" or "snes9x2002" core
        - /bin/snes10 <rom> <clover_args>
          runs "snes9x2010" core
        - /bin/snes02 <rom> <clover_args>
          runs "snes9x2002" core if snes9x2005 or snes9x2010 is installed as a main core
        - /bin/snes05 <rom> <clover_args>
          runs "snes9x2005" core if snes9x2002 or snes9x2010 is installed as a main core
        - /bin/n64 <rom> <clover_args>
          runs "glupen64" core or "mupen64plus" core
        - /bin/n64p <rom> <clover_args>
          runs "mupen64plus" core
        - /bin/n64g <rom> <clover_args>
          runs "glupen64" core
        - /bin/a26 <rom> <clover_args>
          runs "stella" core
        - /bin/pce <rom> <clover_args>
          runs "mednafen_pce_fast" core
        - /bin/fba <rom> <clover_args>
          runs "fb_alpha" core
        - /bin/cps2 <rom> <clover_args>
          runs "fb_alpha_cps2" core
        - /bin/neo <rom> <clover_args>
          runs "fbalpha2012_neogeo" core
        - /bin/cpc <rom> <clover_args>
          runs "caprice32" core
        - /bin/zx <rom> <clover_args>
          runs "fuse" core
        - /bin/dosbox <rom> <clover_args>
          runs "dosbox" core
        - /bin/mame2000 <rom> <clover_args>
          runs "mame2000" core
        - /bin/mame2003 <rom> <clover_args>
          runs "mame2003" core
        - /bin/ngp <rom> <clover_args>
          runs "mednafen_ngp" core
        - /bin/ngc <rom> <clover_args>
          runs "mednafen_ngp" core
        - /bin/gme <rom> <clover_args>
          runs "gme" core
        - /bin/lnx <rom> <clover_args>
          runs "handy" core
        - /bin/pcsx <rom> <clover_args>
          runs "pcsx_rearmed" core
        - /bin/ch8 <rom> <clover_args>
          runs "emux_chip8" core
        - /bin/msx <rom> <clover_args>
          runs "fmsx" core
        - /bin/vb <rom> <clover_args>
          runs "mednafen_vb" core
        - /bin/ws <rom> <clover_args>
          runs "mednafen_wswan" core
        - /bin/wsc <rom> <clover_args>
          runs "mednafen_wswan" core
        - /bin/nxengine <rom> <clover_args>
          runs "nxengine" core
        - /bin/o2em <rom> <clover_args>
          runs "o2em" core
        - /bin/a78 <rom> <clover_args>
          runs "prosystem" core
        - /bin/vec <rom> <clover_args>
          runs "vecx" core
        - /bin/yabause <rom> <clover_args>
          runs "yabause" core

## Known issues

- Nintendo 64 and CP System II save-states are not working, battery backups work fine
- Default CRT filter is not working, scanlines shader added instead but it's not working with all systems.

## Credits

NES Mini port by madmonkey

NES Mini shell integration by Cluster

Various additions, tweaks and fixes by pcm720

RetroArch/libretro project: https://www.libretro.com
Lakka project: www.lakka.tv

(c) 2017
