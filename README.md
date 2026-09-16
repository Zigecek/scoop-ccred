# scoop-ccred

A [Scoop](https://scoop.sh) bucket for [ccred](https://github.com/Zigecek/ccred):
save, list and switch between named sets of local Claude Code credentials.

```powershell
scoop bucket add ccred https://github.com/Zigecek/scoop-ccred
scoop install ccred
```

No admin rights, no execution policy, and no SmartScreen prompt: Scoop
extracts an archive and shims the binary, and a shim is launched through
`CreateProcess` rather than `ShellExecuteEx`.

After installing, set up the background refresh:

```powershell
ccred schedule install
ccred schedule status
```

Uninstalling removes that scheduled task first. A task whose binary is gone is
a permanent, silently failing zombie, so `pre_uninstall` clears it.

A workflow in this repository moves the manifest to each new ccred release
within a few hours, after checking the archive against the `.sha256` published
beside it. `scoop update ccred` picks it up from there.

To remove ccred entirely, stored profiles included:

```powershell
ccred uninstall --purge   # asks before deleting stored credentials
scoop uninstall ccred
```

**Unofficial and independent.** Not affiliated with, endorsed by, or sponsored
by Anthropic PBC.
