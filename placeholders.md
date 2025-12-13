---
icon: spell-check
---

# Placeholders

All placeholders can be used with either the **`%griefprevgui_...%`** or **`%gpextension_...%`** prefix.

## 🟢 Global Player Data
Statistics regarding the player viewing the placeholder.

| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_claimblocks%` | Total accrued claim blocks. |
| `%griefprevgui_claimblocks_formatted%` | Total claim blocks formatted (e.g., 1.5k). |
| `%griefprevgui_remainingblocks%` | Remaining available claim blocks. |
| `%griefprevgui_remainingblocks_formatted%` | Remaining blocks formatted. |
| `%griefprevgui_claimcount%` | Number of claims owned by the player. |
| `%griefprevgui_trustcount%` | Number of claims the player is trusted in. |
| `%griefprevgui_managercount%` | Number of claims the player has manager permissions in. |
| `%griefprevgui_flighttime%` | Remaining flight time. |
| `%griefprevgui_isholding_createwand%` | Returns `true` if holding the claim creation tool (Golden Shovel). |

## 🌍 World & Economy
General server and economy information.

| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_online_online%` | Total count of players online. |
| `%griefprevgui_online_player%` | Viewer's player name. |
| `%griefprevgui_online_playeruuid%` | Viewer's UUID. |
| `%griefprevgui_otherplayer_uuid_<name>%` | Get the UUID of a specific player name. |
| `%griefprevgui_otherplayer_displayname_<name>%` | Get the display name of a specific player name. |
| `%griefprevgui_warpsize%` | Total number of claims on the server that have a public warp set. |
| `%griefprevgui_price_purchase_<amount>%` | Calculate the cost to **buy** `<amount>` claim blocks. |
| `%griefprevgui_price_sell_<amount>%` | Calculate the return to **sell** `<amount>` claim blocks. |
| `%griefprevgui_areaprice_<area>%` | Calculate the cost for a claim of a specific area size. |
| `%griefprevgui_isenabled_economy%` | Returns `true` if economy integration is enabled. |
| `%griefprevgui_isenabled_teleport%` | Returns `true` if teleportation features are enabled. |
| `%griefprevgui_isenabled_warp%` | Returns `true` if warp features are enabled. |

## 🔍 Location Checks
Check if specific locations are claimed.

| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_isclaimed_lookingat%` | `true` if the block the player is looking at is claimed. |
| `%griefprevgui_isclaimed_<x>_<y>_<z>%` | `true` if the specific coordinates are claimed. |
| `%griefprevgui_claimedby_lookingat%` | Name of the owner of the claim being looked at. |
| `%griefprevgui_claimedby_<x>_<y>_<z>%` | Name of the owner at the specific coordinates. |

## 📍 "Standing In" Context
These placeholders return data strictly about the claim the player is **currently standing inside**.

| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_standing_id%` | The numerical ID of the claim. |
| `%griefprevgui_standing_owner%` | The name of the claim owner. |
| `%griefprevgui_standing_size%` | The total area size (blocks). |
| `%griefprevgui_standing_permission%` | The viewer's permission level in this claim (e.g., Access, Trust, Manager, Owner). |
| `%griefprevgui_standing_flag_list%` | A list of all active flags in this claim. |
| `%griefprevgui_standing_flag_isactive_<flag>%` | `true` if the specific `<flag>` is active here. |

## 🆔 Specific Claim Data (Get By ID)
Retrieve information about any claim by its ID.
> **Note:** You can replace `<ID>` with **`here`** to automatically target the claim the player is standing in.

### Basic Information
| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_getbyid_owner_<ID>%` | Name of the claim owner. |
| `%griefprevgui_getbyid_claimname_<ID>%` | The custom name of the claim. |
| `%griefprevgui_getbyid_claimdescription_<ID>%` | The description of the claim. |
| `%griefprevgui_getbyid_claimicon_<ID>%` | The icon material of the claim (e.g., GRASS_BLOCK). |
| `%griefprevgui_getbyid_location_<ID>%` | Formatted center location of the claim. |
| `%griefprevgui_getbyid_size_<ID>%` | Total area size. |
| `%griefprevgui_getbyid_biome_<ID>%` | The biome at the center of the claim. |
| `%griefprevgui_getbyid_expiretime_<ID>%` | Date/Time when the claim will expire. |
| `%griefprevgui_getbyid_isexist_<ID>%` | `true` if a claim with this ID exists. |
| `%griefprevgui_getbyid_isin_<ID>%` | `true` if the viewer is currently inside this claim. |
| `%griefprevgui_getbyid_warplocation_<ID>%` | The formatted location of the claim's warp. |
| `%griefprevgui_getbyid_issubdiv_<ID>%` | `true` if this claim is a subdivision. |
| `%griefprevgui_getbyid_subsize_<ID>%` | The number of subdivisions inside this claim. |
| `%griefprevgui_getbyid_centerblock_<ID>%` | Returns the material of the center block. |

### Permissions & Trust
| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_getbyid_istrusted_<ID>%` | `true` if the viewer is trusted in this claim. |
| `%griefprevgui_getbyid_isbuild_<ID>%` | `true` if the viewer has build permission. |
| `%griefprevgui_getbyid_trustsize_<ID>%` | Total number of trusted players. |
| `%griefprevgui_getbyid_trustlist_<type>_<ID>%` | Formatted list of trusted players.<br>Types: `manager`, `trusted`, `inventory`, `access`. |
| `%griefprevgui_getbyid_trust_<ID>_<index>%` | Get the **Name** of the trusted player at `<index>`. |
| `%griefprevgui_getbyid_trustuuid_<ID>_<index>%` | Get the **UUID** of the trusted player at `<index>`. |
| `%griefprevgui_getbyid_permission_<ID>_<UUID>%` | Get the permission level of a specific UUID. |
| `%griefprevgui_getbyid_permissionname_<ID>_<Name>%` | Get the permission level of a specific Name. |
| `%griefprevgui_getbyid_editaccess_<ID>_<UUID>%` | `true` if the viewer is allowed to edit the permissions of `<UUID>`. |
| `%griefprevgui_getbyid_canremovepermission_<ID>_<UUID>%` | `true` if the viewer is allowed to remove `<UUID>` from the claim. |

### Flags
| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_getbyid_flags_isactive_<flag>_<ID>%` | `true`/`false` if the flag is active. |
| `%griefprevgui_getbyid_flags_isactiveformatted_<flag>_<ID>%` | "Enabled"/"Disabled" (formatted). |
| `%griefprevgui_getbyid_flags_parma_<flag>_<ID>%` | Returns the flag's specific value parameter. |
| `%griefprevgui_getbyid_flags_listflags_<ID>%` | Returns a list of all active flags. |

### Bans & Entry Control
| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_getbyid_blocked_size_<ID>%` | Number of blocked players. |
| `%griefprevgui_getbyid_blocked_players_<ID>%` | List of blocked player names. |
| `%griefprevgui_getbyid_blocked_contains_<ID>_<Name>%` | `true` if the specific player is blocked. |
| `%griefprevgui_getbyid_blocked_get_<ID>_<index>%` | Get the blocked player name at `<index>`. |
| `%griefprevgui_getbyid_claimentry_<ID>_whitelistsize%` | Number of whitelisted players (NoEnter). |
| `%griefprevgui_getbyid_claimentry_<ID>_whitelistedplayers%` | List of whitelisted players. |
| `%griefprevgui_getbyid_claimentry_<ID>_iswhitelisted_<Name>%` | `true` if the specific player is whitelisted. |
| `%griefprevgui_getbyid_claimentry_<ID>_blocklistsize%` | Number of blacklisted players (NoEnter). |
| `%griefprevgui_getbyid_claimentry_<ID>_blacklistedplayers%` | List of blacklisted players. |
| `%griefprevgui_getbyid_claimentry_<ID>_isblacklisted_<Name>%` | `true` if the specific player is blacklisted. |
| `%griefprevgui_getbyid_claimentry_<ID>_isblockedforeveryone%` | `true` if the claim is closed to everyone. |

### Mob Spawning
| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_getbyid_nomobspawnstype_allowedspawnreasons_<ID>%` | List of allowed spawn reasons. |
| `%griefprevgui_getbyid_nomobspawnstype_disallowedentities_<ID>%` | List of disallowed entity types. |
| `%griefprevgui_getbyid_nomobspawnstype_disallowedentity_<ID>_<Entity>%` | `true` if the entity type is disallowed. |
| `%griefprevgui_getbyid_nomobspawnstype_allowedspawnreason_<ID>_<Reason>%` | `true` if the spawn reason is allowed. |

### Utility
| Placeholder | Description |
| :--- | :--- |
| `%griefprevgui_getbyid_isinvited_<ID>%` | `true` if the viewer has a pending invite to this claim. |
| `%griefprevgui_getbyid_invitor_<ID>%` | Name of the person who invited the viewer. |
| `%griefprevgui_getbyid_centerblocklist_<index>%` | Returns the center block icon of the Nth claim in the viewer's list. |
| `%griefprevgui_getclaimid_<index>%` | Returns the Claim ID of the Nth claim in the viewer's trust list. |
