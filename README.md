# Windows 3.0 on Amstrad PC1512

**640x200, 16 colors. [Download PC1512.ZIP](https://github.com/astrobleem/oemdisplay-tandy/releases/download/experimental-displays-2026-10-12/PC1512.ZIP)**

For Amstrad PC1512 built-in video, 8086 and 640 KB. **Not PC1640 or ordinary CGA.**
Use an existing Windows 3.0 real-mode installation. The driver is ready built;
there is no automatic installer or fresh Windows Setup integration.

## Install

1. Extract the ZIP to `C:\P15EXP` and exit Windows completely to DOS.
2. Copy the driver:

   ```bat
   COPY C:\P15EXP\PC1512.DRV C:\WINDOWS\SYSTEM\PC1512.DRV
   ```

3. In `C:\WINDOWS\SYSTEM.INI`, set the `display.drv` line under `[boot]` to
   `display.drv=PC1512.DRV`. Keep the other settings, fonts and grabber.
4. Start Windows:

   ```bat
   C:
   CD \WINDOWS
   WIN /R
   ```

Use your actual Windows directory if different. Dedicated video RAM needs no
RESERVE/JRGUARD step. Use ordinary Windows startup; the Tandy WINXT launcher
and palette animation are for other hardware. This packet keeps your existing
WIN.COM and its startup logo behavior.

## Known limits

The driver passed 88/88 final Windows checks in 86Box. The recorded runs used
an existing AT/EGA installation with EGA fonts/grabber and emulated serial input.
One cursor-state case needed a retry; its cause is unresolved. Physical PC1512,
the native mouse port, fresh Windows Setup and DOS-box switching are unqualified.
Windows 3.1 is not supported.

![Windows 3.0 in the Amstrad PC1512 emulator](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/main/docs/pc1512/P86_11.PNG)

## Change back or get help

From plain DOS, use Windows Setup to restore your previous display, or restore
the previous `display.drv` value. The copied driver is inactive afterward.

[Detailed guide](https://github.com/astrobleem/oemdisplay-tandy/blob/main/experiments/DISPLAY3/PC1512.TXT) ·
[Technical details](https://github.com/astrobleem/oemdisplay-tandy/blob/main/docs/PC1512.MD) ·
[Report a problem](https://github.com/astrobleem/oemdisplay-tandy/issues).
Component notices are included in the download.
This repository is the front door; implementation lives in [oemdisplay-tandy](https://github.com/astrobleem/oemdisplay-tandy).
