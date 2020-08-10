# Guide to Syncing World of Warcraft Settings Across Devices

## Purpose

To avoid setting up a World of Warcraft UI and settings on multiple computers. This keeps your playing experience consistent no matter what device you're on!

## The folders we will sync

### Interface/Addons

This folder contains any addons that you've installed yourself or from clients like the Twitch client. Syncing this to another device will retain a consistent set of addons across all devices.

### WTF/Account

This folder contains saved account setting information for the WoW installation on your current device. Syncing this to another device will bring across your addon settings and other important saved information.

## Tools

A sync client, such as Dropbox, OneDrive, or similar. I use OneDrive.

## Important usage guidelines

* Cannot have World of Warcraft open on both machines. If WoW is left open on one machine, the files may not be properly synchronized to the syncing tool and settings will be lost
    > Always close WoW when you are done playing or going to play on another computer
* Must wait for files to sync
    > The files should take a very short time to sync, but wait for the files to sync across machines before playing WoW again or settings will be lost

## How to sync the folders in Windows

### Install the sync client

Install the sync client on every computer that you want to sync settings on

### Choose which computer that has the WoW UI that you want and perform the steps on that computer

1. Close World of Warcraft if it is open
1. Create a parent folder in your sync application to store the Addons and Account folder. From this point on, we'll refer to this location as %SYNC_FOLDER%
    > example: C:\Users\username\OneDrive\wow-sync
1. Find and note the location of your World of Warcraft folder. From this point on, we'll refer to this location as %WOW_FOLDER%
    > example: D:\game-installs\World of Warcraft\_retail_
1. (optional but recommended) Copy %WOW_FOLDER%\Interface\Addons and %WOW_FOLDER%\WTF\Account to a backup location so that you can restore them if something goes wrong
1. Cut %WOW_FOLDER%\Interface\Addons to %SYNC_FOLDER%. The Interface\Addons folder should no longer exist in %WOW_FOLDER%
1. Cut %WOW_FOLDER%\WTF\Account to %SYNC_FOLDER%. The WTF\Account folder should no longer exist in %WOW_FOLDER%
1. Open Command Prompt as Administrator
1. Execute the commands below to link the folders that you've copied to your sync folder back into your WoW folder, replacing %WOW_FOLDER% and %SYNC_FOLDER% with the folders you were using above:

> mklink /D "**%WOW_FOLDER%**\Interface\Addons" "**%SYNC_FOLDER%**\Addons"
>
> mklink /D "**%WOW_FOLDER%**\WTF\Account" "**%SYNC_FOLDER%**\Account"

My real example:
> mklink /D "**D:\game-installs\World of Warcraft\_retail_**\Interface\Addons" "**C:\Users\username\OneDrive\wow-sync**\Addons"
>
> mklink /D "**D:\game-installs\World of Warcraft\_retail_**\WTF\Account" "**C:\Users\username\OneDrive\wow-sync**\Account"

### Sanity check

* The Addons folder should be visible in %WOW_FOLDER%\Interface\
* The Account folder should be visible in %WOW_FOLDER%\WTF\
* The Addons and Account folder should both be visible in %SYNC_FOLDER%

### Perform these steps on any computer you want to sync to

1. Close World of Warcraft if it is open
1. Find the parent folder in your sync client where you placed the Addons and Account folder from the source computer. From this point on, we'll refer to this location as %SYNC_FOLDER%
    > example: C:\Users\username\OneDrive\wow-sync
1. Wait for any new files to fully sync from the source computer if they haven't already
1. Find and save the location of your World of Warcraft folder on this computer. From this point on, we'll refer to this location as %WOW_FOLDER%
    > example: D:\game-installs\World of Warcraft\_retail_
1. Cut %WOW_FOLDER%\Interface\Addons and %WOW_FOLDER%\WTF\Account to a backup location so that you can restore them if something goes wrong
1. Verify that the Interface\Addons and WTF\Account folder folders no longer exist in %WOW_FOLDER%
1. Like you've done on the other machine, link the sync folder back into your WoW folder, replacing %WOW_FOLDER% and %SYNC_FOLDER% with the folders you from above:

> mklink /D "**%WOW_FOLDER%**\Interface\Addons" "**%SYNC_FOLDER%**\Addons"
>
> mklink /D "**%WOW_FOLDER%**\WTF\Account" "**%SYNC_FOLDER%**\Account"

My real example:
> mklink /D "**D:\game-installs\World of Warcraft\_retail_**\Interface\Addons" "**C:\Users\username\OneDrive\wow-sync**\Addons"
>
> mklink /D "**D:\game-installs\World of Warcraft\_retail_**\WTF\Account" "**C:\Users\username\OneDrive\wow-sync**\Account"

### Sanity check for any synced machines

* The Addons folder should be visible in %WOW_FOLDER%\Interface\
* The Account folder should be visible in %WOW_FOLDER%\WTF\
* The Addons and Account folder should both be visible in %SYNC_FOLDER%

## FAQ

### What about Mac

You should be able to perform the same steps in this guide, replacing the symbolic link steps from Windows with the equivalent "ln" command on a Mac. I'll leave that to you to look up, or message me and I can help out.

### Different screen resolutions

You may see some UI elements that look out of place if you are syncing setups that run at different resolutions. I personally sync 1440p to 1080p without issues, but something like 4k to 1080p might be troublesome.

### What about my keybindings

Keybindings are stored as part of the character variables that are sent to the WoW servers, which are automatically synced as part of your default game installation. This solution should not affect keybindings.

### What is not synced

Settings that are controlled by the client such as sound and graphics settings. Different computers need different settings for these, so this is an item that thankfully does not sync! Keybindings and character-specific settings in the Interface menu option are also not synced.

### What if the game updates

There will always be a potential case where the solution could break during any future update to the game. With that said, this solution has not broken through several major game updates and I have never had to repair it or recover lost files.
