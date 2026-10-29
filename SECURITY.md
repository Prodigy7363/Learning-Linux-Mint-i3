# Privacy and Safe Publishing

This repository is public, so I review files before sharing them. The goal is to document the Linux setup without exposing information that belongs only on my device.

## Before publishing

Check configuration files, scripts, screenshots, and terminal output for:

- Passwords, API keys, access tokens, cookies, and private keys.
- Wi-Fi names or passwords and network details that do not need to be public.
- Private IP addresses, MAC addresses, serial numbers, and account identifiers.
- Personal file paths or usernames that reveal more than the project needs.
- Browser profiles, SSH folders, keyrings, or other private application data.

Use placeholders in examples when a real value is not needed. Don't upload a whole home directory just to share a few configuration files.

## Reviewing changes

Before committing a file:

1. Read it from top to bottom.
2. Check for secrets and machine-specific information.
3. Confirm it is a file you intended to share.
4. Remove local backup copies and temporary files that are not part of the project.
5. Review the final Git diff or file contents.

A quick text search can help find possible issues, but it cannot prove a file is safe. Search results may include harmless examples, and secrets can appear in unexpected formats.

## If a secret is published accidentally

Remove the exposed value from the project and rotate or revoke the credential. Deleting a line in a later commit does not remove it from the repository's history, so additional history cleanup may be necessary.

## Scope

These notes are about protecting private information while sharing this project. They do not replace the security guidance for any specific tool, service, or operating system.
