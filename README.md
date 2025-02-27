Introduction
============

> [!NOTE]
>
> 1.1.2.1440 release on 1 March

VxKex Extended is a set of API extensions for Windows 7 that allow some Windows 8, 8.1 and 10-exclusive applications to run on Windows 7.

To download and install, see the [releases page](https://github.com/tester9071348/VxKex-Extended/releases).

**Uninstalling the following softwares before installing is recommended:**

- **0patch Agent**
  It might cause Chromium-based browsers and JetBrains IDEs to crash after enabling VxKex Extended and running it.

- **MacType**
  It might cause all programs to fail to start after enabling VxKex Extended

After installation, usage is easy. Here are the ways to enable VxKex Extended:
1. Just right click on a program (.exe or .msi), open the Properties dialog, and select "VxKex" tab. Then, check the check box which says "Enable VxKex NEXT for this program", and try to run the program. For shortcuts, select "Shortcut" tab in the Properties dialog, click "Open file location" button, and then perform the actions above.
2. Find "VxKex NEXT Global Settings" from start menu and open it, click "Add" button, select a program (.exe or .msi), click "Open" button, and try to run the program.

![VxKex configuration GUI](/example-screenshot.png)

Some programs require additional configuration. There's a file called "**Application Compatibility List.docx**" inside the VxKex Extended installation folder (which is C:\Program Files\VxKex by default) which details these steps, but for the most part, all configuration is self-explanatory.

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
- Browservice
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

See the **Application Compatibility List.docx** file, which is installed together with VxKex Extended, for more information.

The majority of Qt6 applications will work, and many Electron applications will work as well.

**Q: Does VxKex Extended modify system files? Will it make my system unstable?**

**A**: VxKex Extended does not modify any system files. Its effect on the whole system is extremely minimal. No background services are used, no global hooks are installed, and the shell extensions and DLLs that are loaded have minimal impact and can be disabled if needed. You can rest assured that your Windows 7 will remain as stable as it always is.

**Q: Do I need to have specific updates installed?**

**A**: Users of Windows 7 without any updates can still use it, but many programs require Service Pack 1, KB2533623 (DllDirectories update), KB2670838 (Platform Update), KB4490628 (SSU from March 2019) and KB4474419 (Update for support SHA-256 and SHA-2) in order to run. It is a good idea to install those updates.

**Q: If I have ESUs (Extended Security Updates) installed, can I use VxKex Extended?**

**A**: Yes. There is no problem with ESUs.

**Q: Can I use this with Windows 8 or 8.1?**

**A**: Currently, VxKex Extended is designed for use only with Windows 7. If you use Windows 8 or 8.1, VxKex Extended will do nothing useful.

**Q: Can I remove VxKex or VxKex Extended after upgrading to Windows 8/8.1/10/11?**

**A**: Yes. If VxKex is installed, update it to VxKex Extended, then uninstall it from Control Panel or Settings.

**Q: How does VxKex Extended work?**

**A**: VxKex Extended works by loading a DLL into each program where VxKex Extended is enabled. This is accomplished through using the IFEO (Image File Execution Options) registry key.

Specifically, the "VerifierDlls" value is set to point to a VxKex Extended DLL. This DLL then loads into the process.

API extension is accomplished by editing the program's DLL import table so that instead of importing from Windows 8/8.1/10/11 DLLs, it imports VxKex Extended DLLs instead. These VxKex Extended DLLs contain implementations of Windows API functions which were introduced in newer versions of Windows.

**Q: How do I compile VxKex Extended?**

**A:** You need to install Visual Studio 2010 first, as it is the only version that is
compatible with VxKex Extended. After this, you need to compile both the x86 and x64
binaries of VxKex Extended (beginning with x86). VxKex Extended requires some x86 binaries
produced by compiling VxKex Extended in x86 first, before it can be used in x64.

The program "\01-Development Utilities\vautogen\vautogen.exe" will increment the version
information globally by 1 each time it is executed.

<!--KexPathCch -> KexDll -> KexGui -> KexW32ML -> KxCfgHlp -> KxAdvapi -> KxBase -> KxCom -> KxCrt -> KxCryp -> KxDx -> KxMi -> KxNet -> KxNt -> KxUia -> KxUser -> CpiwBypa -> KexCfg -> KexShlEx -> VxKexLdr -> VxlView -> KexSetup-->
<!-- - QEMU -->
