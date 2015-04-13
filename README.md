# fixes
================
LIST OF FIXES: 
================
* FIX:      GetPlayerColor
* PROBLEM:  Returns "0" if "SetPlayerColor" has never been called.
* SOLUTION: Call "SetPlayerColor" in "OnPlayerConnect".
* SEE:      "OnPlayerConnect".
* AUTHOR:   KoczkaHUN
* POST:     http://forum.sa-mp.com/showpost.php?p=1486048
* 
* FIX:      FILTERSCRIPT
* PROBLEM:  Despite the fact that is in every new script, many people don't
*           define "FILTERSCRIPT" where appropriate.
* SOLUTION: Provide an "IS_FILTERSCRIPT" variable (note the naming to match
*           the original macro).
* AUTHOR:   Y_Less
* SEE:      "OnFilterScriptInit" and "OnGameModeInit".
* 
* FIX:      SpawnPlayer
* PROBLEM:  Kills the player if they are in a vehicle.
* SOLUTION: Remove the from the vehicle.
* SEE:      "FIXES_SpawnPlayer".
* AUTHOR:   Y_Less
* 
* FIX:      SetPlayerName
* PROBLEM:  Using "SetPlayerName" when the new name only differs from the old
*           name in case does not alter the name at all.
* SOLUTION: Change their name twice - once to "_FIXES TEMP NAME" and then to
*           the actual required name.
* SEE:      "OnPlayerConnect" and "FIXES_SetPlayerName".
* AUTHOR:   Y_Less/Slice
* 
* FIX:      GetPlayerSkin
* PROBLEM:  Returns the new skin after "SetSpawnInfo" is called but before the
*           player actually respawns to get the new skin.
* SOLUTION: Record the skin in "OnPlayerSpawn" and always return that one.
* SEE:      "OnPlayerSpawn", "FIXES_GetPlayerSkin" and "FIXES_SetPlayerSkin".
* AUTHOR:   Y_Less
* 
* FIX:      GetWeaponName
* PROBLEM:  Returns nothing for 18, 44, and 45.
* SOLUTION: Return the correct names ("Molotov Cocktail", "Thermal Goggles",
*           and "Night vision Goggles").
* SEE:      "FIXES_GetWeaponName".
* AUTHOR:   Y_Less
* 
* FIX:      SetPlayerWorldBounds
* PROBLEM:  Aiming can bypass the edge.
* SOLUTION: Check for the player leaving the area and reset them to their last
*           good position if they leave the area (aiming or not).
* SEE:      "OnPlayerUpdate" and "FIXES_SetPlayerWorldBounds".
* AUTHOR:   Y_Less
* 
* FIX:      TogglePlayerControllable
* PROBLEM:  Other players see you moving on the spot.
* SOLUTION: Return 0 in OnPlayerUpdate.
* SEE:      "FIXES_TogglePlayerControllable" and "OnPlayerUpdate".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=876854
* 
* FIX:      HydraSniper
* PROBLEM:  Entring military aircraft with a sniper rifle messes up vies.
* SOLUTION: Set their armed weapon to fists.
* SEE:      "OnPlayerStateChange", "FIXES_GivePlayerWeapon",
*           "FIXES_SetPlayerArmedWeapon".
* AUTHOR:   funky1234
* POST:     http://forum.sa-mp.com/showpost.php?p=965644
* 
* FIX:      IsPlayerInCheckpoint
* PROBLEM:  Function returns an undefined value if it is called before any
*           other checkpoint functions are called to initialise the value.
* SOLUTION: Call "DisablePlayerCheckpoint" when they connect.
* SEE:      "OnPlayerConnect".
* AUTHOR:   Y_Less
* 
* FIX:      IsPlayerInRaceCheckpoint
* PROBLEM:  Function returns an undefined value if it is called before any
*           other race checkpoint functions are called to initialise the value.
* SOLUTION: Call "DisablePlayerRaceCheckpoint" when they connect.
* SEE:      "OnPlayerConnect".
* AUTHOR:   Y_Less
* 
* FIX:      GetPlayerWeapon
* PROBLEM:  Returns the old value after using "SetPlayerArmedWeapon" when they
*           are in a vehicle.
* SOLUTION: If "SetPlayerArmedWeapon" is called in a vehicle, store the new
*           value and return that instead.
* SEE:      "OnPlayerStateChange", "FIXES_SetPlayerArmedWeapon", and
*           "FIXES_GetPlayerWeapon".
* AUTHOR:   Y_Less
* 
* FIX:      PutPlayerInVehicle
* PROBLEM:  If this is used on a passenger the driver of their old vehicle
*           doesn't see them in their new vehicle.
* SOLUTION: Remove them from the vehicle first.
* SEE:      "OnPlayerStateChange" and "FIXES_PutPlayerInVehicle".
* AUTHOR:   leong124/Y_Less
* POST:     http://forum.sa-mp.com/showpost.php?p=1265965
* 
* FIX:      KEY_AIM
* PROBLEM:  "KEY_AIM" isn't defined by default.
* SOLUTION: Define it.
* SEE:      N/A.
* AUTHOR:   Y_Less
* 
* FIX:      SetPlayerCheckpoint
* PROBLEM:  If a checkpoint is already set it will use the size of that
*           checkpoint instead of the new one.
* SOLUTION: Call "DisablePlayerCheckpoint" before setting the checkpoint.
* SEE:      "FIXES_SetPlayerCheckpoint".
* AUTHOR:   KoczkaHUN
* POST:     http://forum.sa-mp.com/showpost.php?p=1482401
*
* FIX:      SetPlayerRaceCheckpoint
* PROBLEM:  If a checkpoint is already set it will use the size of that
*           checkpoint instead of the new one.
* SOLUTION: Call "DisablePlayerRaceCheckpoint" before setting the checkpoint.
* SEE:      "FIXES_SetPlayerRaceCheckpoint".
* AUTHOR:   KoczkaHUN
* POST:     http://forum.sa-mp.com/showpost.php?p=1482401
*
* FIX:      TextDrawCreate
* PROBLEM:  Crashes on a blank string.
* SOLUTION: Intercept blank strings.
* SEE:      "FIXES_TextDrawCreate".
* AUTHOR:   wups
* POST:     http://forum.sa-mp.com/showpost.php?p=1484008
* 
* FIX:      TextDrawSetString
* PROBLEM:  Crashes on a blank string and size greater than 1024.
* SOLUTION: Intercept blank strings and truncate long strings.
* SEE:      "FIXES_TextDrawSetString".
* AUTHOR:   TomTrox
* POST:     http://forum.sa-mp.com/showpost.php?p=1487870
* 
* FIX:      AllowInteriorWeapons
* PROBLEM:  Does nothing.
* SOLUTION: Set the player's weapon to fists in an interior.
* SEE:      "FIXES_AllowInteriorWeapons", "OnGameModeInit" and
*           "OnPlayerUpdate".
* AUTHOR:   KoczkaHUN
* POST:     http://forum.sa-mp.com/showpost.php?p=1502696
* 
* FIX:      OnPlayerEnterVehicle
* PROBLEM:  Crashes other players when people enter an invalid seat.
* SOLUTION: Desync the people with invalid seats.
* SEE:      "OnPlayerStateChange" and "OnPlayerUpdate".
* AUTHOR:   RyDeR`/Y_Less
* POST:     http://forum.sa-mp.com/showpost.php?p=1410296
* 
* FIX:      AllowTeleport
* PROBLEM:  0.3dRC9 removed "AllowPlayerTeleport" and "AllowAdminTeleport" in
*           favour of "OnPlayerClickMap".  Some scripts used the old code and.
* SOLUTION: Teleport the player in "OnPlayerClickMap".
* SEE:      "OnPlayerClickMap", "FIXES_AllowPlayerTeleport", and
*           "FIXES_AllowAdminTeleport".
* AUTHOR:   Y_Less
* 
* FIX:      SetPlayerSpecialAction
* PROBLEM:  Removing jetpacks from players by setting their special action to 0
*           causes the sound to stay until death.
* SOLUTION: Call "ClearAnimations" before "SetPlayerSpecialAction".
* SEE:      "FIXES_SetPlayerSpecialAction".
* AUTHOR:   MP2
* POST:     Private message from MP2.
* 
* FIX:      OnDialogResponse
* PROBLEM:  Cheaters can spoof the dialogid they are using to respond to ones
*           they can't actually see.
* SOLUTION: Store the displayed dialogid and use that instead.
* SEE:      "FIXES_OnDialogResponse", "FIXES_ShowPlayerDialog".
* AUTHOR:   Y_Less
* FIXED IN: 0.3e RC6
* 
* FIX:      GetPlayerDialog
* PROBLEM:  This function doesn't exist.  Fixed for hidden dialogs.
* SOLUTION: Add it.  DEFAULTS TO FALSE!
* SEE:      "FIXES_GetPlayerDialog".
* AUTHOR:   Y_Less/xX_Simon_Xx
* POST:     http://forum.sa-mp.com/showpost.php?p=2141254
* 
* FIX:      SetSpawnInfo
* PROBLEM:  Kicks the player if "SpawnPlayer" is called before "SetSpawnInfo".
* SOLUTION: Call "SetSpawnInfo" at least once.
* SEE:      "OnPlayerConnect".
* AUTHOR:   Y_Less
* 
* FIX:      SetPlayerSkin
* PROBLEM:  Breaks sitting on bikes.
* SOLUTION: Put them back in the vehicle after setting their skin.
* SEE:      "FIXES_SetPlayerSkin".
* AUTHOR:   CyNiC
* POST:     http://forum.sa-mp.com/showpost.php?p=1756094
* 
* FIX:      HideMenuForPlayer
* PROBLEM:  Crashes when passed an invalid menu ID.
* SOLUTION: Don't hide it when passed an invalid menu.
* SEE:      "FIXES_HideMenuForPlayer".
* AUTHOR:   Y_Less
* POST:     http://forum.sa-mp.com/showpost.php?p=1787297
* 
* FIX:      valstr
* PROBLEM:  Crashes on large numbers.
* SOLUTION: Use "format" instead.
* SEE:      "FIXES_valstr".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      fclose
* PROBLEM:  Crashes on an invalid handle.
* SOLUTION: Check for an invalid handle.
* SEE:      "FIXES_fclose".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      fwrite
* PROBLEM:  Crashes on an invalid handle.
* SOLUTION: Check for an invalid handle.
* SEE:      "FIXES_fwrite".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      fread
* PROBLEM:  Crashes on an invalid handle.
* SOLUTION: Check for an invalid handle.
* SEE:      "FIXES_fread".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      fputchar
* PROBLEM:  Crashes on an invalid handle.
* SOLUTION: Check for an invalid handle.
* SEE:      "FIXES_fputchar".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      fgetchar
* PROBLEM:  Crashes on an invalid handle.
* SOLUTION: Check for an invalid handle.
* SEE:      "FIXES_fgetchar".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      fblockwrite
* PROBLEM:  Crashes on an invalid handle.
* SOLUTION: Check for an invalid handle.
* SEE:      "FIXES_fblockwrite".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      fblockread
* PROBLEM:  Crashes on an invalid handle.
* SOLUTION: Check for an invalid handle.
* SEE:      "FIXES_fblockread".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      fseek
* PROBLEM:  Crashes on an invalid handle.
* SOLUTION: Check for an invalid handle.
* SEE:      "FIXES_fseek".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      flength
* PROBLEM:  Crashes on an invalid handle.
* SOLUTION: Check for an invalid handle.
* SEE:      "FIXES_flength".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1790300
* 
* FIX:      file_inc
* PROBLEM:  All file.inc fixes are included separately for major overhead.
* SOLUTION: Optionally group them all under one define.  DEFAULTS TO FALSE!
* SEE:      "FIX_file_inc".
* AUTHOR:   Y_Less
* 
* FIX:      IsPlayerAttachedObjectSlotUsed
* PROBLEM:  Doesn't work in OnPlayerDisconnect.
* SOLUTION: Maintain an internal record of slots used.
* SEE:      "FIXES_SetPlayerAttachedObject",
*           "FIXES_RemovePlayerAttachedObject",
*           "FIXES_IsPAttachedObjectSlotUsed", and
*           "OnPlayerDisconnect".
* AUTHOR:   Y_Less
* 
* FIX:      SetPlayerAttachedObject
* PROBLEM:  Doesn't remove objects when the mode ends.
* SOLUTION: Remove them.
* SEE:      "FIXES_SetPlayerAttachedObject",
*           "FIXES_RemovePlayerAttachedObject", and
*           "OnPlayerDisconnect".
* AUTHOR:   Y_Less
* 
* FIX:      OnPlayerDeath
* PROBLEM:  Clients get stuck when they die with an animation applied.
* SOLUTION: Clear their animations.
* SEE:      "OnPlayerDeath" and "OnPlayerUpdate".
* AUTHOR:   h02
* POST:     http://forum.sa-mp.com/showpost.php?p=1641144
* 
* FIX:      strins
* PROBLEM:  Ignores the "maxlength" parameter causing possible crashes.
* SOLUTION: Manually check the length.
* SEE:      "FIXES_strins".
* AUTHOR:   Slice/Y_Less
* POST:     http://forum.sa-mp.com/showpost.php?p=1860495
* POST:     http://forum.sa-mp.com/showpost.php?p=1864706
* 
* FIX:      IsPlayerConnected
* PROBLEM:  Only uses the lower two bytes of a passed ID.
* SOLUTION: Mask the numbers.
* SEE:      "FIXES_IsPlayerConnected".
* AUTHOR:   Slice
* POST:     http://forum.sa-mp.com/showpost.php?p=1860464
* 
* FIX:      OnPlayerCommandText
* PROBLEM:  Can crash ZCMD when passed a null string.
* SOLUTION: Pass NULL if invalid inputs given.
* SEE:      "OnPlayerCommandText".
* AUTHOR:   Y_Less
* POST:     http://forum.sa-mp.com/showpost.php?p=1909511
* 
* FIX:      TrainExit
* PROBLEM:  When getting out of a train entered by "PutPlayerInVehicle", the
*           camera does not reset properly.
* SOLUTION: Reset the camera.
* SEE:      "FIXES_PutPlayerInVehicle", "FIXES_OnPlayerStateChange".
* AUTHOR:   Terminator3/Y_Less
* POST:     http://forum.sa-mp.com/showpost.php?p=1980214
* 
* FIX:      Kick
* PROBLEM:  Calling "Kick" in "OnPlayerConnect" doesn't work properly.
* SOLUTION: Defer it.
* SEE:      "OnPlayerConnect", "FIXES_Kick".
* AUTHOR:   Y_Less
* POST:     http://forum.sa-mp.com/showpost.php?p=1989453
* 
* FIX:      OnVehicleMod
* PROBLEM:  Crashes other players when invalid mods are applied.
* SOLUTION: Desync the player.
* SEE:      "OnVehicleMod".
* AUTHOR:   JernejL/Y_Less
* POST:     http://forum.sa-mp.com/showpost.php?p=1671500
* 
* FIX:      random
* PROBLEM:  Doesn't work with negative numbers.
* SOLUTION: Invert then reinvert.  DEFAULTS TO FALSE!
* SEE:      "FIXES_random".
* AUTHOR:   xX_Simon_Xx
* POST:     http://forum.sa-mp.com/showpost.php?p=2141254
* 
* ==============
*  STYLE RULES: 
* ==============
* 
* All globals should be "static stock" whenever possible (so they can only be
*     accessed from this one file).
* 
* Statics must start with "FIXES_gs", and all other globals with "FIXES_g".
* 
* All functions not overriding existing functions must start with "FIXES_".
* 
* Macros must be upper case, use underscores, and start "FIXES_":
*     "FIXES_LIKE_THIS".
* 
* Functions should be upper camel case (as the original functions are)
*     "FIXES_LikeThis".
* 
* Globals (after the prefix) should be upper camel case, and locals lower camel
*     case "likeThis".
* 
* ALS should be used to hook functions and callbacks.
* 
* The ALS prefix for chaining is also "FIXES_"
* 
* Enums start with "E_" or "e_" depending on type, then follow rules for
*     macros.
* 
* Use "FIXES_gsCallbackHooks" and "E_FIXES_CALLBACK_HOOKS" for ALS chaining.
* 
* NO libraries should be included - not even the default SA:MP ones.  Let the
*     user do it.
* 
* Due to the above rule, you cannot assume any third party libraries AT ALL, so
*     do not use them.
* 
* Certain terms may be shortened when dealing with long callback names to avoid
*     compile truncation warnings (max symbol length is 31).  Current list:
*     
*     "Checkpoint" -> "CP"
*     "Update"     -> "Upd"
*     "TextDraw"   -> "TD"
*     "Object"     -> "Obj"
*     "Player"     -> "P"
* 
* Document all fixes at the top of the file, and highlight code.
* 
* 4 space TABS - do not edit this file in PAWNO unless you know how to correct
*     the indentation.
* 
* All rules have exceptions, but they must be justifiable.  For example
*     "IS_FILTERSCRIPT" is a global variable, but is not called
*     "FIXES_gIsFilterscript" to better match the "FILTERSCRIPT" macro it
*     replaces.  Now a macro for "_FIXES_gIsFilterscript".
* 
* Variables which need to be fully global (i.e. not "static"), but should not
*     actually be used by other people (e.g. appear inside a macro) should be
*     prefixed with "_FIXES" instead of "FIXES" to indicate their private use.
* 
* No comments beyond the end of column 80 (where the line in "PAWNO" is).
* 
* When redefining a native, add a "BAD_" external name declaration with the
*     "_ALS_" definition so that others may use the original native if they so
*     desire (with the caveat that it may break all fixes).  Note the "BAD_"
*     name is meant to indicate the possibility of breaking the fix, not a
*     comment on the original native function.
* 
* If a bug is fixed in some version of the server it can be conditionally
*     included here.  This is done by checking for the existance of a native
*     function introduced in the same server version.  For example
*     "TogglePlayerControllable" was fixed in 0.3eRC6, the same time as the
*     "SetObjectMaterial" native was introduced, thus the inclusion becomes:
*     
*     #if !defined FIX_TogglePlayerControllable
*         #define FIX_TogglePlayerControllable (!defined SetObjectMaterial)
*     #endif
*     
*     This only includes this fix if that native doesn't exist.
* 
* To reduce general memory consumption, strings in this include are stored
*     globally in constant arrays and referenced.  This is EXACTLY as fast as
*     using the string constants directly, but means that strings are not
*     stored in the assembly multiple times (unless the string is only used
*     once, in which case it's more work for no gain).  See this post for more
*     details:
*     
*     http://forum.sa-mp.com/showpost.php?p=1795601
* 
* Documentation explanation:
* 
*     FIX:      <Short name>
*     PROBLEM:  <Description of problem>
*     SOLUTION: <Description of solution>
*     SEE:      <List of relevant functions>
*     AUTHOR:   <Person who wrote the fix>
*     POST:     <Link to the original post where applicable>
*     FIXED IN: <Server version of official fix where applicable>
