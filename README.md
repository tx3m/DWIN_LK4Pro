# DWIN_LKxPro

Touch screen firmware for the **Longer LK4 Pro** DWIN screen, for use with
[Marlin-LK4Pro](https://github.com/tx3m/Marlin-LK4Pro) (Marlin `bugfix-2.1.x` with the DGUS Reloaded screen driver).

This is a continuation of [Guizz27/DWIN_LK4Pro](https://github.com/Guizz27/DWIN_LK4Pro), which is no longer
maintained. It includes jgbrown54's JGB2.2B update and the changes needed for current Marlin.

> **Use at your own risk.** The screen firmware and the printer firmware must be updated together.
> Only use it with [Marlin-LK4Pro](https://github.com/tx3m/Marlin-LK4Pro).

## Compatibility

- Tested on the Longer LK4 Pro. The LK5 Pro and Alfawise U30 Pro may work but are untested.
  The boot screen shows the Longer3D logo.
- **Do not update a screen whose version (in the About screen) contains "TL5", "DWJT" or "DWJTB".** These screens
  can't be updated with this firmware.

## Installing

You need an SD card of **32 GB or less**, formatted **FAT32** with **4096-byte allocation units**.

1. Download `DWIN_SET.zip` from the [Releases](https://github.com/tx3m/DWIN_LK4Pro/releases) page.
2. Unzip it into a folder called `DWIN_SET` in the root of the SD card.
3. Turn the printer off.
4. Insert the card into the screen's own SD card slot. The screen mounting frame has to be removed to reach it.
5. Turn the printer on and wait until the screen shows "end".
6. Turn the printer off, remove the card and turn it on again.

Then flash the matching [Marlin-LK4Pro](https://github.com/tx3m/Marlin-LK4Pro) printer firmware.

For a detailed walkthrough of both updates, see Baddflash's
[LK4 Pro Firmware Tutorial](https://github.com/Baddflash/LK4-Pro-Firmware-Tutorial) (written for the earlier
versions, but the steps are the same).

## Building from source

1. Run `BuildRelease.bat`. It creates `release/DWIN_SET` with the file names and image rotation the screen needs.
2. Copy that `DWIN_SET` folder to the SD card and follow the installation steps above.

To edit the screens, use DWIN's DGUS editor (DGUS V7.648, available from DWIN) and open `DWprj.hmi`.
`TouchConfig.xls` and `DisplayConfig.xls` list every button and display field with the address it uses. The names
match `DGUS_Addr.h` in Marlin-LK4Pro, and the addresses must stay in sync with it.

## Changes

**This fork (tx3m), for Marlin `bugfix-2.1.x`:**

- Addresses aligned with Marlin's DGUS Reloaded driver: Resume button `0x2009`, Pause/Resume icons `0x31BE`,
  elapsed time `0x30E8`, progress `0x30F7`, screen version `0x2050`.
- Bed leveling probing screen reworked (grid layout and background).
- Load and Unload buttons swapped on the filament screen.
- Button and field positions adjusted on several screens.
- Names in `TouchConfig.xls` and `DisplayConfig.xls` match Marlin's `DGUS_Addr.h`.

**jgbrown54 (JGB2.2B), for Marlin 2.1.2.1:** separate Pause, Resume and Abort buttons, new bed leveling grid,
redesigned home, print status, move, filament, advanced settings and runout screens, a new G-code keyboard
([Guizz27/DWIN_LK4Pro#22](https://github.com/Guizz27/DWIN_LK4Pro/issues/22)), status messages on more screens, and
design sources for the icons and screens.

**Guizz27:** the original screen design that replaced Longer's stock screens, including the advanced settings,
EEPROM, runout, PID and G-code entry screens.

The pictures in `Screenshots/` show Guizz27's original design.

## Credits

- [Guizz27](https://github.com/Guizz27): original screen firmware and LKx Pro Marlin port.
- [jgbrown54](https://github.com/jgbrown54): JGB2.2B update, published here with his permission.
- [tx3m](https://github.com/tx3m): update for current Marlin.
- [Baddflash](https://github.com/Baddflash): installation tutorial.
- The Longer3D logo belongs to Longer.

## License

Published under the [GPL v3 license](/LICENSE), which Guizz27 chose for the original project. You may use, modify and
share this firmware, but anything you distribute must stay open and come with its source. Pointing people to this
repository satisfies that.

## Disclaimer

You use this firmware at your own risk. The authors are not responsible for any damage it may cause.
