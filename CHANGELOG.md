# Changelog

## 0.1.4

- The mod is now just two DLLs (`StorageGroups.dll`, `StorageGroups.Core.dll`). It no longer bundles any .NET libraries, including copies of ones Valheim already ships.
- Fixed a flood of "LiberationSans SDF Font Asset was not found" warnings in the log when opening a chest.
- No gameplay changes. Saved groups and multiplayer messages use exactly the same format as before, so existing worlds keep their groups and players on 0.1.2 or 0.1.3 can still play together with 0.1.4 players.
- If you installed an earlier version by hand, delete the old `StorageGroups` folder first so the extra DLLs are gone. Mod managers do this for you.
