# Changelog

## 0.2.2: New characters can join again

**Update the server and every player.** The server part fixes joining for everyone, even players who haven't updated yet.

### Fixes

- A brand-new character (or anyone without a bed) could get stuck on the loading screen forever when joining a world with Storage Groups. The mod keeps its group data on a hidden object at the centre of the world, right next to the start temple, and the game waited for that object to appear before letting the player spawn. The server now moves the group data far outside the world, and the game no longer waits for it. Your groups and chests are not affected.
- "*Name* isn't on Storage Groups 0.2" no longer appears when that player is on 0.2: your game only believes a list of outdated players from a server that counts proof alone (0.2.2 or newer). A 0.2.0 server could flag a player who was just slow to load.

## 0.2.1: No more false "please update" message

### Fixes

- Players already on 0.2 could get "This server uses Storage Groups 0.2 ... please update" when they joined. The server gave each player 20 seconds to report their version, but a game only reported once the player had spawned, and loading the world can take longer than that. Now your game reports its version as soon as it connects.
- Version warnings now only appear when a different version is certain: a player's game reported another version, or it edited a group the way only 0.1.x does. Being slow to load never counts.
- The "server runs an older Storage Groups" warning is gone, because an older server can't be recognised for certain.

Works together with 0.2.0 players and servers. Update the server too, so it uses the stricter rule.

## 0.2.0: Locked chests, Priority and a new look

**Update the server and every player to 0.2.** Mixed versions still work, but Locked chests are only fully protected when everyone is on 0.2 (see Multiplayer below).

Thanks to **@datacain** for reporting the issues and ideas behind this release: Locked chests (#1), the popup size on large screens (#2) and Priority (#3).

### New

- **Locked** group, built in and always at the top of the group menu. Nothing moves into or out of a Locked chest automatically; you can still put items in and take them out by hand. Good for personal gear, boss loadouts, or materials saved for a build. It can't be renamed, deleted or given items.
- **Priority** toggle on grouped chests. Priority chests fill first, and the group's other chests nearby move their items into a Priority chest whenever it has room, so your stock gathers in one place.

### Look and feel

- The Storage Groups and Edit Items popups now use the chest window's own wood background, and its colour changes with the time of day just like the chest window's. They used to be solid dark panels.
- The popups now scale with the rest of the game's UI. They were about half size on large screens, such as 2160p.
- Locked shows a padlock and a blue tint, in the group menu and on a Locked chest's Group button. A Locked chest's sidebar shows only the Group button; its hover explains that nothing moves.
- Priority is a new row below Pause sorting, shown on grouped chests.
- The chest sidebar always stays on screen, even when it has to move aside for the weight badge on a narrow screen.

### Fixes

- Placing a new chest didn't make nearby chests send it anything until something else changed. Now, for example, a Strict chest's leftover items move into a new ungrouped chest right away.

### Multiplayer and updating

- Version check, warnings only (nobody is kicked): players on an older version get an on-screen message asking them to update, and 0.2 players are told when someone outdated is online.
- Players on 0.1.x don't know Locked: while their game is handling a Locked chest, it can still move items out of it, or (rarely) drop overflow into it. Their edits to the Locked group are refused, with a message telling them why.
- If your world already has a group called "Locked", it's renamed to "Locked (old)". Its chests and items stay as they were.
- Saved groups use the same format as before, so 0.1.x players and servers can still read them. Priority is saved separately, and 0.1.x ignores and keeps it.
- If you ever installed the mod by hand, delete any loose `StorageGroups.dll` / `StorageGroups.Core.dll` directly in `BepInEx/plugins` and keep only the mod's own folder. 0.2 now detects an old leftover copy, turns itself off and names the file to delete in the log, instead of filling the log with errors.

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
