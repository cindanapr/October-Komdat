![Teeworldss](https://raw.githubusercontent.com/cindanapr/Teeworld-Komdat/master/teeworlds.jpg)


Teeworlds ![GitHub Actions](https://github.com/teeworlds/teeworlds/workflows/Build/badge.svg)
=========

A retro multiplayer shooter 
---------------------------

Teeworlds adalah game multiplayer online gratis, tersedia untuk semua sistem operasi utama. Bertarung dengan hingga 16 pemain dalam berbagai mode permainan, termasuk Team Deathmatch dan Capture The Flag. Anda bahkan dapat mendesain peta Anda sendiri!

Perangkat lunak ini disediakan 'sebagaimana adanya', tanpa jaminan tersurat maupun tersirat. Dalam hal apa pun penulis tidak akan bertanggung jawab atas segala kerusakan yang timbul dari penggunaan perangkat lunak ini. Lihat lisensi.txt untuk teks lisensi lengkap termasuk informasi hak cipta.

Silakan kunjungi https://www.teeworlds.com/ untuk informasi terkini tentang permainan, termasuk versi baru, peta khusus dan banyak lagi.

Originally written by Magnus Auvinen


Building on Linux or macOS
==========================

Installing dependencies
-----------------------

    # Debian/Ubuntu
    sudo apt install build-essential cmake git libfreetype6-dev libsdl2-dev libpnglite-dev libwavpack-dev python3

    # Fedora
    sudo dnf install @development-tools cmake gcc-c++ git freetype-devel pnglite-devel python3 SDL2-devel wavpack-devel

    # Arch Linux (doesn't have pnglite in its repositories)
    sudo pacman -S --needed base-devel cmake freetype2 git python sdl2 wavpack

    # macOS
    brew install cmake freetype sdl2


Downloading repository
----------------------

    git clone https://github.com/teeworlds/teeworlds --recurse-submodules
    cd teeworlds

    # If you already cloned the repository before, use:
    # git submodule update --init


Building
--------

    mkdir -p build
    cd build
    cmake ..
    make

On subsequent builds, you only have to repeat the `make` step.

You can then run the client with `./teeworlds` and the server with
`./teeworlds_srv`.


Build options
-------------

The following options can be passed to the `cmake ..` command line (between the
`cmake` and `..`) in the "Building" step above.

`-GNinja`: Use the Ninja build system instead of Make. This automatically
parallizes the build and is generally **faster**. (Needs `sudo apt install
ninja-build` on Debian, `sudo dnf install ninja-build` on Fedora, and `sudo
pacman -S --needed ninja` on Arch Linux.)

`-DDEV=ON`: Enable debug mode and disable some release mechanics. This leads to
**faster** builds.

`-DCLIENT=OFF`: Disable generation of the client target. Can be useful on
headless servers which don't have graphics libraries like SDL2 installed.


Building on Windows with Visual Studio
======================================

Download and install some version of [Microsoft Visual
Studio](https://www.visualstudio.com/) (as of writing, MSVS Community 2017)
with the following components:

* Desktop development with C++ (on the main page)
* Python development (on the main page)
* Git for Windows (in Individual Components → Code tools)

Run Visual Studio. Open the Team Explorer (View → Team Explorer, Ctrl+^,
Ctrl+M). Click Clone (in the Team Explorer, Connect → Local Git Repositories).
Enter `https://github.com/teeworlds/teeworlds` into the first input box. Wait
for the download to complete (terminals might pop up).

Wait until the CMake configuration is done (watch the Output windows at the
bottom).

Select `teeworlds.exe` in the Select Startup Item… combobox next to the green
arrow. Wait for the compilation to finish.

For subsequent builds you only have to click the button with the green arrow
again.


Building on Windows with MinGW
==============================

Download and install MinGW with at least the following components:

- mingw-developer-toolkit-bin
- mingw32-base-bin
- mingw32-gcc-g++-bin
- msys-base-bin

Also install [Git](https://git-scm.com/downloads) (for downloading the source
code), [Python](https://www.python.org/downloads/) and
[CMake](https://cmake.org/download/).

Open CMake ("CMake (cmake-gui)" in the start menu). Click "Browse Source"
(first line) and select the directory with the Teeworlds source code. Next,
click "Browse Build" and create a subdirectory for the build (e.g. called
"build"). Then click "Configure". Select "MinGW Makefiles" as the generator and
click "Finish". Wait a bit (until the progress bar is full). Then click
"Generate".

You can now build Teeworlds by executing `mingw32-make` in the build directory.


Building with bam, guides for all operating systems
===================================================

You can also compile Teeworlds with bam, a custom build system. Instructions
for that can be found at https://www.teeworlds.com/?page=docs&wiki=hacking.
