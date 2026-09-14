# Gaming Dads Valheim mods

The Windows player updater installs the exact shared mod versions used by the Gaming Dads server.

1. [Download the player updater](https://github.com/Scroatal/gaming-dads-valheim-mods/releases/latest).
2. Extract the ZIP, close Valheim, and run **Gaming Dads Valheim Updater.exe**.
3. Check your Steam Valheim folder, then select **Update mods**.
4. Wait for the completion message and launch Valheim normally through Steam.

The app checks this repository for the current server version file on each update. It downloads
those exact packages from Thunderstore, verifies their file hashes and creates a backup before
installation. Existing personal mods and unshared settings are preserved. Duplicate copies of
shared DLLs are backed up before being removed from the active plugins.

This release supports Windows and ordinary Steam installations. It does not manage r2modman
or Thunderstore profiles. Characters and worlds are not modified. The app is locally built and
not code-signed. In-game compatibility still depends on the upstream mods.

## Camp Kitchen test and updater 1.2.0

**Current kitchen version: 0.3.2.** Close Valheim completely, open **Gaming Dads
Valheim Updater 1.2.0** and select **Update mods** before joining. If you already
have updater 1.2.0, you do not need a new EXE: it reads the current download feed.
[Download updater 1.2.0](https://github.com/Scroatal/gaming-dads-valheim-mods/releases/tag/v1.2.0).

The server has loaded kitchen 0.3.2, its model and the ChestFlow 0.5.7 adapter.
The public download was tested with the existing updater in an isolated game
folder. Actual updated in-game fonts, controls and multiplayer cooking still need
testing. Start with small quantities in test chests. ChestFlow shared access stays
enabled; recipe requirements, reserves and the 10 wood / 10 stone / 5 flint build
cost are unchanged. The new compact interface includes clearer chest selection
and a 10-metre basic-cooking fire range.

The updater supports ordinary Windows Steam installs, not mod-manager profiles.
**Manual/profile users:** retain the matching shared dependencies and replace your
old kitchen DLL once with the [Camp Kitchen 0.3.2 test ZIP](https://github.com/Scroatal/gaming-dads-valheim-mods/releases/download/kitchen-0.3.2/AutoKitchen-0.3.2-model-test.zip).
The older complete 1.1.1 pack and kitchen 0.3.0 archive are not current.

`Gaming-Dads-Valheim-Server-Addons.json` pins the current kitchen archive, hashes,
supported game assembly and dependency versions. A missing feed, changed hash or
unsupported game/dependency version stops the update without a stale fallback.

## Manual installation fallback

[Download the complete manual mod ZIP](https://github.com/Scroatal/gaming-dads-valheim-mods/releases/download/v1.1.1/Gaming-Dads-Valheim-Manual-Mod-Pack-2026-09-14.zip) (about 218 MB). This is a snapshot from 14 September 2026, including the 12 shared packages, Deepwater Fishing 1.0.8 and Gravestone Assist 1.0.0.

Use this if the updater cannot connect. It contains the actual mod files, so no updater or additional mod downloads are needed. Fully close Valheim, extract the ZIP, and follow READ ME FIRST.txt. Back up existing mods first. Starter settings are kept separate to help preserve personal settings and fishing journals. Check with Scott before using this snapshot after later server updates.

Use the download above or the files under Releases; GitHub's green Code > Download ZIP button does not contain the playable mod pack.

## Certificate errors and updater 1.1.1

If an older updater reports `CERTIFICATE_VERIFY_FAILED`, download and extract the latest ZIP
into a new folder. Check the window title says **1.2.0** before selecting **Update mods**.
This version uses Windows certificate-chain validation and retains expiry and hostname checks.
If it still fails, send Scott the new error, which identifies the failing site and local time.
A genuinely expired certificate or a problem with HTTPS inspection software still needs attention.

## Client add-ons

**Updater 1.1.0 adds Deepwater Fishing 1.0.8 and Gravestone Assist 1.0.0.**
Players using the original updater should download and extract the new ZIP once, then run
**Update mods** with Valheim closed. Each player installs these mods locally.

Deepwater Fishing includes the splash cue, journal input fix and perfect-catch material rewards.
Gravestone Assist helps select your own nearby grave within 5 metres. Existing fishing journals
and personal mod settings are preserved. Restart the game after updating.

`Gaming-Dads-Valheim-Client-Addons.json` holds the reviewed client DLLs and their SHA-256 hashes.
Updater 1.1.0 reads this file on each update. It is separate from the server manifest so automatic
server publishing preserves the client add-ons. A failed download or hash check stops installation.
These builds passed automated and isolated installation checks; in-game testing remains separate.

## What is stored here

`Gaming-Dads-Valheim-Player-Manifest.json` contains package versions, file hashes and selected
shared gameplay settings. It contains no server passwords, account tokens, IP addresses or saves.
The manifest is generated from the server's verified installed files. The updater never chooses
an independently newer version of a shared mod.

The server manager publishes this file after successful managed update checks when publishing
is enabled. A publishing failure is logged and the previous GitHub file is kept. Direct server
launches that bypass the manager also bypass these checks and publishing.

## Backups and recovery

Backups are kept in `%LOCALAPPDATA%\Gaming Dads\Valheim Mod Updater\backups`.
If an update is interrupted, reopen the updater and select **Recover interrupted update**.
If GitHub or a required download is unavailable, installation stops without using an old local feed.

Mod authors retain ownership of their packages. Package attribution accompanies downloaded mods.
