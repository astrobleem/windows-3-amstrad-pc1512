# Windows 3.0 on Amstrad PC1512

**[Download PC1512.ZIP](https://github.com/astrobleem/oemdisplay-tandy/releases/download/windows-xt/PC1512.ZIP)**

For PC1512 built-in video, an 8086, 640 KB, DOS 3.20+ and an installed Windows
3.0 in real mode. Not PC1640 or ordinary CGA. The packet includes the driver,
matching original fonts, grabber and startup artwork.

## Install

1. Extract all files from PC1512.ZIP to `C:\P15EXP`. Exit Windows to DOS.
2. Run `C:\P15EXP\INSTALL`.
3. In Windows Setup choose Display, Other, `C:\P15EXP`, then
   **Amstrad PC1512 640x200 16 colors**. Complete Setup and return to DOS.
4. Start Windows with `C:\P15EXP\P15WIN`.

For Windows outside `C:\WINDOWS`, pass its drive and directory to both entries,
for example `INSTALL D: \WIN30` and `P15WIN D: \WIN30`.
Dedicated video RAM needs no reservation helper.

Native Setup and 640x200 startup passed on an emulated PC1512. Physical hardware,
the Amstrad mouse port and DOS-box switching remain unqualified. Windows 3.1
is not supported.

![Windows 3.0 on emulated PC1512](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/main/docs/pc1512/P86_11.PNG)

[Packaged instructions](https://github.com/astrobleem/oemdisplay-tandy/blob/main/tools/CURRENT/GUIDES/PC1512.TXT) |
[Technical details](https://github.com/astrobleem/oemdisplay-tandy/blob/main/docs/PC1512.MD) |
[Report a problem](https://github.com/astrobleem/oemdisplay-tandy/issues).
Implementation lives in [oemdisplay-tandy](https://github.com/astrobleem/oemdisplay-tandy).
