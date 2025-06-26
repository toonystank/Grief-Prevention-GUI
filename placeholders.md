---
icon: spell-check
---

# Placeholders

The following is a comprehensive list of placeholders provided by the GriefPrevention GUI Addon for use with PlaceholderAPI. These placeholders can be used in GUIs, messages, and other plugin integrations to display dynamic information about claims, players, and settings.

## Placeholder List

* `%griefprevgui_isclaimed%`
* `%griefprevgui_isclaimed_lookingat%`
* `%griefprevgui_isclaimed_x_y_z%`
* `%griefprevgui_claimedby%`
* `%griefprevgui_claimedby_lookingat%`
* `%griefprevgui_claimedby_x_y_z%`
* `%griefprevgui_isenabled_economy%`
* `%griefprevgui_isenabled_list%`
* `%griefprevgui_isenabled_teleport%`
* `%griefprevgui_isenabled_warp%`
* `%griefprevgui_warpsize%`
* `%griefprevgui_price_purchase_amount%`
* `%griefprevgui_price_sell_amount%`
* `%griefprevgui_prefix%`
* `%griefprevgui_title%`
* `%griefprevgui_flighttime%`
* `%griefprevgui_isholding_createwand%`
* `%griefprevgui_otherplayer_uuid_playername%`
* `%griefprevgui_otherplayer_displayname_playername%`
* `%griefprevgui_online_player%`
* `%griefprevgui_online_playeruuid%`
* `%griefprevgui_online_online%`
* `%griefprevgui_areaprice_area%`
* `%griefprevgui_claimblocks%`
* `%griefprevgui_remainingblocks%`
* `%griefprevgui_claimcount%`
* `%griefprevgui_trustcount%`
* `%griefprevgui_managercount%`
* `%griefprevgui_getclaimid_index%`
* `%griefprevgui_standing_id%`
* `%griefprevgui_standing_owner%`
* `%griefprevgui_standing_size%`
* `%griefprevgui_standing_permission%`
* `%griefprevgui_standing_flag_list%`
* `%griefprevgui_standing_flag_isactive_flagname%`
* `%griefprevgui_getbyid_isinvited_{claimid}%`
* `%griefprevgui_getbyid_invitor_{claimid}%`
* `%griefprevgui_getbyid_size_{claimid}%`
* `%griefprevgui_getbyid_isexist_{claimid}%`
* `%griefprevgui_getbyid_trustlist_{claimid}_{permission}%`
* `%griefprevgui_getbyid_expiretime_{claimid}%`
* `%griefprevgui_getbyid_issubdiv_{claimid}%`
* `%griefprevgui_getbyid_subsize_{claimid}%`
* `%griefprevgui_getbyid_blocked_size_{claimid}%`
* `%griefprevgui_getbyid_blocked_players_{claimid}%`
* `%griefprevgui_getbyid_blocked_contains_{claimid}_{player}%`
* `%griefprevgui_getbyid_blocked_get_{claimid}_{index}%`
* `%griefprevgui_getbyid_owner_{claimid}%`
* `%griefprevgui_getbyid_location_{claimid}%`
* `%griefprevgui_getbyid_trustsize_{claimid}%`
* `%griefprevgui_getbyid_istrusted_{claimid}%`
* `%griefprevgui_getbyid_trust_{claimid}_{index}%`
* `%griefprevgui_getbyid_trustuuid_{claimid}_{index}%`
* `%griefprevgui_getbyid_permission_{claimid}_{uuid}%`
* `%griefprevgui_getbyid_permissionname_{claimid}_{playername}%`
* `%griefprevgui_getbyid_isbuild_{claimid}%`
* `%griefprevgui_getbyid_editaccess_{claimid}_{uuid}%`
* `%griefprevgui_getbyid_canremovepermission_{claimid}_{uuid}%`
* `%griefprevgui_getbyid_biome_{claimid}%`
* `%griefprevgui_getbyid_teleportlocation_{claimid}%`
* `%griefprevgui_getbyid_centerblock_{claimid}%`
* `%griefprevgui_getbyid_claimname_{claimid}%`
* `%griefprevgui_getbyid_claimicon_{claimid}%`
* `%griefprevgui_getbyid_claimentry_whitelistsize_{claimid}%`
* `%griefprevgui_getbyid_claimentry_whitelistedplayers_{claimid}%`
* `%griefprevgui_getbyid_claimentry_blocklistsize_{claimid}%`
* `%griefprevgui_getbyid_claimentry_blacklistedplayers_{claimid}%`
* `%griefprevgui_getbyid_claimentry_isblockedforeveryone_{claimid}%`
* `%griefprevgui_getbyid_claimentry_isblacklisted_{claimid}_{player}%`
* `%griefprevgui_getbyid_claimentry_iswhitelisted_{claimid}_{player}%`
* `%griefprevgui_getbyid_nomobspawnstype_allowedspawnreasons_{claimid}%`
* `%griefprevgui_getbyid_nomobspawnstype_disallowedentities_{claimid}%`
* `%griefprevgui_getbyid_nomobspawnstype_disallowedentity_{claimid}_{entity}%`
* `%griefprevgui_getbyid_nomobspawnstype_allowedspawnreason_{claimid}_{reason}%`
* `%griefprevgui_getbyid_claimdescription_{claimid}%`
* `%griefprevgui_getbyid_isin_{claimid}%`
* `%griefprevgui_getbyid_warplocation_{claimid}%`
* `%griefprevgui_getbyid_centerblocklist_{index}%`
* `%griefprevgui_getbyid_flags_isactive_{flagname}_{claimid}%`
* `%griefprevgui_getbyid_flags_isactiveformatted_{flagname}_{claimid}%`
* `%griefprevgui_getbyid_flags_parma_{flagname}_{claimid}%`
* `%griefprevgui_getbyid_flags_listflags_{flagname}%`

## Notes

* **Usage**: Use these placeholders in GUI configurations (e.g., `menu_title`, `display_name`, `lore`), messages, or other PlaceholderAPI-compatible plugins.
* **Dynamic Parameters**: Placeholders with `{claimid}`, `{player}`, `{uuid}`, `{index}`, `{flagname}`, `{permission}`, `{entity}`, or `{reason}` require specific values (e.g., a claim ID, player name, or flag name like `ChangeBiome`).
* **Dependencies**: Some placeholders (e.g., those using `{player}`) require the PlaceholderAPI `Player` expansion. Install it via `/papi ecloud download Player` if needed.
* **Testing**: Test placeholders in your server to ensure they return expected values, especially for dynamic parameters like `{claimid}` or `{flagname}`.

For further assistance, refer to the GriefPrevention GUI Addon documentation or contact the server admin.
