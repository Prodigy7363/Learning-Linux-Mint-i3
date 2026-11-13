# Testing desktop changes

This is the checklist I use to keep desktop experiments organized. I prefer one change at a time because it makes troubleshooting easier.

## Before a change

- Write down which setting or app I want to change.
- Make a backup of the current configuration.
- Note what is working before changing anything.
- Avoid changing boot, firmware, or power settings without a recovery plan.

For an i3 configuration edit, a backup might look like:

```bash
cp -a ~/.config/i3/config ~/.config/i3/config.before-edit
```

## After a change

1. Check whether the configuration is valid.
2. Reload or restart only the affected program.
3. Test the shortcut or feature I changed.
4. Check whether something else stopped working.
5. Keep the change if it works; otherwise restore the backup.

For example, to check and reload i3:

```bash
i3 -C -c ~/.config/i3/config
i3-msg reload
```

Do not run the reload if the syntax check fails.

## Change log template

| Date | Component | What changed | Test | Result | Rollback needed? |
| --- | --- | --- | --- | --- | --- |
| YYYY-MM-DD | Example: i3 | Short description | How it was checked | Pass / fail / not tested | Yes / no |

Only record results after actually testing them. Remove private paths, user names, network addresses, and device identifiers before publishing notes.

## Before publishing

Read [SECURITY.md](../SECURITY.md), inspect the staged files with `git diff --cached`, and confirm that no backup, secret, or private configuration was accidentally included.
