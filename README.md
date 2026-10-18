# Windows 3.0 on the Amstrad PC1512

**640 × 200 pixels · 16 colors · PC1512 built-in video**

An experimental display driver for Windows 3.0 real mode on the Amstrad PC1512's four-plane, 64 KB video hardware.

## [Download PC1512.ZIP →](https://github.com/astrobleem/oemdisplay-tandy/releases/download/experimental-displays-2026-10-12/PC1512.ZIP)

Ready-built driver, installation instructions, checksums and component notices. Bring your own Windows 3.0 installation; this is a driver packet, not a Windows Setup disk.

[Release notes](https://github.com/astrobleem/oemdisplay-tandy/releases/tag/experimental-displays-2026-10-12) · [Prerequisites](#prerequisites) · [Install](#install-in-a-clone) · [Rollback](#rollback-from-plain-dos) · [Source & support](#source--support)

![Windows 3.0 Program Manager over a 16-color test wallpaper, Amstrad PC1512 emulated in 86Box](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/ba980d4ccf9092c38ea22b006373f420d0f059e2/docs/pc1512/P86_11.PNG)

*86Box 6.0, emulated Amstrad PC1512 built-in planar video: Windows 3.0 Program Manager in 640×200×16. See the [88/88 test record](https://github.com/astrobleem/oemdisplay-tandy/blob/ba980d4ccf9092c38ea22b006373f420d0f059e2/docs/pc1512/P86CHK.JSN) and [tested evidence commit ba980d4](https://github.com/astrobleem/oemdisplay-tandy/commit/ba980d4ccf9092c38ea22b006373f420d0f059e2). Emulator evidence only; physical PC1512 hardware remains unqualified. One cursor-state case required recovery and retry, as described below.*

### Prerequisites

- Amstrad PC1512 built-in planar video, 8086 and normal 640 KB RAM. The PC1640, ordinary CGA, Tandy and PCjr use different video hardware.
- A bootable backup or disposable clone of an existing Windows 3.0 installation, with a plain-DOS recovery route.
- For the first reproduction, retain the EGA fonts/grabber configuration used by the recorded AT/EGA installation tests. Fresh CGA-class Setup/fonts/grabber integration is untested.

Read **README.TXT inside the ZIP** before making changes. The [exact published instructions](https://github.com/astrobleem/oemdisplay-tandy/blob/37b504be3619032f435381eded7d92a504d8d9da/experiments/DISPLAY3/PC1512.TXT) describe the qualified cloned-install route. Exit Windows completely before changing files.

### Install in a clone

1. Extract the complete ZIP into a new `C:\P15EXP` directory. Verify its `SHA256.SUM` on a modern host and back up the complete Windows installation/image.
2. From plain DOS, save `SYSTEM.INI`:

   ```dos
   COPY C:\WINDOWS\SYSTEM.INI C:\P15EXP\SYSBACK.INI
   ```

   Stop if `SYSBACK.INI` already exists. Record the old `display.drv` setting. If `C:\WINDOWS\SYSTEM\PC1512.DRV` already exists, preserve its original bytes separately.
3. Copy the driver:

   ```dos
   COPY C:\P15EXP\PC1512.DRV C:\WINDOWS\SYSTEM\PC1512.DRV
   ```

4. With a DOS text editor, change only `[boot]` → `display.drv` in `C:\WINDOWS\SYSTEM.INI` to `display.drv=PC1512.DRV`.
5. Start Windows in real mode:

   ```dos
   CD \WINDOWS
   WIN /R
   ```

Substitute your actual Windows directory consistently if it differs. PC1512 has dedicated video RAM and needs no `RESERVE`/`JRGUARD` step. Do not use the Tandy `WINXT` startup route or its palette animation.

### Rollback from plain DOS

Exit Windows completely, or reboot to DOS if Windows will not start. Restore the saved configuration:

```dos
COPY C:\P15EXP\SYSBACK.INI C:\WINDOWS\SYSTEM.INI
```

Restore any pre-existing `PC1512.DRV` you replaced. If other configuration changed, restore the complete installation/image backup. A newly added driver may remain inactive after restoring the old setting.

### Recorded results and limits

The packaged driver passed **88/88 final Windows 3.0 checks in 86Box 6.0**. Of 16 palette cursor cases, **15 passed on the first try; one required recovery and retry**. The rejected frame showed a crosshair at the correct hotspot; the cursor-state cause remains unresolved. See the [recorded checks](https://github.com/astrobleem/oemdisplay-tandy/blob/ba980d4ccf9092c38ea22b006373f420d0f059e2/docs/pc1512/P86CHK.JSN).

**Physical PC1512 hardware, the native Amstrad mouse port, real timing, fresh Windows Setup and DOS-box/grabber switching remain untested or unqualified.** Serial input was emulated. These results establish the recorded emulator scope, not general hardware compatibility.

![Windows arrow cursor over the PC1512 16-color test wallpaper in 86Box](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/ba980d4ccf9092c38ea22b006373f420d0f059e2/docs/pc1512/P86_05.PNG)

*86Box emulator capture: Windows arrow cursor over the 16-color test wallpaper. Both screenshots are original captures, not physical-hardware photos.*

### Source & support

This repository is the documentation and download front door. All implementation, builds, fixes, release binaries and issue tracking live in **[astrobleem/oemdisplay-tandy](https://github.com/astrobleem/oemdisplay-tandy)**.

- [Report a problem or request a change](https://github.com/astrobleem/oemdisplay-tandy/issues)
- [Matching adaptation/build/test source — DISP3SRC.ZIP](https://github.com/astrobleem/oemdisplay-tandy/releases/download/experimental-displays-2026-10-12/DISP3SRC.ZIP)
- [Release qualification — QUALIFY.JSON](https://github.com/astrobleem/oemdisplay-tandy/releases/download/experimental-displays-2026-10-12/QUALIFY.JSON)
- [Published SHA-256 checksums](https://github.com/astrobleem/oemdisplay-tandy/releases/download/experimental-displays-2026-10-12/SHA256SUMS)

Release/package source: [`37b504be3619032f435381eded7d92a504d8d9da`](https://github.com/astrobleem/oemdisplay-tandy/commit/37b504be3619032f435381eded7d92a504d8d9da). Runtime adaptation and screenshot evidence: [`ba980d4ccf9092c38ea22b006373f420d0f059e2`](https://github.com/astrobleem/oemdisplay-tandy/commit/ba980d4ccf9092c38ea22b006373f420d0f059e2).

`PC1512.ZIP` SHA-256: `8ef7691a10b4b9acd2bfb3647ec2a9fa025e0eab14aa863aa37fae604ef62ec8`.

Component notices and license scope are included in the packet's `NOTICE.TXT` and `LICENSE.TXT`; the derived driver is not blanket MIT-licensed. Windows, DOS, fonts/grabbers, ROMs, compilers and original DDK inputs are not included.
