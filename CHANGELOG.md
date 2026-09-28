# Changelog

## 0.1.7: UI/UX overhaul

- The chest sidebar now changes with the chest. A chest without a group shows **New Group From Contents**; a chest with a group shows **Add Contents** and **Edit Items...**. Both have **Pause sorting**.
- **New Group From Contents**: one click (plus Enter) makes a group from the chest's items, named after the item there is most of, and puts the chest in it.
- **Edit Items...**: a list of the group's items with icons, a Remove button for each, and Clear all.
- The Group button's hover now also shows the group chests nearby, so the separate Routes (?) button is gone.
- Clearer names: **Evict Mismatching** is now **Strict**, **Hold routing** is now **Pause sorting**, **Extend From Contents** is now **Add Contents**, and **Edit** in the group menu is now **Rename**. **Set From Contents** is gone: use Clear all, then Add Contents.
- Popups have a solid dark background, so nothing shows through them.
- Hover boxes update while you hover, for example right after Add Contents.
- No gameplay or save changes. Groups, settings and multiplayer messages are the same as before, so older players and servers still work together with 0.1.7.

## 0.1.6

- New **Extend From Contents** button in the chest sidebar: adds this chest's items to its group without removing the group's other items. An item still belongs to one group only; if it was in another group, it moves over and the game tells you.
- New icon: three chests, each with its own group.
- The mod page now has screenshots.

## 0.1.5

- Group changes on a server now show up almost immediately (they could take up to about 5 seconds). This covers creating, renaming and deleting groups, Evict Mismatching, and Set From Contents.
- For the full effect, update both the server and all players. Players on 0.1.5 already see their own changes quickly, even on a server that's still on an older version.
- The group menu picks up changes faster and does less work while it's open.
- No gameplay changes. Saved groups and multiplayer messages use the same format as before, so 0.1.2 to 0.1.4 players and servers still work together with 0.1.5.

## 0.1.4

- The mod is now just two DLLs (`StorageGroups.dll`, `StorageGroups.Core.dll`). It no longer bundles any .NET libraries, including copies of ones Valheim already ships.
- Fixed a flood of "LiberationSans SDF Font Asset was not found" warnings in the log when opening a chest.
- No gameplay changes. Saved groups and multiplayer messages use exactly the same format as before, so existing worlds keep their groups and players on 0.1.2 or 0.1.3 can still play together with 0.1.4 players.
- If you installed an earlier version by hand, delete the old `StorageGroups` folder first so the extra DLLs are gone. Mod managers do this for you.

## 0.1.3

- No longer bundles `System.Memory` and `System.Runtime.CompilerServices.Unsafe`. Valheim already ships both, and a second copy could conflict with the game's own.

## 0.1.2

- Pressing the Use key while typing a group name no longer closes the name editor.

## 0.1.1

- Works with the standard BepInExPack for Valheim, with no extra MonoMod libraries needed.
- Nearby chests are rechecked when a group's settings change (including turning Evict Mismatching off) and when a nearby chest's contents change.

## 0.1.0

- First release. Put chests in groups and items move to the right chest by themselves.
