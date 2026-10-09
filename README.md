# BatchRunner releases

## Overview

Public release channel for the **BatchRunner** Revit 2026 add-in. The add-in's source is
private; this repo holds only what installed copies and users need: the
installers (as GitHub Releases) and `latest.json`, the update and expiry policy every
installed copy reads at startup.

## Tech stack

- **GitHub Releases** for the `BatchRunner-Setup-<version>.exe` installers
- A plain **JSON** file (`latest.json`) read over HTTPS by the add-in

## Project tree

```text
batchrunner-releases/
├── latest.json                      # Update and expiry policy read by the add-in
├── README.md
└── .claude/settings.json
```

## Installing

Download `BatchRunner-Setup-<version>.exe` from [Releases](../../releases/latest), close
Revit, and run it.

## `latest.json`

| Field | Meaning |
|---|---|
| `latestVersion` / `message` | Shows an "update available" notice when newer than the installed version |
| `downloadNote` | Where to download the installer |
| `allowedUntil` | Date every version stops working (`yyyy-MM-dd`) |
| `versionExpiry` | Per-version override of `allowedUntil`, e.g. `{ "1.0": "2027-03-01" }` |
| `minVersion` | Blocks every version below this one (`null` = no minimum) |

## Publishing a release

1. Build the installer from the private add-in repo.
2. Create a GitHub Release here and attach `BatchRunner-Setup-<version>.exe`.
3. Update `latest.json` (`latestVersion`, `message`, and `allowedUntil` / `versionExpiry` /
   `minVersion` as needed) and push to `main`. Installed copies pick it up on their next
   start.

Every installed copy reads `latest.json` at startup, so a wrong date or `minVersion` locks out
users immediately. Check the values before pushing.
