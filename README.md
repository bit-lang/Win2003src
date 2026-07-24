# Windows-Server-2003
This is the leaked source code of Windows Server 2003 / xp

Source: Torrent Hash - 3d8b16242b56a3aafb8da7b5fc83ef993ebcf35b

---

from https://github.com/tongzx/nt5src
Sources:
    4Chan thread: https://boards.4channel.org/g/thread/77894863/the-windows-xp-source-code-was-leaked-online
    MEGA 7zip and cabinet download: https://mega.nz/file/PdhxBSZD#w-O3C-BAMwE4E02qPn_fSdTivILcE8hzk9PeyoXg7wU

---

from https://github.com/cynegeirus/windows-nt5

Pre-Installation Preparations

    Extract the source tree. In this guide, we will assume C:\NT.
    Remove the Read Only setting, including subfolders and files.
    Create a desktop shortcut for:

    %windir%\system32\cmd.exe /k C:\NT\tools\razzle.cmd free offline

    Open the razzle window using the shortcut you created.

Building

    Clean Rebuild: Performs a clean rebuild of all components:

    build /cZP

    Incremental Build: Builds only components that have changed since the last clean build:

    build /ZP

    Mount RTM CD: Execute tools\missing.cmd (optionally, perform this step for every SKU).
    Post-Build: Execute tools\postbuild.cmd. Use the -sku:{sku} option if you want to process only a specific SKU. Expect filechk errors if you skip the optional missing.cmd step.

You can modify your razzle shortcut (or execute the command manually inside C:\NT) to include (or remove) additional arguments:

    free: Build 'free' bits (production, omitting it will generate 'checked' bits).
    CkhKernel: Build 'checked' (testing) kernel/hal/ntdll when building 'free' bits.
    no_opts: Disable binary optimization (useful for debugging, but will likely fail a full build since some code can't be built without optimization).
    verbose: Enable verbose execution of the build process.
    binaries_dir <basepath>: Specifies custom output directory (default is binaries, the suffix added after the dot is non-customizable).

For more options, see razzle.cmd /? for details.
Generating ISO Files

Execute the following command to generate ISO files:

tools\oscdimg.cmd {sku} [destination-file (optional)]

Where {sku} is one of the following:

    srv: Windows Server 2003 Standard Edition
    sbs: Windows Server 2003 Small Business Edition
    ads: Windows Server 2003 Enterprise Edition
    dtc: Windows Server 2003 Datacenter Edition
    bla: Windows Server 2003 Web Edition
    per: Windows XP Home Edition
    pro: Windows XP Professional

The ISO file will be saved to {build-drive}\{build-tag}_{sku}.iso, unless [destination-file] is provided as a parameter.
Generating New Build Name/Number (Optional)

    Version information is stored in \public\sdk\inc\ntverp.h.
    You can also use the following command to generate a new build name quickly:

    nmake set_builddate set_buildnum set_buildname -f makefil0

Timebomb (Optional)

The timebomb feature can be enabled or disabled by commenting or uncommenting the timebomb.cmd entry in \tools\postbuildscripts\pbuild.dat.

    If enabled, time can be adjusted by editing \tools\postbuildscripts\timebomb.cmd.
    Modify the DAYS variable inside timebomb.cmd (line 44):
        Setting DAYS to 0 will disable the timebomb.
        Valid DAYS parameters: 0, 5, 15, 30, 60, 90, 120, 150, 180, 240, 360, 444.

Product Keys

    Standard Edition: M6RJ9-TBJH3-9DDXM-4VX9Q-K8M8M
    Enterprise Edition: QW32K-48T2T-3D2PJ-DXBWY-C6WRJ
    Enterprise x64: KK2WD-BFYJ6-77X87-8TRBF-9B343

Disclaimer

I do not own this source code. The leaks are not from me. I uploaded the extracted source code to a new repository because I thought it would benefit developers.
