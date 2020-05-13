# SkyMM-NX

SkyMM-NX is a simple mod manager that runs on your Switch and provides an easy way to toggle mods on
and off.

SkyMM will attempt to discover all mods present in Skyrim's ROMFS on the SD card and present them through its interface.
Through the interface, you can toggle mods on or off, or change the load order by holding `Y`. Note that the load order
for pure replacement mods (lacking an ESP) will not be preserved when the respective mods are disabled.

When the save function is invoked, the INI and `Plugins` files will be modified accordingly and saved to the SD card.

Currently, the app requires that all mods follow a standard naming scheme:

- BSA files with a suffix must use a hyphen with one space on either side between the base name and the suffix
  - Example: `Static Mesh Improvement Mod - Textures.bsa`
  - Note that a mod may have exactly one non-suffixed BSA file
- BSA files with an associated ESP file must match the ESP's name, not including the suffix
  - Example: `Static Mesh Improvement Mod - Textures.bsa` matches `Static Mesh Improvement Mod.esp`
- All BSA files for a given mod must match each other in name
  - Example: `Static Mesh Improvement Mod - Textures.bsa` matches `Static Mesh Improvement Mod - Meshes.bsa`

Notes from 78:

This version works on the SX OS operating system; Make sure to use titles instead of content folder like some mods provide. There is some remaining junk functions from the atmosphere edition, but they should be harmless. The original maintainer has made the choice not to support SX OS, so this fork will remain here solely for those users that that don't like the limited scope of atmosphere/partners.

### To-do

- Graceful error handling
  - I've done minimal edge testing so far, so the app probably won't respond well to most less-than-ideal
    conditions (e.g. missing or malformed files)
- Proper graphical interface
  - This isn't high priority since the console interface seems to work well enough for now
- INI injection support
  - Injecting INIs is easy; the hard part is disabling them in a sane way

### Building

SkyMM-NX depends on `devkitA64`, `libnx`, and `switch-tools` to compile. These packages are installable through
[devkitPro pacman](https://devkitpro.org/wiki/devkitPro_pacman).

Once all dependencies have been satisfied, simply run `make` in the project directory.

Notes From 78:

The tools involved in building are mostly based on Arch Linux's Pacman; If you are familiar with it, you will know that there is both no documentation and no easily accessible resources to use the basic system... So, use the Windows installer version of devkitpro. This downloads an MSYS instance with everything prebuilt. You will also need to download GCC with Pacman. Look this up on something like stackexchange. Afterwards, you will need to get inipp.h from the original maintainer and place it in the aptly named folder...

After that headache, it should be a simple 'make' command away from producing an NRO. However, I will just provide one becauseI am not heartless.

### License

SkyMM-NX is made available under the
[MIT License](https://github.com/caseif/SkyrimNXModManager/blob/master/LICENSE). It may be used, modified, and
distributed within the bounds of this license.
