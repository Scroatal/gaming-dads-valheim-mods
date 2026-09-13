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
