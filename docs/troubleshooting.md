# Troubleshooting Notes

This page collects issues I ran into while building my Linux Mint and i3 desktop. The fixes below describe what worked on my device; another installation may behave differently.

## Audio showed a Dummy Output

At one point, Linux showed a Dummy Output instead of the expected audio device. On my setup, opening `pavucontrol` and changing the device profile to **Pro Audio** brought the expected audio options back.

If this happens again, check the available output devices and profiles first. Don't assume Pro Audio is the right choice for every computer.

## Kitty kept making a bell sound

I disabled the terminal audio bell in Kitty's configuration with:

```text
enable_audio_bell no
```

After changing a setting, start a new terminal or reload the configuration as appropriate and check whether the behavior changed.

## Polybar overlapped the desktop

My Polybar uses a floating, override-redirect setup. I left a gap at the top of i3 so windows would not sit underneath the bar. The top gap in my setup is 48 pixels.

If the bar overlaps windows or leaves too much space, check the i3 gap and Polybar position together. Change one value at a time and test the result.

## i3 configuration changes did not work

I learned to check the configuration before reloading it:

```bash
i3 -C -c ~/.config/i3/config
```

If the syntax check succeeds, reload i3:

```bash
i3-msg reload
```

If it fails, read the error message and check the relevant line before trying again. Keeping a backup makes it easier to undo a bad edit.

## Missing icons

Some icons rely on a particular font being installed. A missing-glyph box does not always mean the Polybar or Rofi configuration is broken. Check the font first, then choose a character supported by that font.

## Delayed screenshots

My delayed screenshot shortcut depends on Flameshot and a small helper script. If it stops working, check that Flameshot is installed, the script is still executable, and the i3 keybinding points to the right script. Test the command manually before changing the keybinding.

## Performance on 4 GB of RAM

The Chromebook has about 4 GB of RAM, so browsers and several system tools can use most of the available memory. Firefox with multiple tabs was one of the heavier applications during testing.

When the desktop becomes slow:

- Close tabs and applications that are not needed.
- Check memory use with a system monitor.
- Avoid adding visual effects before checking their memory and performance cost.
- Keep changes small so it is easier to identify what caused a slowdown.

I disabled Picom blur to keep the desktop lighter. I also kept an older kernel available as a fallback instead of removing it during cleanup.

## General approach

When something breaks, I try to:

1. Identify exactly what changed.
2. Read the relevant config or error message.
3. Make a backup.
4. Test one change at a time.
5. Verify the result before moving on.

These notes reflect my own troubleshooting experience and are not meant to be a universal fix list.
