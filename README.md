# osu-wine-install-script

An osu-wine installer, forked from mrniceguy127's (old) installer. This one basically just goes through the steps listed [here](https://osu.ppy.sh/community/forums/topics/367783) with the exception of the optional Japanese fonts fix.

# Important Notice on custom install locations
Stop changing the path by hand in the script you dinguses, there's info on how to set a custom path:

You can specifiy your own WINEPREFIX, WINESERVER, WINE and WINETRICKS in your environment. Defaults are used otherwise of course. e.g. `WINEPREFIX="..." WINE="..." WINESERVER="..." ./install-osu`
The most relevant for you if you want to install osu in a non-default location would be `WINEPREFIX="/your/path/for/osu" ./install-osu`


# Platforms
This guide is focused and optimized for Arch Linux and other distros based on it (e.g. EndeavourOS, etc.)


# Pre-installation notice
This is 100% relevant to nVidia/Intel GPUs. AMD GPUs should be fine but in case any issues come up refer to this.

PLEASE INSTALL THE APPROPRIATE GRAPHICS DRIVERS/PACKAGES
https://github.com/lutris/docs/blob/master/InstallingDrivers.md

The easiest way to get all relevant dependencies installed is to follow the [Lutris documentation on installing the most important dependencies needed for gaming.](https://github.com/lutris/docs/blob/master/WineDependencies.md) This will especially be useful for people planning to play osu on nVidia and Intel GPUs as they usually run more quickly into issues but AMD users are not 100% exempt from needing troubleshooting.

Some distros do not ship the necessary package for osu to connect to its servers. This can prevent the initial client install to work properly.
<br>Following package should help solve this issue:
<br>Arch - `lib32-gnutls`

To prevent an error code in terminal when trying to launch osu which reads `X Error of failed request: BadWindow` or something similar you will need to install the following packages first:
<br>Arch - `lib32-gst-plugins-base-libs lib32-libxcomposite icoutils`

For nVidia Cards:
Make sure `lib32-nvidia-utils` is installed or else the game won't run at full speed for some reason.


# Instructions

1. Install wine and winetricks. This has been tested with the latest version of wine-staging 9.8 at the time of writing.
2. `git clone https://github.com/marshallracer/osu-wine-install-script`
3. `cd osu-wine-install-script`
4. `./install-osu` - <b>DO NOT INSTALL MONO</b> - Keep in mind that because of the necessary dependencies installed through winetricks it WILL take a while to install everything. osu! will also launch at some point, so make sure to close it when it does.
- Add the path the launcher is installed to to your PATH if it isn't already. Copy `export PATH=$HOME/.local/bin/:$PATH` and add it to your users bash profile [just as explained in this Arch Wiki article](https://wiki.archlinux.org/title/Environment_variables#Per_user).
5. Launch osu. You can either type `osu` in the command line, or if you like GUI's, you can just search "osu" in whatever application launcher you might have. Use the command `osukill` to force kill osu.


# Discord Rich Presence

Check [here](https://osu.ppy.sh/community/forums/topics/1005264?start=7313104).

Thanks to jvyden for their code which includes discordrpc during the install. It should launch automatically when starting osu! via terminal or through your application launcher.

# File listing

- Default WINEPREFIX: `~/Games/osu-wine`
- osu! folder shortcut: `~/Games/osu`
- osu! launch script: `~/.local/bin/osu`
- osu! kill script: `~/.local/bin/osukill`
- osu! desktop file: `~/.local/share/applications/osu!.desktop`
- osu! logo file: `~/.local/share/icons/osulogo.png`


# Installation Troubleshooting

- <b>NOTE FOR NON-ARCH DISTRO USERS:</b>

If you can ensure lib32-gnutls or some equivalent is present on your system and all other prerequisites are fulfilled then this guide should work fine but I can't guarantee anything

- <b>The script is stuck!</b>
(this should hopefully not happen anymore but stays in case your install may hang anyway)

> Running /usr/bin/wineserver -w. This will hang until all wine processes in prefix=/home/user/osu-wine terminate

Winetricks sometimes gets stuck while setting the windows version after installing .NET. Whenever it gets stuck just type the following command in a seperate terminal: `WINEPREFIX="$HOME/Games/osu-wine" wineserver -k`.
