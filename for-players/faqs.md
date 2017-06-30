---
layout: default
title: Player's guide to using mods » troubleshooting & FAQs
intro: >
   Welcome to Stardew Valley modding! This guide will help you install mods and
   fix any problems that come up.
permalink: /for-players/faqs
redirect_from:
    - /guides/asking-for-help
    - /guides/smapi-faq
movedToWiki: Modding:Player FAQs
---

<div class="scroll-box" style="float: right;">
    <strong>For players</strong>
    <ul>
        <li><a href="/for-players/intro">Intro</a></li>
        <li><a href="/for-players/install-smapi">Install SMAPI</a></li>
        <li><a href="/for-players/use-mods">Use mods</a></li>
        <li><strong><a href="/for-players/faqs">Troubleshooting & FAQs</a></strong></li>
    </ul>
</div>

## Intro

### Use or create mods
See the _[intro pages](/for-players/intro)_ for using mods, or
_[creating a SMAPI mod](/for-devs/creating-a-smapi-mod)_ for creating mods.

### Find help
For help with a mod, the mod author is the best person to ask. These are the best ways to contact them:

1. the discussion thread linked to on the mod page (if any);
2. the 'bugs' section on the Nexus mod page (if any);
3. otherwise contact the author directly (e.g. use the 'Contact' button on the Nexus mod page).

For help with SMAPI, or if you can't ask the mod author, [post in this thread](http://community.playstarbound.com/threads/dos-and-donts-of-reporting-issues-with-smapi-mods.125211/)
or [ask in Discord](https://discord.gg/kH55QXP).

### What to include in a bug report
<section id="bug-report"></section>

Figuring out why something went wrong for someone else can be tough, so it helps if you include
as much information as possible. Here's the most useful information you can give.

1. Describe your problem:
   * Which mod has an issue?
   * What is the problem? Be as descriptive as possible. (Does the game freeze or close? Does the
     screen go black? Does nothing at all happen?)
   * What were you doing when it broke? Did you notice a pattern? For example, maybe it always
     breaks when you do a certain thing.
2. Describe your context:

   * Do you use a mod manager? If so, which one?
   * Do you play on Linux, Mac, or Windows?

3. Cause the problem again (so any details are in the log), then attach a copy of the latest log
   file.  
   (See _[Where is my error log and how can I share it?](#error-log)_)

## Files
### SMAPI log
The SMAPI log provides useful information for troubleshooting problems. It includes your game and
SMAPI version, which mods you have, where the game is installed, any errors that occurred, and
what happened.

Here's how to share it:

1. Find the log file here:

   Platform | Path
   :------- |:-----
   Windows | `%appdata%\StardewValley\ErrorLogs\SMAPI-latest.txt`<br /><small>(Paste "`%appdata%`" into the address bar, Windows knows where it is.)</small>
   Linux   | `~/.config/StardewValley/ErrorLogs/SMAPI-latest.txt`<br /><small>(The folder is hidden by default. From Files, click _Go » Enter Location_ and enter "~/.config".)</small>
   Mac     | `~/.config/StardewValley/ErrorLogs/SMAPI-latest.txt`<br /><small>(The folder is hidden by default. From Finder, click _Go » Go to Folder_ and enter "~/.config".)</small>

   <small>(If you see a `MODDED_ProgramLog.Log_LATEST.txt` file instead, you have an older version of
   SMAPI. Try [updating to the latest version](https://github.com/Pathoschild/SMAPI/releases).)</small>

2. If you're sharing it...
   * In the [`#modding` Discord channel](https://discord.gg/kH55QXP): just drag the file onto the
     channel to attach it.
   * Somewhere else: attach the file, or send a [pastebin](http://pastebin.com/) link.

### Save files
The game puts save files here:

Platform | Path
:------- |:-----
 Windows | `%appdata%\StardewValley\Saves`<br /><small>(Paste "`%appdata%`" into the address bar, Windows knows where it is.)</small>
 Linux   | `~/.config/StardewValley/Saves`<br /><small>(The folder is hidden by default. From Files, click _Go » Enter Location_ and enter "~/.config".)</small>
 Mac     | `~/.config/StardewValley/Saves`<br /><small>(The folder is hidden by default. From Finder, click _Go » Go to Folder_ and enter "~/.config".)</small>

Each save has a folder like `JonSnow_123456789`, with two main files inside it:
`JonSnow_123456789` and `SaveGameInfo`. Both files are needed to load the save.

To share your save, zip the entire `JonSnow_123456789` folder and send that.

### Game folder
The "game folder" is the folder that contains the `Stardew Valley.exe` or `StardewValley.exe`
file. The default locations are:

Platform | Path
:------- | :----
Windows  | GOG: `C:\Program Files (x86)\GalaxyClient\Games\Stardew Valley`<br />Steam: `C:\Program Files (x86)\Steam\steamapps\common\Stardew Valley`
Linux    | GOG: `~/GOG Games/Stardew Valley/game`<br />Steam: `~/.local/share/Steam/steamapps/common/Stardew Valley`
Mac      | GOG: `/Applications/Stardew Valley.app/Contents/MacOS`<br />Steam: `~/Library/Application Support/Steam/steamapps/common/Stardew Valley/Contents/MacOS`

If your game isn't in the default location, here's how to find it:

* If you have the GOG version:
  * Open the GOG Galaxy client.
  * In the game sidebar, right-click on _Stardew Valley_.
  * Choose _Manage Installation > Show Folder_ to open the game folder.

* If you have the Steam version:
  * Open the Steam client and go to the library view (the view that lists your games).
  * Right-click on _Stardew Valley_.
  * Click _Properties_.
  * Click the _Local Files_ tab.
  * Click the _Browse Local Files..._ button to open the game folder.

## Troubleshooting

### Common issues
Let's run through a quick checklist:

1. Are you running the latest versions? The versions are listed in the first line of the console
   window:

   > ![](images/faqs/smapi-versions.png)
   
   Make sure you have [Stardew Valley 1.2.26+](http://stardewvalleywiki.com/Version_History) and the
   [latest version of SMAPI](https://github.com/Pathoschild/SMAPI/releases).

2. Are you using a Stardew Valley mod manager? Those are still experimental, so they can cause
   problems. Try downloading the mod manually.

3. See the sections below for solutions to specific errors.

### Could not load file or assembly 'Stardew Valley'
That error means SMAPI couldn't find your `Stardew Valley.exe` (Windows) or `StardewValley.exe`
(Linux/Mac) file, probably because SMAPI isn't in the right folder. Make sure you're running
`StardewModdingAPI.exe` in your [game folder](#game-folder), _not_ the one in the downloaded
installer folder. See the [official install instructions](/for-players/install-smapi) for
detailed steps.

### Ignored folder "..." which doesn't have a manifest.json
SMAPI couldn't find the `manifest.json` file for the mod in that folder. That usually means it's
not a SMAPI mod, so it won't work from the `Mods` folder. See that mod's documentation for install
instructions.

### SEHException: External component has thrown an exception
<section id="sehexception"></section>

You may see an error like this with `SEHException` in the text:

```
System.Runtime.InteropServices.SEHException (0x80004005): External component has thrown an exception.
   at new[](UInt32 )
   at Microsoft.Xna.Framework.Audio.UnsafeNativeMethods.AllocateArrayAndReadFile(String filename, Void** ppData, UInt32* pdwBufferSize)
   at Microsoft.Xna.Framework.Audio.UnsafeNativeMethods.WaveBank.CreateHandle(UInt32 hEngine, String string, Int32 length, IntPtr& pCleanup)
   at Microsoft.Xna.Framework.Audio.WaveBank..ctor(AudioEngine audioEngine, String nonStreamingWaveBankFilename)
   at StardewValley.Game1.Initialize()
   at StardewModdingAPI.Inheritance.SGame.Initialize() in D:\source\_Stardew\SMAPI\src\StardewModdingAPI\Inheritance\SGame.cs:line 302
   at Microsoft.Xna.Framework.Game.RunGame(Boolean useBlockingRun)
   at Microsoft.Xna.Framework.Game.Run()
   at StardewModdingAPI.Program.StartGame() in D:\source\_Stardew\SMAPI\src\StardewModdingAPI\Program.cs:line 274
```

That error happens in the game's audio startup code, which is very sensitive to resources being
used before the audio is ready. This isn't caused by SMAPI directly, though SMAPI uses some extra
resources during startup.

Common solutions:

* Restart your computer.
* Close your browsers and any open apps before playing. (You can reopen them once the game is started.)
* Remove any mods that change the game's audio (e.g. mods which add more music).

### SMAPI contains a trojan?
<section id="trojan"></section>

* **Why does this happen?**  
  Some antivirus programs may warn you that SMAPI contains a trojan with scary names like
  "Peals.A!cl". Don't worry, SMAPI doesn't actually have a trojan. That warning is based on something
  called a _heuristic detection_ — basically the antivirus looked at the SMAPI code, and saw
  something trojan-like. That's because SMAPI can rewrite your mods so they work on your
  computer (mainly so players can use the same mods on Linux, Mac, or Windows). Rewriting files is
  something trojans also do, so your antivirus got suspicious.

* **How do I know it doesn't _really_ have a trojan?**  
  You can check! SMAPI is all open-source, so you can
  [read the code](https://github.com/Pathoschild/SMAPI) to make sure it's not doing anything shady.
  If you don't trust the download, you can [decompile it](https://www.jetbrains.com/decompiler/)
  and see what code it really contains.

* **How do I fix it?**  
  You just need to tell your antivirus that SMAPI is okay. How you do that depends on which program
  you use. Try searching online for your antivirus name with the words "add exception" to find
  answers.
