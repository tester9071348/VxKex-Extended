Introduction
============

Ext7 is a set of API extensions for Windows 7 that allow some Windows 8, 8.1 and 10-exclusive applications to run on Windows 7.

To download and install, see the [releases page](https://github.com/tester9071348/Ext7/releases).

**Uninstalling the following softwares before installing is recommended:**

- **0patch Agent**
It might cause Chromium-based browsers and JetBrains IDEs to crash after enabling Ext7 and running it.

- **MacType**
It might cause all programs to fail to start after enabling Ext7

After installation, usage is easy. Here are the ways to enable Ext7:
1. Just right click on a program (.exe or .msi), open the Properties dialog, and select "VxKex" tab. Then, check the check box which says "Enable VxKex NEXT for this program", and try to run the program. For shortcuts, select "Shortcut" tab in the Properties dialog, click "Open file location" button, and then perform the actions above.
2. Find "VxKex NEXT Global Settings" from start menu and open it, click "Add" button, select a program (.exe or .msi), click "Open" button, and try to run the program.

![VxKex configuration GUI](/example-screenshot.png)

Some programs require additional configuration. There's a file called "**Application Compatibility List.docx**" inside the Ext7 installation folder (which is C:\Program Files\VxKex by default) which details these steps, but for the most part, all configuration is self-explanatory.

If you are a developer, source code is provided as a zip and tar.gz files on the releases page. Compilation
instructions are at the bottom of this file.

FAQ
===

**Q: What applications are supported?**

**A**: The list of compatible applications includes, but is not limited to:

- Anki
- Bespoke Synth
- Blender
- Blockbench
- Calibre
- Chromium (including Ungoogled Chromium)
- Citra
- Commander Wars
- CopyQ
- Cygwin
- Dasel
- Discord
- ElectronMail
- Firefox
- FlareSolverr
- GIMP
- GitHub Desktop
- HandBrake
- Kate
- Kodi
- Life is Strange: True Colors
- Listary
- Miru
- MKVToolNix
- MongoDB
- MPC-Qt
- MPV
- MPV.NET
- Opera
- osu!lazer
- Python
- qBittorrent
- QEMU
- QMMP
- Qt Creator
- RedNotebook
- Rufus
- Steel Bank Common Lisp
- Signal
- SpaceEngine
- Spotify
- StaxRip
- Steinberg SpectraLayers
- TeamTalk
- Universe Sandbox
- VSCode and VSCodium
- Webcord
- WinDbg (classic from Windows 11 SDK, and preview)
- Yuzu (gameplay was not tested)
- Zig
- Zoner Photo Studio

See the **Application Compatibility List.docx** file, which is installed together with Ext7, for more information.

The majority of Qt6 applications will work, and many Electron applications will work as well.

**Q: Does Ext7 modify system files? Will it make my system unstable?**

**A**: Ext7 does not modify any system files. Its effect on the whole system is extremely minimal. No background services are used, no global hooks are installed, and the shell extensions and DLLs that are loaded have minimal impact and can be disabled if needed. You can rest assured that your Windows 7 will remain as stable as it always is.

**Q: Do I need to have specific updates installed?**

**A**: Users of Windows 7 without any updates can still use it, but many programs require Service Pack 1, KB2533623 (DllDirectories update) and KB2670838 (Platform Update) in order to run. It is a good idea to install those updates.

**Q: If I have ESUs (Extended Security Updates) installed, can I use Ext7?**

**A**: Yes. There is no problem with ESUs.

**Q: Can I use this with Windows 8 or 8.1?**

**A**: Currently, Ext7 is designed for use only with Windows 7. If you use Windows 8 or 8.1, Ext7 will do nothing useful.

**Q: Can I remove VxKex or Ext7 after upgrading to Windows 8/8.1/10/11?**

**A**: Yes. If VxKex is installed, update it to Ext7, then uninstall it from control panel.

**Q: How does Ext7 work?**

**A**: Ext7 works by loading a DLL into each program where Ext7 is enabled. This is accomplished through using the IFEO (Image File Execution Options) registry key.

Specifically, the "VerifierDlls" value is set to point to a Ext7 DLL. This DLL then loads into the process.

API extension is accomplished by editing the program's DLL import table so that instead of importing from Windows 8/8.1/10/11 DLLs, it imports Ext7 DLLs instead. These Ext7 DLLs contain implementations of Windows API functions which were introduced in newer versions of Windows.

**Q: How do I compile Ext7?**

**A:** You need to install Visual Studio 2010 first, as it is the only version that is
compatible with Ext7. After this, you need to compile both the x86 and x64
binaries of Ext7 (beginning with x86). Ext7 requires some x86 binaries
produced by compiling Ext7 in x86 first, before it can be used in x64.

The program "\01-Development Utilities\vautogen\vautogen.exe" will increment the version
information globally by 1 each time it is executed.

KexPathCch -> KexDll -> KexGui -> KexW32ML -> KxCfgHlp -> KxAdvapi -> KxBase -> KxCom -> KxCrt -> KxCryp -> KxDx -> KxMi -> KxNet -> KxNt -> KxUia -> KxUser -> CpiwBypa -> KexCfg -> KexShlEx -> VxKexLdr -> VxlView -> KexSetup

Ignore any warnings

Screenshots
============
**Browservice v0.9.11.0**
![Browservice v0.9.11.0](/bs.png)

**Chromium 132**
![Chromium 132](/ch.png)

**Firefox 134.0.2**
![Firefox 134.0.2](/ff.png)

**Ungoogled Chromium 132**
![Ungoogled Chromium 132](/uc.png)
