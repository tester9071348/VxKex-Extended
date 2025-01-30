介绍
============

Ext7 是一套适用于 Windows 7 的 API 扩展，可让一些 Windows 8、8.1 和 10 独占应用程序在 Windows 7 上运行。

如需下载和安装，请参阅[版本页面](https://github.com/YuZhouRen86/VxKex-NEXT/releases)。

**安装前，建议卸载以下软件。**

- **0patch Agent**  
  它可能导致基于 Chromium 的浏览器和 JetBrains IDE 在启用 Ext7 并运行后崩溃。

- **MacType**  
  它可能导致所有程序在启用 Ext7 后无法启动。

安装后，使用很简单。以下是启用 Ext7 的方法：
1. 右键单击程序（.exe 或 .msi），打开属性对话框，选择“VxKex”选项卡。然后，选中“为此程序启用 Ext7”复选框，并尝试运行程序。对于快捷方式，需要在属性对话框中选择“快捷方式”选项卡，点击“打开文件位置”按钮，然后执行以上操作。
2. 从开始菜单中找到“Ext7 Global Settings”并打开，点击“添加”按钮，选择程序（.exe 或 .msi），点击“打开”按钮，并尝试运行程序。

![Ext7 configuration GUI](/example-screenshot.png)

有些程序需要额外配置。Ext7 安装文件夹（默认为 C:\Program Files\VxKex 文件夹）内有一个名为“**Application Compatibility List.docx**”的文件，其中详细说明了这些步骤，但大多数情况下，所有配置都是不言自明的。

如果您是开发人员，源代码将以 7z 文件的形式在版本页面上提供。

常见问题
===

**问：哪些应用程序受支持？**

**答**：兼容的应用程序包括但不限于：

- Bespoke Synth
- Blender
- Blockbench
- Calibre
- Chromium (including Ungoogled Chromium)
- Citra
- Commander Wars
- Cygwin
- Dasel
- Discord Canary
- ElectronMail
- Firefox
- GIMP (3.0.0-RC2)
- GitHub Desktop
- HandBrake
- Kodi
- Life is Strange: True Colors 4.25
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
- Rufus
- Steel Bank Common Lisp
- SpaceEngine
- Spotify
- Steinberg SpectraLayers
- TeamTalk
- Universe Sandbox
- VSCode and VSCodium
- WinDbg (classic from Windows 11 SDK, and preview)
- Yuzu (gameplay was not tested)
- Zig

如需获取更多信息，请参阅与 Ext7 一起安装的**Application Compatibility List.docx**文件。

大多数 Qt6 应用程序都能正常运行，许多 Electron 应用程序也能正常运行。

**问：Ext7 会修改系统文件吗？它会使我的系统不稳定吗？**

**答**：Ext7 不会修改任何系统文件。它对整个系统的影响极小。不使用后台服务，不安装全局钩子，加载的 shell 扩展和 DLL 影响也很小，可以随时禁用。您可以放心，您的 Windows 7 将一如既往地保持稳定。

**问：我需要安装特定的更新吗？**

**答**：没有任何更新的 Windows 7 用户仍可使用它，但许多程序需要安装 Services Pack 1、KB2533623（DllDirectories 更新）和 KB2670838（平台更新）才能运行。最好安装这些更新。

**问：如果我安装了 ESU（扩展安全更新），我可以使用 Ext7 吗？**

**答**：是的，ESU 没有问题。

**问：可以在 Windows 8 或 8.1 中使用吗？**  

**答**：目前，Ext7 只适用于 Windows 7。如果您使用的是 Windows 8 或 8.1，Ext7 将毫无用处。

**问：升级到 Windows 8/8.1/10/11 后可以删除 VxKex 或 VxKex NEXT 或 Ext7 吗？**

**答**：可以。如果 VxKex 已安装，请将其更新为 Ext7，然后从控制面板卸载它。

**问：Ext7 如何运作？**

**答**：Ext7 的工作原理是在启用 Ext7 的每个程序中加载一个 DLL。这是通过使用 IFEO（图像文件执行选项）注册表键来实现的。

具体来说，“VerifierDlls”值被设置为指向 Ext7 DLL。该 DLL 会加载到进程中。

API 扩展是通过编辑程序的动态链接库导入表来实现的，这样程序就不会从 Windows 8/8.1/10/11 动态链接库中导入，而是导入 Ext7 动态链接库。这些 Ext7 动态链接库包含较新版本 Windows 中引入的 Windows API 函数的实现。
