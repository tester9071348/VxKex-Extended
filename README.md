Introduction
============

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
  - The first time you open the application, a popup may appear complaining that it could not initialize the video driver. Simply start the application again and it will work. Subsequent launches will not have this problem.
- Bespoke Synth
- Blender
  - Installer does not work. Use the portable version.
- Blockbench
- Browservice
  - Add this to command line: --chromium-args=disable-gpu
- Calibre
- Chromium (including Ungoogled Chromium)
  - There is a known issue with some debug builds displaying a crash dialog on some websites. It is harmless and you can just minimize the dialog.
- Citra
- Commander Wars
- CopyQ
- Cygwin
- Dasel
- Discord
- ElectronMail
- Firefox
  - Don't enable version spoof, only enable VxKex Extended. An error dialog may occur under some conditions after quitting the browser.
- FlareSolverr
- GIMP
  - Installer requires version spoof to Windows 10. Main GIMP EXE requires VxKex Extended enabled to avoid error messages and broken Python features. You might see some Python-related error messages in the console. These are network related and do not represent a real issue.
- GitHub Desktop
  - Enable VxKex Extended for the installer before installing. No version spoof needed. Enable VxKex Extended for the app after installing as well (%LocalAppData%\GitHubDesktop\GitHubDesktop.exe).
- HandBrake
  - Requires version spoof to Windows 10. .NET Desktop Runtime 6.0.x is required. Will crash without. If it crashes at startup please ensure the .NET Desktop Runtime is installed. After opening HandBrake, go to Tools->Preferences->Advanced and make sure the "Run each queued job in a separate worker process" checkbox is NOT CHECKED. This feature doesn't work but luckily it isn't very important.
- Kate
- Kodi
  - Installer requires version spoof to Windows 8.1, works afterwards without VxKex Extended.
- Life is Strange: True Colors
  - Without VxKex Extended, this game may not open due to missing xinput1_4.dll, and/or may crash after a short amount of time due to faulty error handling code. Known issue: The game shows a crash dialog after exiting. This does not affect the functionality of the game.
- Listary
  - Installer requires version spoof to Windows 10. Listary EXE requires VxKex Extended enabled, version spoof to Windows 10 is recommended, otherwise automatic updater will not work.
- Miru
- MKVToolNix
- MongoDB
- MPC-Qt
- MPV
- MPV.NET
  - .NET Desktop Runtime 6.0.x is required.
- Opera
  - Installer requires version spoof to Windows 10. Opera EXE requires VxKex Extended enabled, but no version spoof is needed.
- osu!lazer
  - Requires version spoof to Windows 8.1. After installation, go to %LocalAppData%\osulazer and enable VxKex Extended for Update.exe with version spoof to Windows 8.1. An error dialog may appear during installation. It is harmless and may be dismissed.
- Python
  - Installer works with version spoof to Windows 10. In order to run Python, you must enable VxKex Extended for python.exe and pythonw.exe, which are located in the Python installation folder. The default installation folder is %LocalAppData%\Programs\Python. No version spoof is required. In order to be able to uninstall Python, you can use the installer that has exact same version of installed Python. You can also enable VxKex Extended and version spoof to Windows 10 for the uninstaller. The uninstaller is located at "%LocalAppData%\Package Cache" inside one of the folders. It is usually the only EXE file present. Due to the issues with the uninstaller, it is recommended that you only use the portable version of Python.
- qBittorrent
- QEMU
- QMMP
- Qt Creator
- RedNotebook
- Rufus
- Steel Bank Common Lisp
- Signal
  - Installer requires version spoof to Windows 10. After installation you may see an error message saying that DiscardVirtualMemory could not be found. Ignore it. Enable VxKex Extended for Signal.exe in %LocalAppData%\Programs\signal-desktop. No version spoof is required.
- SpaceEngine
- Spotify
  - Installer requires version spoof to Windows 10. After installation, enable VxKex Extended for Spotify.exe in %AppData%\Spotify. No version spoof is required.
- StaxRip
  - The app itself opens without VxKex Extended but the bundled applications which it uses (Python and MKVToolNix) require VxKex Extended. Therefore it is recommended to enable VxKex Extended for this program. Ensure that the “Disable VxKex NEXT for child processes” option is not checked.
- Steinberg SpectraLayers
  - Installer works without VxKex Extended. Activation Manager Unlocker requires version spoof to Windows 10.
- TeamTalk
- Universe Sandbox
- VSCode (including VSCodium)
- Webcord
- WinDbg (classic from Windows 11 SDK, and preview)
  - It is recommended to select the “Disable VxKex NEXT for child processes” option, otherwise the applications you are debugging may inadvertently have VxKex Extended enabled as well. The “Time Travel Debugging” feature in preview version does not work due to a missing Windows Runtime interface.
- Yuzu
  - Gameplay was not tested.
- Zig
- Zoner Photo Studio
  - Installer does not work. Use the portable version. GPU accelerated calculations are not available – CPU will be used instead. Due to large number of child processes created, it is recommended that you select “Disable VxKex NEXT for child processes” in the settings.

See the **Application Compatibility List.docx** file, which is installed together with VxKex Extended, for more information.

The majority of Qt6 applications will work, and many Electron applications will work as well.

**Q: Does VxKex Extended modify system files? Will it make my system unstable?**

**A**: VxKex Extended does not modify any system files. Its effect on the whole system is extremely minimal. No background services are used, no global hooks are installed, and the shell extensions and DLLs that are loaded have minimal impact and can be disabled if needed. You can rest assured that your Windows 7 will remain as stable as it always is.

**Q: Do I need to have specific updates installed?**

**A**: Users of Windows 7 without any updates can still use it, but many programs require Service Pack 1, KB2533623 (DllDirectories update) and KB2670838 (Platform Update) in order to run. It is a good idea to install those updates.

**Q: If I have ESUs (Extended Security Updates) installed, can I use VxKex Extended?**

**A**: Yes. There is no problem with ESUs.

**Q: Do console applications work with VxKex Extended?**

**A:** Yes. After you have enabled VxKex Extended for a program you can use it through the
command prompt as normal.

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
