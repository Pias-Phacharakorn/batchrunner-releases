# BatchRunner releases

Public release channel for the BatchRunner Revit 2026 add-in (the source is private).

- **Install:** download `BatchRunner-Setup-<version>.exe` from [Releases](../../releases/latest), close Revit, run it.
- **`latest.json`** is read by every installed copy at startup:
  - `latestVersion` / `message`: show an "update available" notice when newer than the installed version
  - `allowedUntil`: the date every version stops working (`yyyy-MM-dd`)
  - `versionExpiry`: per-version override of `allowedUntil`, e.g. `{ "1.0": "2027-03-01" }`
  - `minVersion`: block every version below this one
