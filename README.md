# MapleEzorsia v2 (Standalone HD dll client/localhost for v83)

Please follow [setup instructions here](https://github.com/444Ro666/MapleEzorsia-v2/wiki/v83%E2%80%90Client%E2%80%90Setup%E2%80%90and%E2%80%90Development%E2%80%90Guide) for optimal setup.  
See some [gameplay after optimal setup](https://www.youtube.com/watch?v=HxGKn0EjPC0) here.  
Follow the [changelog](https://github.com/444Ro666/MapleEzorsia-v2/wiki/Change-Log).  
[Go to Troubleshooting Section](https://github.com/444Ro666/MapleEzorsia-v2/wiki/v83%E2%80%90Client%E2%80%90Setup%E2%80%90and%E2%80%90Development%E2%80%90Guide#troubleshooting) of the setup guide and see if any fixes help.  
  
This is a `dinput8.dll` DLL that turns the default v83 Maplestory.exe (from NXXXON) or any localhost into an HD client/localhost usable for single-player or with any server.  
It doesn't need an injector or other extra .exe file to work because MapleStory already loads up `dinput8.dll` automatically.  
It just needs the DLL to be in the same folder.
  
You can set your own options in the `config.ini` for:
- width and height for resolution
- IP of the server to connect to
- Amount of loot messages to be shown in the bottom right screen
- Remove Intro videos/Logos
- Enable Tubi
- Set Damage Cap
- Set Speed movement Cap
- Enable Custom Login/Cash shop frames from your own UI.wz/img
- Choose between v62 and v83 EXP tables
- Load up to three custom DLLs in addition
  
## How to use (DLL only)

1. Download all files from [Releases](https://github.com/Phantomeis/MapleEzorsia-v2/tree/main/Release) into your v83 MapleStory directory
   - You can skip the ´/Data´ fodler if you dont plan to load IMG files with your client.
2. Open the `config.ini` (will be auto-generated when removed) and edit the values to your liking.
   - For compatibility with your own WZ edits, see the [troubleshooting section](https://github.com/phantomeis/MapleEzorsia-v2/wiki/v83%E2%80%90Client%E2%80%90Setup%E2%80%90and%E2%80%90Development%E2%80%90Guide#Troubleshooting).
   - I suggest doing all your edits in your own `EzorsiaV2_UI.wz` or `MapleEzorsiaV2wzfiles.img` (if using .IMG) file to avoid WZ conflicts with the base game, and to ensure you can keep track of them.
   - You can load your edits from these custom files by using the string pool hook provided in the release source code.
3. Run your Game and enjoy!
4. If you ran into problems like your game not launching, check out the [troubleshooting section](https://github.com/phantomeis/MapleEzorsia-v2/wiki/v83%E2%80%90Client%E2%80%90Setup%E2%80%90and%E2%80%90Development%E2%80%90Guide#Troubleshooting).

### Optional stuff: 
- [If you want borderless fullscreen and better graphics, check out Magpie](https://github.com/Blinue/Magpie). I personally use this when playing on 1280x720 to force it to cover my screen without graphic quality loss.
- [Default v83 client with windows admin-elevation request removed, and 4GB memory flag enabled](https://mega.nz/file/9uNmHIAZ#zzE7t7T6wQyDbJrHJxgw-AOlmzzwCpLrOKmoUlec_5E): this is the default v83 client but doesn't request windows admin rights and can use 4GB of memory instead of 2g. It crashes less and is easier to use ;) 
- [See my setup instructions here if you want to do the edits yourself for verification](https://github.com/444Ro666/MapleEzorsia-v2/wiki/v83%E2%80%90Client%E2%80%90Setup%E2%80%90and%E2%80%90Development%E2%80%90Guide)

## Features
- The first publicly released standalone DLL client for v83 (functionality added on 11/16/2023).
- No WZ/IMG conflicts; Ezorsia V2 will generate its only WZ/IMG file, compatible with any set of WZ or IMG files, provided it is configured correctly!
- The ability to load 3 custom third-party DLLs that you can specify in the config; these must be in the game folder. Ezorsia v2's edits will take precedence over conflicting edits (sometimes a good thing if those DLL files have things that prevent the game running, and Ezorsia v2 overwrites those same things).
- Pick up and exp gain messages that were centered on the character in the original Ezorsia are fixed and moved to the bottom right. The messages also no longer appear cut off at the beginning. The functionality of announcing the messages has been improved, and the player can now configure how many pick up and exp gain messages they want to display instead of being stuck with 6 maximum (the recommended maximum amount is half your resolution height divided by 14, this will make the messages go up to half your screen).
- Cash shop has been fully fixed, and it now displays as 800x600, centered in the middle of the screen regardless of resolution (you still need UI.wz edit if you don't want the medal text under the character to show outside the left of the preview screen).
- Cash shop preview bug from vanilla v83 has been fixed and now you can move your character right away in preview upon entering the cash shop. Normally you'd have to toggle previewing off and then on again for it to work (vanilla bug).
- Login, world/channel, character select, screens have been fixed and are now centered, and they now display as 800x600, centered in the middle of the screen regardless of resolution (you still need UI.wz edit for the best look, but it works with vanilla login frame as well if EzorsiaV2WzIncluded=false and CustomLoginFrame=false in config).
- Version number, view recommended, buttons, and other UI element related to these screens are centered.
- Fully scaled Mulung Dojo UI, all elements in right spots for each resolution.
- Fully scaled "clear" pop up for small bosses (tested on Capt latanica).
- Systems and shortcuts blue pop-up menus have their locations fixed.
- Various pop-up messages, invites, and requests like party, guild, trade, family, quest complete, party quest available, have been fixed.
- Megaphone avatar location fixed.
- Normal boss bars scale with resolution.
- Window mode that can be turned on and off.
- Logos on game load that can be turned on and off.
- All of the resolution edits that came with original Ezorsia (ones that cause issues have been commented out but still kept for reference).
- Most of the resolution edits from the [RageZone resolution addresses release](https://forum.ragezone.com/threads/all-addresses-for-v83-resolution-change.1161938/), with problematic ones removed and addresses not repeated versus the original Ezorsia addresses.

# Technical Stuff from Author
This DLL modifies addresses in a default, packed, v83 MapleStory client fresh from installation to enable the game to run, as well as changes the game window and canvas resolution to HD. Most in-game component boundaries are also modified to scale with the custom resolution.

The original goal of this DLL is to allow an old 4:3 aspect ratio game to work on 16:9 aspect ratio modern monitors while preserving the original gameplay experience as much as possible. However, I also believe that it is the individual player's choice on how they wish to play the game, so I am willing to be flexible regarding optional functionality. As such, this project has expanded into also becoming a development base that allows plenty of room for expansion and allows the user to play the game their way.

This standalone DLL client is designed to provide a quality, relatively safe, open-source client setup to work alongside open-source servers. This DLL will work with any client or localhost, including the one that comes from a default installation of the game. Deletion of files that come from a default installation is also unnecessary for it to work.

This code can only be compiled on the x86 platform.  
Try these settings if compiling throws errors:  
![Compilation settings](/images/compilationdoesntworkrelease.jpg)  
  
  
Try these settings when debugging doesn't work:  
![Compilation settings](/images/compilationdoesntworkrelease.jpg)

- [HD client setup instructions/development guide](https://github.com/444Ro666/MapleEzorsia-v2/wiki/v83%E2%80%90Client%E2%80%90Setup%E2%80%90and%E2%80%90Development%E2%80%90Guide)
- Original Ezorsia: [Link](https://github.com/izarooni/MapleEzorsia)
- Current most frequently updated open-source v83 server source (checked 2023/10/10): [cosmic](https://github.com/P0nk/Cosmic)
- Coming from another version and need a good localhost? [Check out hendi's releases](https://forum.ragezone.com/threads/localhost-workshop.1202021/)

## Improvements in Source from Original:
- Too many changes to count, see [change log](https://github.com/444Ro666/MapleEzorsia-v2/wiki/Change-Log) and source xD
- Contains examples of function replacement and codecaves
- Occasional helpful comments for further development
- Numerous addresses, some of which aren't used because they aren't related to resolution
- Key edits/addresses have functionality identified (these cause noticeable issues when messed with)

(Note: I have not fully identified all address functionality but I have playtested the game and commented out or modified ones that caused issues; I've also reorganized a lot of the addresses to be closer other addresses in the same memory region)

### Want to Help Me?
My [To-do](https://github.com/444Ro666/MapleEzorsia-v2/wiki/my-to%E2%80%90do-list) list is what I'm currently looking to improve on for the patch in the future. Development will be slower now that it is releasable compared to pre-release. [Click here](https://github.com/444Ro666/MapleEzorsia-v2/blob/main/CONTRIBUTING.md) to see how you can help. You can also see the [guide here](https://github.com/444Ro666/MapleEzorsia-v2/wiki/v83%E2%80%90Client%E2%80%90Setup%E2%80%90and%E2%80%90Development%E2%80%90Guide) on how to develop the patch.

## Credits
I'd like to thank the members of the [Maple Dev Community](https://discord.gg/DU8j6xrW) who took the time to help me when they did. I'd also like to thank the creator of the [original Ezorsia](https://github.com/izarooni/MapleEzorsia) for creating the base I used to work off of and learn from. A special mention to the creators of [MapleClientEditTemplate](https://github.com/MapleStory-Archive/MapleClientEditTemplate) whose rewritten utility functions and type definitions helped transition this project towards more advanced client modifications. Another special mention to [hendi's localhost workshop](https://forum.ragezone.com/threads/localhost-workshop.1202021/) for the guidance about which functions to rewrite to implement a working standalone client DLL and for providing an unvirtualized localhost to analyze. Finally, I'd like to thank everyone who provided the releases and resources on the [setup and development](https://github.com/444Ro666/MapleEzorsia-v2/wiki/v83%E2%80%90Client%E2%80%90Setup%E2%80%90and%E2%80%90Development%E2%80%90Guide) page; I would not have been able to do this work without the work that was done before me.

## License

[AGPL-3.0 license](https://github.com/444Ro666/MapleEzorsia-v2/blob/main/LICENSE) Ezorsia v2 uses the same copyleft license as cosmic and its predecessor heavenms. It is a copyleft license where if the source is used, in part or in whole, in another project, then the resulting "modified" version must also come under the same license (GNU Affero General Public License v3.0)
