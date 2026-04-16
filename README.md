# SteaMidra

SteaMidra helps you set up games to work with Steam using Lua scripts, manifests, and GreenLuma. It writes the right files into your Steam folder so games and DLC can run. It does not replace or crack Steam itself.

# Educational use only. Use at your own risk.

*Made by Midrag and his brother!*

---
Need help? Chat with us on our discord server: https://discord.gg/hwUqSfMEVa


## What SteaMidra can do
- Download and use Lua files for games, download manifests, and set up GreenLuma.  
- Write Lua and manifest data into Steam's config so games work with or without an extra injector.  
- Other features: multiplayer fixes (online-fix.me), **game fixes/bypasses (Ryuu)**, DLC status check, cracking (gbe_fork), SteamStub DRM removal (Steamless), AppList management, and DLC Unlockers (CreamInstaller-style: SmokeAPI, CreamAPI, Koaloader, Uplay).  
- **Multi-language GUI** — English and Portuguese built-in; add more via `sff/locales/`.
- Parallel downloads, backups, recent files, and settings export/import.

---

## Quick start

### Step 1: SteaMidra

Download the latest version from [here](https://github.com/Midrags/SFF/releases/latest).
Create an folder anywhere and name it `SteaMidra` and put the `SteaMidra_GUI.exe` and `SteamKillInject.exe` in this folder.

### Step 2: Greenluma

Download the latest Greenluma patched version [here](https://catbox.moe).
Extract the ZIP and you will see three folders. In this case we only need `NormalModePatch.rar`.
Extract `NormalModePatch.rar` and put all files from this folder in your `SteaMidra\Greenluma` folder.


### Step 3: Setup Greenluma
Go into the Greenluma folder and execute `GreenLumaSettings2025.exe`.
Then type 2 in the terminal and press Enter and set full `steam.exe` (Default: `C:\Program Files (x86)\Steam\steam.exe`) and `GreenLuma_2025_x64.dll` (Default: `SteamMidra\Greenluma\GreenLuma_2025_x64.dll`) path.

---

### AppList profiles (GreenLuma limit workaround)

GreenLuma has a hard limit of 130–134 App IDs. To use more games, use AppList profiles:

1. **Manage AppList IDs** → **AppList Profiles** (CLI) or the profiles option in the GUI
2. **Create profile** – creates an empty profile. Switch to it before adding more games.
3. **Switch to profile** – loads that profile's IDs into the AppList folder (truncated to the limit).
4. **Save current AppList to profile** – saves your current IDs into a profile (new or existing).
5. **Delete / Rename** – manage profile names and remove unused profiles.

When you reach 130 IDs, SteaMidra will remind you to create a new profile. Create an empty profile, switch to it, then add more games.

## What's new

See [CHANGELOG.md](CHANGELOG.md) for what changed in the latest update.

## Documentation

[Documentation index](docs/README.md) – Start here.

[Setup Guide](docs/SETUP_GUIDE.md) – What to install (including GreenLuma).
[User Guide](docs/USER_GUIDE.md) – What each menu option does and how to add games.

[Quick Reference](docs/QUICK_REFERENCE.md) – Commands and shortcuts.

[Feature Guide](docs/FEATURE_USAGE_GUIDE.md) – Parallel downloads, backups, library scanner, and more.

[Multiplayer Fix](docs/MULTIPLAYER_FIX.md) – Using the online-fix.me multiplayer fix.

[Fixes/Bypasses (Ryuu)](docs/RYUU_FIX.md) – Using Ryuu as a free, no-account alternative fix source.

[DLC Unlockers](docs/dlc_unlockers/README.md) – Using DLC unlockers (CreamInstaller-style).


## Troubleshooting

**Steam says "No Internet Connection" when downloading** — SteaMidra handles this automatically.

1. **Workshop ACF fix** — The most common cause is orphaned workshop items in `appworkshop_{id}.acf` triggering a failed Workshop update. SteaMidra patches this file to clear `NeedsDownload` when no workshop content is installed.
2. **Manifest seeding** — When you process a .lua file or use "Update all manifests", manifests are written directly to Steam's `depotcache` folder before Steam starts. Steam finds them locally.
3. **ACF error state** — SteaMidra clears stale `UpdateResult` and validation flags in the game ACF so Steam doesn't get stuck in a retry loop.

**Dependency conflicts / urllib3 error** — Run both install commands from Step 1 above (requirements.txt first, then `pip install steam==1.4.4 --no-deps`). If conflicts persist with other projects on your system, use a virtual environment.

**ModuleNotFoundError** — Dependencies are not installed. Run `pip install -r requirements.txt`.

**Remove SteamStub (Steamless) → WinError 2** — In the GUI, clicking "Remove SteamStub" now opens a file picker. Just navigate to your game folder and select the `.exe` yourself — no Steam API lookup needed.

**SteamAutoCrack not found** — Make sure the SteaMidra folder is intact and hasn't had any files deleted. SteamAutoCrack is bundled in `third_party/SteamAutoCrack/cli/` and should already be there.


## Credits

**Made by Midrag and his brother.**

**GreenLuma** – SteaMidra works alongside GreenLuma for AppList injection. GreenLuma is a separate tool and must be downloaded and set up independently. GreenLuma patch developed by **Lightse**.

**gbe_fork** – The "Crack a game" feature uses **gbe_fork**, a Steam emulator for running games offline. License in `third_party_licenses/gbe_fork.LICENSE`.

**gbe_fork tools** – Build and packaging tools for gbe_fork. License in `third_party_licenses/gbe_fork_tools.LICENSE`.

**Steamless** – The "Remove SteamStub DRM" feature uses **Steamless** by Atom0s for stripping Steam DRM from executables. License in `third_party_licenses/steamless.LICENSE`.

**aria2** – Used internally for fast file downloads. License in `third_party_licenses/aria2.LICENSE`.

**fzf** – Used for fuzzy search in menus (CLI). License in `third_party_licenses/fzf.LICENSE`.

**SteamAutoCrack** – The SteamAutoCrack feature uses the **SteamAutoCrack CLI** by oureveryday. Bundled in `third_party/SteamAutoCrack/cli/`. License in `third_party_licenses/SteamAutoCrack.LICENSE`.

**CreamInstaller** – The DLC Unlockers feature is inspired by and compatible with CreamInstaller. SteaMidra does not ship CreamInstaller; it provides its own implementation that follows similar behavior.

**online-fix.me** – The multiplayer fix feature downloads fixes from online-fix.me. SteaMidra is not affiliated with online-fix.me. An account on that site is required.

**GBE Token Generator** – Goldberg Emulator configuration generation based on work by **Detanup01** ([gbe_fork](https://github.com/Detanup01/gbe_fork)), **NickAntaris**, and **Oureveryday** ([generate_game_info](https://github.com/oureveryday/Goldberg-generate_game_info)).

**Hubcap Manifest** – Store browser and manifest library API provided by **Hubcap Manifest** ([hubcapmanifest.com](https://hubcapmanifest.com)). Formerly known as Morrenus / Solus.

**RedPaper** – Credit to RedPaper for the Broken Moon MIDI cover, originally arranged by U2 Akiyama and used in Touhou 7.5: Immaterial and Missing Power. Touhou 7.5 and its assets are owned by Team Shanghai Alice and Twilight Frontier. SteaMidra is not affiliated with or endorsed by either party. All trademarks belong to their respective owners.

SteaMidra is licensed under the GNU General Public License v3.0 (see LICENSE file).

Use at your own risk. For educational purposes only.
