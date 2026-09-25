# Storage Groups

> **Work in progress. Use at your own risk.** This mod is not fully tested yet, especially in multiplayer and with wards. Back up your world before using it.

A Valheim mod. Put your chests in groups, and items move to the right chest by themselves.

## How it works

Open any chest. The controls are next to the chest window.

- **Group**: hover to see the items in this chest's group; click to open the group settings. Pick a group for this chest (for example "Ore"), or make a new one. Click the same group again to take the chest out of it.
- **Set From Contents**: this chest's contents become the group's items. An item can only be in one group, so if an item belonged to another group, it moves to this one and the game tells you.
- **Routes (?)**: hover for a short list of nearby groups (closest first, marked if full or behind a ward edge) and which of them have Evict Mismatching on.
- **Hold routing**: while ticked, nothing moves in or out of this chest. Handy when setting up a new group: fill the chest, then use Set From Contents without nearby chests pulling your items away. Turns off when you close the chest.
- **Evict Mismatching** (per group, optional): what happens to items that don't belong in this group's chests when their own group has no room nearby. With it on, they go to a nearby chest that doesn't evict. With it off, they stay.

When an item lands in any chest, and a chest of that item's group is within 10 meters with room, the item moves there. Closest chest first.

- If its group's chests are all full or too far away, the item stays put, unless the chest it landed in evicts (see above). Nothing is lost.
- Items with no group stay where you put them, unless the chest evicts.
- Changing a chest's group re-checks everything in it.
- Hover over a chest to see its group, and whether it is inside a ward.
- **Show routing messages** (checkbox at the top of the group menu, just for you): shows a short message every time an item is routed near you, like "Evicted 3 Stone to an ungrouped chest (7 m)". Handy to see what the mod is doing. Off by default.

## Where does an item go?

```
                  An item lands in a chest
                            |
                            v
        +-------------------------------------+
        | Is this chest in the item's group?  |--- yes ---> STAYS (it is home)
        +-------------------------------------+
                            | no
                            v
        +-------------------------------------+
        | Is a chest of the item's group      |--- yes ---> MOVES there
        | within 10 m, with room, and in the  |             (closest first)
        | same ward (or both outside wards)?  |
        +-------------------------------------+
                            | no
                            v
        +-------------------------------------+
        | Does this chest's group have        |--- no ----> STAYS
        | Evict Mismatching turned on?        |             (waits for room)
        +-------------------------------------+
                            | yes
                            v
        +-------------------------------------+
        | Is an ungrouped chest nearby        |--- yes ---> MOVES there
        | with room (same ward rule)?         |
        +-------------------------------------+
                            | no
                            v
        +-------------------------------------+
        | Is a grouped chest WITHOUT Evict    |--- yes ---> MOVES there
        | Mismatching nearby with room?       |
        +-------------------------------------+
                            | no
                            v
                  STAYS (nowhere to send it)
```

An item moves at most twice, and never back and forth. A group chest works like a sink: it keeps pulling in its group's items from nearby chests until it is full.

Everything is checked again when:

- an item lands in a chest,
- a chest frees up space (you take something out),
- a chest's group is set, changed or cleared,
- a group's Evict Mismatching is turned on,
- a group's item list changes (Set From Contents),
- Hold routing is turned off,
- a group is deleted.

## Install

You need **BepInExPack for Valheim** installed first.

**Download** `StorageGroups-0.1.0.zip` from the [Releases](../../releases) page, or all the files in the `plugins` folder of this repo. Besides `StorageGroups.dll` and `StorageGroups.Core.dll` there are a few `System.*` and `Microsoft.*` library files the mod needs. All of them are needed.

**With a mod manager (Gale, r2modman, Thunderstore Mod Manager):**

1. Open your profile folder. In Gale: the profile menu, then "Open profile folder".
2. Go to `BepInEx/plugins`.
3. Make a folder called `StorageGroups` and put all the DLLs in it.
4. Start the game through the mod manager.

**Manual install:**

1. Go to your Valheim folder (Steam: right-click Valheim, Manage, Browse local files).
2. Go to `BepInEx/plugins`.
3. Make a folder called `StorageGroups` and put all the DLLs in it.

**Uninstall:** delete the `StorageGroups` folder. Your chests keep their items.

## Multiplayer

- Install on the server and on every player.
- Groups are shared by everyone on the server. Anyone can create, rename or delete a group, and change its settings.
- All chests work together, no matter who built them or who has them open.
- Renaming a group keeps every chest in it, for everyone.

## Wards

- Items never cross the edge of a ward. Chests inside a ward only send items to chests inside the same ward, and chests outside wards only to chests outside wards.
- A chest standing where two wards overlap only routes with chests covered by the same wards.
- Private chests are never touched.

## Works with

- **AzuAutoStore**: AzuAutoStore puts the item in a chest first, then this mod moves it to the right group chest. Tip: turn on Evict Mismatching for your groups, because AzuAutoStore stores into any chest that already has that item.

## Does NOT work with

- **Smart Containers / Smarter Containers**, and other mods that move items between chests on their own. Two sorting mods fight over the same items. This mod will not load if Smart Containers is installed. Remove it first.

## Settings

After the first launch, the config file `BepInEx/config/com.jonasd.valheim.storagegroups.cfg` appears. With a mod manager, open it from the manager's config editor.

- `Routing.RangeMeters` (default 10): how far, in meters, an item can travel to reach another chest. Everyone on a server should use the same value.
- `UI.ShowRoutingMessages` (default off): same as the checkbox in the group menu.

## Disclaimer

- This is a work in progress and not fully tested. Use at your own risk.
- Multiplayer and ward support are the least tested parts. Back up your world before using it on a server, and report anything odd.
- Items are only moved, never created or deleted on purpose. Still, if something goes wrong, the backup is your safety net.
