# Dotfiles
My dotfiles on Arch Linux, with the awesome window manager.

![](./rice.png)

Other key pieces of software which these files configure:
- Alacritty
- Neovim
- Qutebrowser

## Dependencies
The following packages _must be installed_ (`rc.lua` will not load without them):
- `vicious` for the battery widget

The following packages are _recommended_:
- `picom` for rounded corners on windows
- `xorg-setxkbmap` for loading languages and switching them with a keybind
- `alsa-utils` for volume keybinds
- `brightnessctl` for screen brightness keybinds

Of course you may use alternatives if you wish, just make sure to modify `rc.lua` accordingly.

## Setup

Some _root_ files were intentionally moved under the home directory, to be tracked as dotfiles.
A symbolic link must be created at their original path so the system can find them.

```bash
sudo ln -s /home/$USER/.config/ly/config.ini /etc/ly/
```

## Cron jobs

Add the following to root's crontab:

```bash
* 22-23 * * * /usr/bin/shutdown now
```

And to user's crontab:

```bash
0 21 * * * /usr/bin/env DISPLAY=:0 DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u)/bus /usr/bin/notify-send --urgency=critical "Shutting down in 60m" "Embrace it, finish up."
30 21 * * * /usr/bin/env DISPLAY=:0 DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u)/bus /usr/bin/notify-send --urgency=critical "Shutting down in 30m" "Embrace it, offload to taskwarrior."
55 21 * * * /usr/bin/env DISPLAY=:0 DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u)/bus /usr/bin/notify-send --urgency=critical "Shutting down in 5m" "You should not be here."
```
