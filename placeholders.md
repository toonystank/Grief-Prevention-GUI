---
icon: spell-check
---

# Placeholders

Placeholders can be used with the prefix `%griefprevgui_<placeholder>%` or `%gpextension_<placeholder>%`.

## General

- `%griefprevgui_isclaimed [lookingat|x_y_z]%` - Returns true if the location is claimed.
- `%griefprevgui_claimedby [lookingat|x_y_z]%` - Returns the owner of the claim at the location.
- `%griefprevgui_isenabled [economy|list|teleport|warp]%` - Checks if a feature is enabled.
- `%griefprevgui_warpsize%` - Returns the number of claims with warps.
- `%griefprevgui_price [purchase|sell] <amount>%` - Calculates block price.
- `%griefprevgui_prefix%` - Returns the plugin prefix.
- `%griefprevgui_title%` - Returns the plugin title.
- `%griefprevgui_flighttime%` - Returns the player's flight time.
- `%griefprevgui_isholding createwand%` - Returns true if holding the claim creation tool.
- `%griefprevgui_online [player|playeruuid|online]%` - Returns player name, UUID, or online count.
- `%griefprevgui_areaprice <area>%` - Returns the price for a specific area size.

## Player Specific

- `%griefprevgui_claimblocks [formatted]%` - Returns player's available claim blocks.
- `%griefprevgui_remainingblocks [formatted]%` - Returns player's remaining claim blocks.
- `%griefprevgui_claimcount%` - Returns number of claims owned.
- `%griefprevgui_trustcount%` - Returns number of claims trusted in.
- `%griefprevgui_managercount%` - Returns number of claims with manager permissions.
- `%griefprevgui_otherplayer_uuid_<player>%` - Returns UUID of another player.
- `%griefprevgui_otherplayer_displayname_<player>%` - Returns display name of another player.

## Standing In Claim

Placeholders relative to the claim the player is currently standing in.

- `%griefprevgui_standing_id%` - Claim ID.
- `%griefprevgui_standing_owner%` - Claim Owner.
- `%griefprevgui_standing_size%` - Claim Area.
- `%griefprevgui_standing_permission%` - Player's permission level.
- `%griefprevgui_standing_flag_list%` - List of active flags.
- `%griefprevgui_standing_flag_isactive_<flagName>%` - Check if a flag is active.

## By Claim ID

Prefix: `%griefprevgui_getbyid_<subcommand>_<claimID>%` (or `here` for current location)

- `isinvited`: Is the player invited?
- `invitor`: Name of the invitor.
- `size`: Claim area.
- `isexist`: Does the claim exist?
- `expiretime`: Expiration date.
- `issubdiv`: Is it a subdivision?
- `subsize`: Number of subdivisions.
- `owner`: Claim owner name.
- `location`: Formatted center location.
- `trustsize`: Number of trusted players.
- `istrusted`: Is the player trusted?
- `trust <index>`: Name of trusted player at index.
- `trustuuid <index>`: UUID of trusted player at index.
- `permission <UUID>`: Permission level of specific UUID.
- `permissionname <player>`: Permission level of specific player.
- `isbuild`: Does player have build trust?
- `editaccess`: Does player have edit access?
- `canremovepermission <UUID>`: Can player remove permission of UUID?
- `biome`: Center biome.
- `teleportlocation`: Teleport location.
- `centerblock`: Center block type.
- `claimname`: Claim name.
- `claimicon`: Claim icon type.
- `isin`: Is player inside?
- `warplocation`: Warp location.
- `trustlist <separator>`: Formatted trust list.

### Flag Info by ID
- `flags_isactive_<flagName>`
- `flags_isactiveformatted_<flagName>`
- `flags_parma_<flagName>`
- `flags_listflags_<flagName>`

### Blocked/WhiteList Info by ID
- `blocked_size`
- `blocked_players`
- `blocked_contains_<player>`
- `blocked_get_<index>`
- `claimentry_whitelistsize`
- `claimentry_whitelistedplayers`
- `claimentry_blocklistsize`
- `claimentry_blacklistedplayers`
- `claimentry_isblockedforeveryone`
- `claimentry_isblacklisted_<player>`
- `claimentry_iswhitelisted_<player>`

### Mob Spawns Info by ID
- `nomobspawnstype_allowedspawnreasons`
- `nomobspawnstype_disallowedentities`
- `nomobspawnstype_disallowedentity_<entityType>`
- `nomobspawnstype_allowedspawnreason_<reason>`

### Other
- `centerblocklist <index>`: Center block of a trusted claim by index.
- `getclaimid <index>`: Claim ID of a trusted claim by index.