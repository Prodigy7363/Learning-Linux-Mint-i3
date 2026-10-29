# Commands and Customization

These are the main tools and settings I worked with while customizing Linux Mint and i3 on my Chromebook. Commands are examples to help me check the setup, not a one-click installer.

## Checking the setup

These commands show versions or basic desktop information without printing network addresses or other private details.

```bash
echo "$XDG_CURRENT_DESKTOP"
i3 --version
kitty --version
bash --version | head -n 1
```

To see the main configuration folders:

```bash
ls ~/.config/i3
ls ~/.config/polybar
ls ~/.config/picom
ls ~/.config/kitty
ls ~/.config/rofi
```

Some folders or files may not exist on another installation. That's normal if the related program has not been configured.

## Main configuration files

| Component | What I used it for |
| --- | --- |
| i3 | Window layout, gaps, keybindings, startup programs, and window borders |
| Polybar | A floating status bar with system information and icons |
| Rofi | Application launcher and power menu styling |
| Picom | Window shadows, fading, and rounded corners |
| Kitty | Terminal appearance, transparency, and terminal behavior |
| Flameshot | Screenshots, including a delayed screenshot copied to the clipboard |
| feh | Setting desktop wallpaper |

Most user settings live under `~/.config/`. The exact files and options depend on the installed version and my current configuration.

## Backing up before editing

Before changing a config, make a copy. For example:

```bash
cp -a ~/.config/i3/config ~/.config/i3/config.before-edit
```

Use the same idea for another file, changing the source path to the file you are editing. Keep backup files out of the public repository unless they have been reviewed and are needed.

## Checking and reloading i3

After editing the i3 configuration, check its syntax first:

```bash
i3 -C -c ~/.config/i3/config
```

If the check passes, reload the configuration:

```bash
i3-msg reload
```

If the desktop behaves unexpectedly, restore the backup rather than continuing to stack untested changes.

## Shortcuts and appearance

Some of the shortcuts and visual choices in my setup include:

- `Super + D` opens the Rofi application launcher.
- `Print` opens the regular screenshot tool.
- `Super + Shift + S` runs my delayed screenshot helper, which copies a screenshot to the clipboard.
- A 48-pixel top gap leaves room for the floating Polybar.
- The focused window border uses hot pink (`#ff69b4`).
- Kitty uses a dark appearance with slight transparency and has its audio bell disabled.
- Picom provides shadows and rounded corners; I left blur disabled to keep the setup lighter on limited memory.

The exact shortcut behavior depends on the local configuration. Check the config before assuming a binding is present.

## Polybar and Rofi

I customized Polybar to float near the top of the screen with rounded corners, a little space around it, and system information. Rofi has a matching pink theme, a launcher image strip, and a separate power menu.

Some icon characters depend on the fonts installed on the system. If an icon appears as a square or is missing, check which fonts are available before changing the character code.

## Scripts and system settings

I also experimented with a power menu and a delayed screenshot helper. The power button behavior uses a systemd-logind drop-in on my device. These settings are specific to my installation and should not be copied blindly to another computer.

Before using a script or system setting on another machine:

1. Read the whole file.
2. Check any commands it runs.
3. Back up the original setting.
4. Test one change at a time.
5. Keep a way to undo the change.

I still need to compare any files published here against the current copies on the Chromebook before treating them as exact, reusable configuration files.
