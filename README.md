# Simple Slots

A simple quickswitch mod for gzdoom, attempting to improve quality of life by making weapons easier to select/use

# Features

* ZScript based
* "Last weapon used" key, similar to Half-Life
* Holster key, which lowers your current weapon and hides the crosshair.
* The ability to create "Slots"
    * Slots are like special versions of the number keys
    * Slots can be "hold" or "toggle" depending on how long you press the button for
    * The highest-priority weapon in the slot will be selected, otherwise it will go down the list
    * Can dynamically assign weapons to/from slots using hotkeys
    * Weapons selected via Slots don't count when using Last-Weapon key, so they are good for "quick" selections like melee weapons
* Works for all Doom-Engine games including Doom, Doom 2, Heretic, Hexen and Strife, as well as any other IWADs or PWADs including TCs like Ashes.

## Installation ##

Just run it in GZDoom alongside any other mod.

This mod modifies Crosshair #5. This is usually the "right angle" crosshair, which is replaced by a blank crosshair.
Project Brutality modifies the same crosshair to also be blank, making these mods compatible.

This mod will conflict with other mods that change Crosshair #5, and players who use that crosshair will no longer be able to use it.

## Using the Mod ##

This mod defines a few keybinds: Last Used Weapon, the CONFIG key, and a key for each slot (up to 10).

By default, "Last Used Weapon" (bound to Q by default) will work similar to other games with similar features - after selecting at least 2 weapons, pressing the last weapon key will switch to the previously selected weapon.

By holding the CONFIG key, the Last Used Weapon button becomes an Ignore button, which will add the players currently selected weapon to the ignore list. Ignored weapons will always be skipped when using the Last Weapon key.

While holding the CONFIG key, each slot can have any number of weapons assigned. Pressing the slot button while the CONFIG key is held will assign the players currently selected weapon to the slot. Pressing it while the weapon is in the slot will remove it.

Slots can be selected by either pressing the slot key, or by holding it. If it is held, the last weapon will automatically be selected when the slot key is released. Weapons selected via slots are always skipped when using the Last Weapon key.

Slots also have a priority system. When selecting a slot, the last-added weapon will be selected. If it's unavailable, the previously added weapon will be selected, and so on. By default all weapons are added to slots at the highest priority. By using the CONFIG button and pressing the slot key, you can increase the priority for the selected weapon to maximum if it is not already at the highest priority. Otherwise, it will be removed from the slot.

It's recommended to use slots for "quickswitching" between weapons that are needed frequently but aren't normally desired in general play. For example, it may be worthwhile to assign a slot for the Axe/Chainsaw in project brutality, allowing quick, easy access to melee weapons when needed, but otherwise not disrupting the last weapon key.

### Usage Examples ###

**Example 1: Slot Usage**

I am playing Project Brutality. My last selected weapon was the M2 Plasma Rifle. I currently have the Shotgun equipped. I have the Double Barrel Shotgun assigned to Slot 1. While playing, I am suddenly confronted by a Baron of Hell. I quickly press the Q key to switch to my M2 Plasma Rifle. After blasting the Baron, I run out of ammo and need to reload, leaving me sitting ducks against their attacks. Thinking quickly, I hold my Slot 1 key, pulling out the Double Barrel Shotgun. I blast the Baron, finally killing it. I then release the slot key, switching back to the M2 plasma rifle, allowing me to reload. Seeing some weaker enemies ahead, I press the Q key again to switch back to the Shotgun, leaving my M2 Plasma Rifle ready to be selected on a moments notice with the Q key.

**Example 2: Slot Priority**

I am playing Project Brutality. I have assigned the Axe and the Chainsaw to Slot 1. While exploring, I am ambushed by a large number of Pinky demons. They are too strong to take out with Project Brutality's melee button, so I hold my Slot 1 key instead, selecting the Axe. After chopping through them, I release the key to switch back to my previous weapon. Later in the level, I find the Chainsaw. In a subsequent ambush, I am surrounded by pinkies and revenants, as well as other powerful demons. Holding my Slot 1 key, I pull out the chainsaw, cutting through them with ease. Then I release the key to switch back to my previous weapon.

**Example 3: Ignoring Weapons**

I am playing Ashes 2063. While using the Shotgun, I enter a dark area. I previously used the FAL, so it's my last weapon. I press G to pull out my lantern, which works by automatically switching to the Crowbar, which has been set as ignored. While in the darkness, I see an enemy. I press Q to switch away from the crowbar back to my shotgun. While fighting I run out of shotgun ammo, and in a panic, I press Q again to switch from the shotgun to the FAL, allowing me to finish off the enemy.

## Building ##

Please note that the repository only contains source code with no transient data (no zscript include files or compiled ACS script)
**Premade release versions are ready to go on the [Releases page](https://github.com/tunbridgep/doom-simpleslots/releases).**

If you wish to build the project yourself, please follow the following steps:

1. Clone or download the repository
2. Create an include file for all files in the zsc directory. Zscript includes are discussed in detail [here](https://zdoom.org/wiki/ZScript)
3. [Zip the contents of the src directory as a pk3](https://zdoom.org/wiki/Using_ZIPs_as_WAD_replacement), then run in GZDoom by dragging and dropping it onto gzdoom.exe, using the -file parameter or using another method.

Alternatively, a config.json file is provided for use with my [doom-quickbuild](https://github.com/tunbridgep/doom_quickbuild) utility.

## Contributing ##

There are many ways to contribute to the project. The easiest way is by filing a bug report or feature request, however code and documentation contributions are welcome. Documentation of the various features and lighting modes is especially important. All pull requests are welcome, however code should generally follow these rules:

1. ZScript should always be preferred over DECORATE and ACS.
2. Features should be as compatible as possible. Changing or overriding a function or flag on an actor is preferred over simply making a new actor.
3. Almost no thought has been put into multiplayer. This mod has not been tested at all with multiplayer. It is not required for contributions to consider multiplayer, however some consideration would be appreciated. A good example of small considerations is considering whether a console command should exist within the user or server space, and using netevents wherever possible.
4. Consideration should be made for hubs. There is not a significant number of popular hub maps for Doom, however this mod is intended to eventually support Hexen, at which point hub map support will be required. This is usually as simple as checking for e.Reopen when defining/using an event handler.
5. Documentation should be clear. Pull requests and commits should be well documented. Code should be documented where necessary if the intention or logic is not clear. Please follow the existing code style.

For questions or feature suggestions, feel free to create an issue on the issues page, or email me at tunbridge.p+doom@gmail.com

## Other Stuff ##

Checkout my other mods on github

* [Simple Teleporter Effects](https://github.com/tunbridgep/doom-simpleteleportereffects) - add particle effects to any teleporter in any map in a compatible way
* [Simple Saving](https://github.com/tunbridgep/doom-simplesaving) - remove save scumming and tie saving to resource usage.
* [Simple Inventory Items](https://github.com/tunbridgep/doom-inventoryitems) - make most Doom powerups usable from the inventory bar in a compatible way.
* [Simple Completion Rewards](https://github.com/tunbridgep/doom-simplecompletionrewards) - be rewarded for getting 100% completion in a map. Highly configurable.
* [Flashlight Mod](https://github.com/tunbridgep/doom-flashlight) - adds a usable flashlight, the ability to darken the map, a dynamic system for enemy and player stealth, and more.
