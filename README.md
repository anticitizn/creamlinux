# Creamlinux
A CreamAPI clone for Linux.

Since 20PercentRendered has archived the repo, I have decided to fork and support it as far as I can.

## Support
Creamlinux *should* work on most Steam games. It does not work with Proton or Wine - use SmokeAPI or other alternatives made specifically for Windows instead.
The following games have been tested and definitely confirmed to work:

 - Stellaris
 - Hearts Of Iron IV
 - Europa Universalis IV
 - Crusader Kings II
 - Crusader Kings III
 - Victoria 3
 - PAYDAY 2

## Unsupported Games
The following games have been tested and do not currently work with creamlinux, feel free to try some of the alternatives listed at the bottom of this readme:
- Cities Skylines 2
- European Truck Simulator / American Truck Simulator

## Installation
The easiest way of installing is using **Tickbase**'s Application: https://github.com/Novattz/creamlinux-installer
It automatically downloads and sets up creamlinux for Steam games that you choose, as well as fetching all DLC IDs for it. Keep in mind that you will still need the actual, **up-to-date** DLC files in the game. The install script and creamlinux do **not** automatically download any game content. You will have to run it again if new DLCs are released for a game.

If the script does not work for you, you can install `creamlinux` manually. Beware that you will have to manually update `cream_api.ini` to contain the DLC IDs for the games that you choose.

## Manual Installation
0. You will need the actual, **up-to-date** DLC files in the game. Creamlinux does **not** auto-download anything
1. Download the [latest](https://github.com/anticitizn/creamlinux/releases/latest/download/creamlinux.zip) release of Creamlinux
2. Unzip it and copy the files to the game's directory
3. Set the game's steam launch params to `sh ./cream.sh %command%`
4. Launch the game and have fun!

The list of "supported" DLCs is stored in `cream_api.ini`. If you want to test creamlinux on a new game or a new DLC has just come out, you can add more entries here manually.

If that doesn't work, please check the Troubleshooting section below.

## Building from source
0. Ensure you have all build dependencies installed:
- On Ubuntu: `build-essential` `gcc-multilib` `g++-multilib` `cmake` `git`
- On Arch: `base-devel` `multilib-devel` `cmake` `git`

1. Clone the project:
```
git clone https://github.com/anticitizn/creamlinux
```
2. Build the project:
```
sh ./build.sh
```

3. Copy `output` folder contents to the game folder
4. Set the game's steam launch params to `sh ./cream.sh %command%`

Alternatively, if you have Docker installed, you can just run `docker compose up`

# Troubleshooting
## Red triangles next to DLCs
This is normal. The DLCs should still work.

![Red triangles next to DLCs are normal](https://cdn.discordapp.com/attachments/663174968791662594/1093109044295766106/image.png)

## DLCs don't work
- Have you made sure to download the latest version of the DLC files? Sometimes unrelated patches or updates to the game will modify some DLC files, and creamlinux is currently somewhat sensitive to outdated files.
- Do you have Steam installed from a flatpak? Creamlinux doesn't play nicely with it, please try a native version if possible

## Game not starting after enabling creamlinux
Are you sure that the creamlinux files are at the game's root directory and not in a subfolder?

Try setting the executable flag of the `cream.sh` script (it should be set already, but just in case):
```
chmod +x cream.sh
```

## It doesn't work with Proton or Wine
Creamlinux is specifically made for native Linux games. If you are using a compatibility layer, use alternatives made specifically for Windows (e.g. SmokeAPI, regular CreamAPI or whatever).
[AutoCreamAPI](https://github.com/MoebiusZero/AutoCreamAPI) has worked well for some people, keep in mind that you need to install .NetCore3 on your Wine/Proton instance first.

## Nothing helped!
Please collect a log using the instructions below as well as an overview of the game's directory using `ls -lh; ls -lh */`, then post an issue describing your situation [here](https://github.com/anticitizn/creamlinux/issues/new).

## Gathering logs
If using a KDE environment, set your game launch options to this:
```
konsole --hold -e sh ./cream.sh %command%
```
Or if you are using Gnome environment, you can set your launch options to this:
```
gnome-terminal -- sh -c "./cream.sh %command%; exec bash"
```
If using neither, install `konsole` and follow the KDE step.
Then launch the game (skip any launchers like the Paradox launcher if possible, they interfere with the logging). Wait for the game to load, close it, then copy and paste the contents of the terminal.

# Advanced 
If you want to load `cream_api.ini` from a specific path, specify the path with `CREAM_CONFIG_PATH` in the launch options.

# Alternatives
If creamlinux doesn't work for your game, there are a couple of known alternatives for Linux. I provide no guarantees for their legitimacy and functionality, but some people seem to be happy with them.
- [StellarKey](https://0xacab.org/stellarkey/stellarkey)
- [CreamAPI (Windows, MacOS, Linux)](https://cs.rin.ru/forum/viewtopic.php?f=29&t=70576)
- [AutoCreamAPI for Proton](https://github.com/MoebiusZero/AutoCreamAPI) (.NetCore3 required)

# Credits
The many contributors who submitted bugfixes, tested games and updated the list of DLC IDs :)

[Novattz](https://github.com/Novattz) for [creamlinux-installer](https://github.com/Novattz/creamlinux-installer)

[Rosentti](https://github.com/Rosentti) for originally creating and maintaining this project

[pulzed](https://github.com/pulzed) for [mINI](https://github.com/pulzed/mINI)(ini.h)

[Valve](https://www.valvesoftware.com/) for [steamworks](https://partner.steamgames.com/)

[gabime](https://github.com/gabime) for [spdlog](https://github.com/gabime/spdlog)

[goddeysfreya](https://github.com/goddessfreya) for [hookey](https://github.com/goddessfreya/hookey)
