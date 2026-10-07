# Index

- [Required Items](#required-items)
- [Identify Corrupt Data](#identify-corrupt-data)
- [How to Remove Corrupt Data](#how-to-remove-corrupt-data)
- ["The Usual Fix"](#the-usual-fix)
- [Prevent Data Corruption](#prevent-data-corruption)
- [More Resources](#more-resources)

> **Make a full backup of your save files before attempting any of these steps!**

---

# Required Items

## Steam Workshop Mods Folder (Workshop Mods)

* Can be accessed by clicking the folder icon on a Steam Workshop in the Paralives Mod Menu.
* By navigating to:

**Windows:**

```text
C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
```

**Mac:**

```text
~/Library/Application Support/Steam/steamapps/workshop/content/1118520
```

## Paralives Folder (Local Mods)

* Can be accessed by clicking the folder icon on a local mod in the Paralives Mod Menu.
* By navigating to:

**Windows:**

```text
C:\Users\USER\AppData\LocalLow\Paralives\Paralives
```

**Mac:**

```text
~/Library/Application Support/com.Paralives.Paralives/
```

## Paralives\Player.Log

* Can be read with any text file reading software such as Notepad or Notepad++.
* Located in the Paralives\Paralives Folder.
* Provides logs for current or last played Paralives session.

## Paralives\MySavedGames.mod Folder

* Folder containing all current save games and auto saves.
* Located in the Paralives\Paralives Folder.
* This folder is more important than any other.
* Please regularly make a full copy of this folder to a safe location outside of the game files!

## Paralives\MyPremadeHouseholds.mod Folder

* Households saved to the library.

## Paralives\MyPremadeLot.mod Folder

* Lots saved to the library.

## Paralives\MyPremadeOutfits.mod Folder

* Outfits saved to the library.

## Paralives\Local.mod and 0.mod Folder

* Stores game settings like custom swatches.

---

# Identify Corrupt Data

Corrupt data is made of files that have been changed to no longer be in the form or sequence the game is expecting to find.

## Out of Date Files

* The game has updated and these files no longer comply with the current syntax.
* While this can happen occasionally with mods, almost all bepinex code injection plugins become out of date following a game update.
* If a bepinex plugin is installed but mods are still not working, the plugin may be doing more harm than good.

## Improperly Modified Files

* These have been modified by a player, modder, or even the game engine and now are incorrect.
* This is mods or plugins being used and then being removed.

For example, a mod used to add a custom outfit and then the mod is removed but the outfit is still identified in the game files.

It may be impossible to remove some mods without breaking a save file.

## Files Improperly Moved

* Files are often moved by the player, the game engine, or by Steam and some parts of the file are left behind or deleted.

## How will the game tell me which files are corrupt?

The game engine will try to tell the user when there is an error through direct and indirect notifications.

### Direct:

* On screen popups
* Notifications in the console
* Events in the player.log

### Indirect:

* Flickering
* Flashing
* Stuttering
* Lag
* Crashing
* Canceling operations

## Reading the Error Console and Player.Log

The error console and player.log reports overlap only partially so it is import to check both when trying to identify an error.

It is important to identify the initial error and ignore additional errors caused by the first error. When reading the error log, attempt to fix the errors from top to bottom in sequential order.

If multiple errors are introduced at the same time, it can be very hard to diagnose. It is important to make only a small number of changes between tests.

If the game is working smoothly, make note of the errors in the log so that they can be ruled out later on when something breaks.

### ERROR CONSOLE

* The error console is accessed in game as a tab in the cheat menu.
* It cannot be used if the game will not load.

1. Press Ctrl+Shift+C open the cheat menu.
2. Press the carrot to switch to the console tab.
3. The console is sorted into three categories of importance.
4. Only red errors are important as it concerns this tutorial.

### PLAYER.LOG & PLAYER-PREV.LOG

* This file logs actions done by the Unity game engine running Paralives.
* Player.log is overwritten each time the game is started and moved to Player-prev.log.
* It is located in the Paralives\Paralives local mods folder.
* More information can be put in the log by enabling options in the control panel. Too many options can quickly make the log very large in size.
* If something in the log is important, make a copy!

### Good Errors (at least not bad):

```text
+ Meta cache is expired
+ Loaded asset database (No metacache) of mod Local.mod in 0.06581748 seconds
+ The referenced script on this Behaviour (Game Object 'SlackService') is missing!
+ Serialization depth limit 10 exceeded
+ Loaded asset database of mod MyPremadeLot.mod in 0.04702377 seconds
+ Unloading 10 unused Assets to reduce memory usage
```

### Bad Errors:

```text
- NullReferenceException: Object reference not set to an instance of an object
- Material builder got given parameters that don't match any shaders
- Could not resolve 'ProceduralRig/ReachWithLeftArm/ArmLChainIK/TargetArmLChainIK'
- FileNotFoundException
- Failed to find setting class
- Could not register Paralives Town.saved
```

> Note: In version 1.7, there are three new red errors in the console and the player.log that do not seem to negatively affect game performance.
>
> * `+ System Exception: Invalid Path...`
> * `+ Runtime data is null...`
> * `+ OperationException: Addressables...`

> Note: In version 1.8A, the .fbx importer did not work properly would get stuck on the importing assets screen.

---

# Types of Errors

The kinds of problems going on at a technical level.

## Null Reference

* Sometimes null pointer reference.
* Any error along the lines of setting, item, mesh, or value could not be found.
* The game references a object which it cannot find or it did not understand what it found

> Note: The game is able to handle some null references and several are part of the early access version of the game.

## Out of Bounds

* The game was given a value outside of the expected range.
* If game is expecting a value between 0 and 10 but the value it receives in 10842 then it may cause an error.

## Translation

* The game tried to fix a file determined to be broken and the output was incorrect.

For example an issue with .tmp files ⁠.mod.meta and .tmp

## Syntax

* The game updated and the mod no longer conforms to the standards set by the game. Most common with Bepinex code injection plugins.
* Some mods created when the game launched are missing colons in the text file.

---

# Categories of Symptoms

When the cause of the error is unknown, the goal is to correlate symptoms to a specific cause. After every error is fixed then the game will work. Here are arbitrary categories to help group similar errors into clusters.

It is important to identify the initial error and ignore additional errors caused by the first error.

## Cat A — Launch Game

### Symptoms

* Game can't get to the Paralives main menu
* The screen is black
* Game crashes when launching the game from Steam
* An error appears when launching the game from Steam
* The game is stuck on a picture of clouds.

### Possible Solutions

* Check hardware meets the minimum requirements to play Paralives.
* A critical file used while the game is launching is corrupt, unreadable, or inaccessible.
* Start by validating game files.
* Make an exception for Paralives in anti-virus.
* Check player.log for errors in the paralives/paralives local mods folder.

## Cat B — Importing Assets

### Symptoms

* Stuck on importing assets

### Possible Cause

A mod file is unreadable.

### Possible Solutions

* Remove newest mods from paralives/paralives local mod folder or Steam Workshop folders until problem is resolved.
* Validate game files.

## Cat C — Select a Save

### Symptoms

* Game returns to the main menu when attempting to load a save
* Save file is white

### Possible Cause

Save file has incorrect file names, is missing files, or is unreadable

### Possible Solution

Start by checking the save name matches the meta files inside and the save contains all required components.

## Cat D — Load a Save

### Symptoms

* Game gets stuck while loading save
* Game stays on loading screen forever

### Possible Cause

Corrupt mod, a mod was removed improperly, or save file corruption such as a null reference error.

It may be impossible to remove some mods without breaking a save file.

### Possible Solution

Test if errors persist in a new save game.

## Cat E — Live Mode

### Symptoms

* Game gets stuck or freezes when opening a menu in live mode
* Game gets stuck or freezes when when performing a specific action in live mod

### Possible Cause

Corrupt mod, a mod was removed improperly, or save file corruption such as a null reference error.

It may be impossible to remove some mods without breaking a save file.

### Possible Solution

Test if errors persist in a new save game.

## Cat F — Menus

### Symptoms

* Game menu will not open when clicked
* Game menu is blank when clicked
* Game menu will not close

### Possible Cause

Corrupt mod, a mod was removed improperly, or save file corruption such as a null reference error.

It may be impossible to remove some mods without breaking a save file.

### Possible Solution

Test if errors persist in a new save game.

## Cat G — Installing Mods

### Symptoms

* Mods won't install

### Possible Solutions

* Check Steam and Local mods folder for partial files.
* Delete corrupt mod files preventing download.

## Cat H — Missing Mods

### Symptoms

* Installed mods do not show in the mod menu
* Installed mods show on the mod menu but do not show in game

### Possible Solutions

* Check for corrupt mods.
* Check for duplicated mod files.

## Cat I — Validating Mods

### Symptoms

* Installed mod items do not show when equipped to character
* Installed mod items have disappeared
* Character with mod items disappeared
* Mod items look strange
* Mod items interact in an unexpected way
* Mod items are the wrong color, shape, or size

### Possible Solution

Check for corrupt mods.

---

> **Make a full backup of your save files before attempting any of these steps!**

---

# How to Remove Corrupt Data

Sorted by difficulty level and complexity.

## Easy

### Turn Mods off and On

* Sometimes the mods do not initialize properly which can be fixed by turning just one mod off and on again using the ingame mod menu.

### Restart Paralives

* The game has safe guards against corrupt data which activate when the game is started.
* This may seem silly but restarting the game multiple times can be effective in some scenarios.

### Start a new save game

* If the errors are too complicated or can not be fixed then starting a new game save may be the best option.

### Validate game files or reinstall the game using Steam

* In the Steam client, with the game shutdown:

  * Steam > Paralives > Properties > Verify integrity of games files

### Resubscribe to all mods to clear any corrupt files

1. Add all subscribed mods to a custom collection
2. Unsubscribe from all mods
3. Subscribe to all mods in collection

### Remove mods until the corrupt mod is removed

* Remove one mod at a time or use the 50/50 method to remove half of the mods until the corrupt mod is identified.
* Mods can still cause bugs even when turned off. They need to be removed completely by moving, unsubscibing, or deleting the mod files.
* The game may need to be restarted between each test to ensure cached files are purged.
* Document your findings and write down which mods work!

### Resubscribe to mods slowly to insure mods install properly

* The theory is that installing too many at once causes errors so install mods slowly.
* The game is designed to install mods quickly but perhaps there is something to this.

---

## Intermediate

### Move Steam Workshop mods to the Paralives\Paralives local mods folder

* Mods installed locally are interpreted differently by the game engine which may fix the error.
* While the game is not running, open the file explorer, return to the Steam Workshp Mod Folder:

  ```text
  C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
  ```
* Put ".mod" in the search bar. If no results, then try "*.mod".
* This will return the folders containing mods within the Steam Mods folder.
* Select, cut, and paste all the .mod folders to the local mods folder Paralives\Paralives.
* All of the folders should be moved at once.
* Then unsubscribe from the mods to prevent Steam from copying them back.
* Make sure the copy in the Steam Workshop mods folder is properly deleted as having two copies of one mod can cause errors.

### Delete any files remaining in the Steam workshop mod folders

* Return to workshop\content\1118520\ and remove any files which were not properly disposed of.
* Make sure to pay attention to the details as small mistakes will be hard to find later.
* Lingering files are very likely to cause errors when the game is not expecting them.

### Use console commands to repair a corrupt save file by removing corrupt data

* `CLEARALLOCCUPATIONS` will delete all jobs and job history for the selected para and can not be undone.
* `CLEARCHARACTEROUTFITS` will delete all outfits for selected para and can not be undone.
* `CLEARINVENTORY` empties the inventory for selected para and can not be undone.
* The tutorial linked below explains the available cheat coomands.

Tutorial for cheat commands ⁠Console and Cheat Commands

### Install a code injection plugin to manage mod errors

* These plugins work by giving the game engine more time to process each mod file and helping the game engine diagnos errors.
* Plugins may also cause additional data corruption if not maintained and updated properly.
* Plugins will hopefully become unneccesary as the Paralives devs add more error correcting code to the game.

Paralines Launcher Plugin ⁠Paraline Launcher [Help | Bug R…

---

## Advanced

### Purge the local mods folder

* This is required in order to get a proper fresh start.
* Steam Cloud may need to be turned off to prevent corrupt files from being restored during testing.

1. Cut and paste the local mods folder to a safe location outside of the game files such as the desktop
2. Validate game files using Steam
3. Restart the game. When the game is started, Paralives will regenerate the entire local mods folder from scratch.
4. Verify a new local mods folder has been generated.
5. Check if the problem is solved.

   * Yes: Reintroduce important files from the copy made in step 1.
   * No: Attempt other methods of fixing the problem before reintroducing old files.
6. Only add files to the newly generated Paralives folder which are believed to be safe to reduce chances of copying the corrupt data files.

### Edit save files directly to remove corrupt data

* Save files are text files and can be modified directly.
* Any text editor can be used but Notepad++ with a plugin for formatting json files is preferred.
* The tutorial linked below explains how save files are formatted.

Explanation of the local mods folder ⁠Mod Folder/Save Folder

### Move safe parts of a save to a new save file

* When the problem with the save cannot be indentified, move small pieces to a new save.
* This method can be helpful when attempting to identify corrupt files.
* For example, household folders can be dragged between saves with relatively minimal data loss.
* The tutorial linked below explains how save files are formatted.

Explanation of the local mods folder ⁠Mod Folder/Save Folder

### Use console commands to rebuild characters on a new save

* When all is lost, perhaps it is best to start over on a new save but with a bit of a headstart.
* Commands like `SETMONEY` can be used add money.
* Commands can be used to restore skills, recipes, and more.
* The tutorial linked below explains the available cheat coomands.

Tutorial for cheat commands ⁠Console and Cheat Commands

---

> **Make a full backup of your save files before attempting any of these steps!**

# "The Usual Fix"

The slash-and-burn method for fixing most problems by deleting every file associated with the game to give the best possible fresh start. I don't recommend this solution for all problems because this may make old modded saves unplayable without the mods they depend on to work properly.

## Purge every game file for a fresh start

1. Purge the game files by cutting and pasting the entire paralives/paralives local mods folder to the desktop.
2. Unsubscribe from all Steam Workshop mods and delete any lingering mod files.
3. Validate game files using Steam or reinstall the game.
4. Restart Paralives.
5. Start a new save game.
6. If the game now works, slowly rollback the changes until the problem returns and you will know the cause of the problem.

---

# Prevent Data Corruption

## Make copies of EVERYTHING and OFTEN

* Make a hard copy of important files to a safe location such as the desktop outside the game files.
* Files accessible by the Paralives game engine can always be corrupted.

> Note: The ZIPSAVEFILE command will make a copy of your current save on the desktop. It may overwrite the old copy if the command is used twice.

Tutorial for cheat commands ⁠Console and Cheat Commands

`ZIPSAVEFILE` makes a zip of the current save file on the desktop

## Read Mod Reviews

* And leave reviews too!
* Comments on mods are how the modder and other users share information about mods.
* If the mod seems broken, let the modder know so they can fix it!

## Disable Steam Cloud

* Steam Cloud is amazing for protecting important files but sometimes it causes hard to find issues.
* Steam Cloud likes to bring back expired files without telling anyone and just slip them in there for you to find later.

## Properly Remove Mods

* Mods add items references to the game.
* Every instance of these items need to be removed manually from the game save BEFORE removing the mod.
* It is much easier to remove mod items in game rather than by modifying a save file.
* Delete that fancy couch and that fun sweater before you remove the mod!

## Update Drivers

* For this tutorial the driver to focus on is for the graphics card (GPU).
* For windows, download the Nvidia or AMD app and install the new driver every few months.

## Update Operating System

* Yeah eww gross but it is important!
* Run built in update software such as Windows Update on a regular basis.

## Install mods slowly and check installed mods individually or in small batches

* This might help the game process each file without making mistakes.

## Preventative Maintainence for hardware

* Take care of the computer and it will take care of you.
* Install and run securely obtained anti-malware software.
* Inspect for physical damage and clean out dust.
* Run built in programs for checking component health and stability.

---

# More Resources

## Threads discussing mod issues (where I get my test subjects)

* Dev fix recommendations
  https://steamcommunity.com/app/1118520/discussions/1/569288683937662349/
* Missing mods mega thread
  https://discord.com/channels/595045400805769238/1517352862395404499
* Mods not loading
  https://discord.com/channels/595045400805769238/1517449529174130779
* Null reference errors
  https://discord.com/channels/595045400805769238/1517532031662424154
* Null reference errors
  https://discord.com/channels/595045400805769238/1513991069379858515/1517000216207822899
* Corrupt mod files
  https://discord.com/channels/595045400805769238/1517266950944981062
* Paralives wiki
  https://paralives.wiki.gg/wiki/Portal:Modding_guides
* Paralives change log
  https://www.paralives.com/news
* Paralives development
  https://www.paralives.com/development
* Paralives roadmap
  https://paralives.notion.site/f138c4f6cb234604be16fe4198d17f51
* Known bugs
  https://discord.com/channels/595045400805769238/1508927230154244216
* Paralives roadmap
  https://paralives.notion.site/f138c4f6cb234be16fe4198d17f51
* Known bugs

The contents of this repository, source code, documentation, and associated files, may not be used for AI model training, dataset creation, or other machine-learning purposes.
  known-issues-and-bugs
