# osu-wine-install-script

An osu-wine installer, forked from mrniceguy127's installer. This one basically just goes through the steps listed [here](https://osu.ppy.sh/community/forums/topics/367783) with the exception of the optional Japanese fonts fix.

# Instructions

1. Install wine and winetricks. This has been tested with the latest version of wine-staging 5.22 at the time of writing.
2. `git clone https://github.com/marshallracer/osu-wine-install-script`
3. `cd osu-wine-install-script`
4. `./install-osu` Keep in mind that because of the necessary dependencies installed through winetricks it WILL take a while to install everything. osu! will also launch at some point, so make sure to close it when it does.
5. Launch osu. You can either type `osu` in the command line, or if you like GUI's, you can just search "osu" in whatever application launcher you might have. Use the command `osukill` to force kill osu.

You can also specifiy your own WINEPREFIX, WINESERVER, WINE and WINETRICKS in your environment. Defaults are used otherwise of course. e.g. `WINEPREFIX="..." WINE="..." WINESERVER="..." ./install-osu`

# Discord Rich Presence

Check [here](https://osu.ppy.sh/community/forums/topics/1005264?start=7313104).

Thanks to jvyden for their code which includes discordrpc during the install. It should launch automatically when starting osu! via terminal or through your application launcher.

# File listing

- Default WINEPREFIX: `~/Games/osu-wine`
- osu! folder shortcut: `~/Games/osu`
- osu! launch script: `/usr/bin/osu`
- osu! kill script: `/usr/bin/osukill`
- osu! desktop file: `~/.local/share/applications/osu!.desktop`
- osu! logo file: `~/.local/share/icons/osulogo.png`


# Installation Troubleshooting

(this should hopefully not happen anymore but stays in case your install may hang anyway)

> Running /usr/bin/wineserver -w. This will hang until all wine processes in prefix=/home/user/osu-wine terminate

Winetricks sometimes gets stuck while setting the windows version after installing .NET. Whenever it gets stuck just type the following command in a seperate terminal: `WINEPREFIX="$HOME/Games/osu-wine" wineserver -k`.
