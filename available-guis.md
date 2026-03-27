---
icon: building
---

# Available GUIs

The GriefPrevention GUI Addon includes the following built-in GUIs. GUIs marked as **Custom** dynamically populate content at runtime and may require a specific template section in their `items` configuration.

## Standard GUIs

These GUIs display only items defined in their YAML file — what you configure is exactly what you get.

| GUI Name | File Name | Purpose |
|---|---|---|
| `MAIN_MENU` | `ClaimMenu.yml` | Main interface for managing claims and accessing other GUIs. |
| `CLAIM_INFO` | `ClaimInfo.yml` | Displays detailed information about a specific claim (location, biome, trust, flags). |
| `CLAIM_PERMISSIONS` | `ClaimPermissions.yml` | Manages trust and permission settings for a claim. |
| `CLAIM_BLOCKS` | `ClaimBlock.yml` | Handles claim block-related actions (buy, sell, view). |
| `CLAIM_DELETE` | `ClaimDelete.yml` | Confirmation GUI for deleting a specific claim. |
| `CLAIM_DELETE_ALL` | `ClaimDeleteAll.yml` | Confirmation GUI for deleting all claims owned by a player. |
| `CLAIM_KICK` | `ClaimKick.yml` | Allows kicking players from a claim. |
| `CLAIM_LEAVE` | `ClaimLeave.yml` | Confirmation GUI for leaving a specific claim. |
| `CLAIM_LEAVE_ALL` | `ClaimLeaveAll.yml` | Confirmation GUI for leaving all claims. |
| `CLAIM_UPGRADE_NO_ENTER` | `ClaimUpgradeNoEnter.yml` | Manages upgrades for claims with the NoEnter flag. |

## Dynamic GUIs

These GUIs dynamically populate items at runtime. They may require a **matching section** in their `items` configuration that acts as a template for dynamically generated items.

| GUI Name | File Name | Template Section | Purpose |
|---|---|---|---|
| `CLAIM_LIST` | `ClaimList.yml` | `CLAIM_LIST` | Lists all claims owned or accessible by the player. Supports sorting by permission, distance, flag, type, and expiration. |
| `CLAIM_TRUST` | `TrustList.yml` | `CLAIM_TRUST` | Lists trusted players for a claim with their trust levels. |
| `PLAYER_LIST` | `PlayerList.yml` | `PLAYER_LIST` | Lists players for trust management. Supports online/offline filtering. |
| `WARP` | `WarpList.yml` | `WARP` | Displays warpable claims (those with the `ClaimWarp` flag). |
| `EXPIRING_CLAIMS` | `ExpiringClaimList.yml` | `EXPIRING_CLAIMS` | Shows claims nearing expiration, sortable by soonest. |
| `ICON_SELECTOR` | `IconSelector.yml` | `ICON_SELECTOR` | Allows selecting a claim icon from all Minecraft materials. Supports category filtering (Block, Edible, Record). |
| `CHUNK_CLAIM` | `ChunkClaim.yml` | Per-status sections | Visual grid of chunks around the player. Supports claiming, extending, zooming, and status-specific sections (`CHUNK_CLAIM_OWNED`, `CHUNK_CLAIM_TRUSTED`, etc.). |
| `NO_MOB_SPAWNS_TYPE` | `NoMobSpawnsType.yml` | `NO_MOB_SPAWNS_TYPE` | Configures mob spawn restrictions (entities or spawn reasons). |
| `NO_MOB_AI_TYPE` | `NoMobAIType.yml` | `NO_MOB_AI_TYPE` | Configures which mob AIs are disabled within a claim. |
| `NO_VEHICLE_TYPE` | `NoVehicleType.yml` | `NO_VEHICLE_TYPE` | Configures vehicle type restrictions within a claim. |
| `BLOCKS` | `ClaimBlock.yml` | `BLOCKS` | Manages claim block purchases or allocations. |
| `BLACKLIST` | `BlackList.yml` | `BLACKLIST` | Manages blacklisted players for the NoEnter flag. |
| `WHITELIST` | `Whitelist.yml` | `WHITELIST` | Manages whitelisted players for the NoEnter flag. |
| `CLAIM_INVITES` | `ClaimInvites.yml` | `CLAIM_INVITES` | Manages claim invitations (when invite trust mode is enabled). |
| `CLAIM_UPGRADE` | `ClaimUpgrade.yml` | `CLAIM_UPGRADE` | Handles claim flag upgrades. |
| `CLAIM_BLOCKS_SELECTOR` | `ClaimBlockSelector.yml` | `CLAIM_BLOCKS_SELECTOR` | Allows selection of claim block purchase/sell amounts. |
| `TEMPLATE_LIST` | `TemplateList.yml` | `TEMPLATE_LIST` | Lists available claim templates. |
| `GUESTBOOK` | `GuestbookMenu.yml` | `GUESTBOOK` | Manages and views guestbook entries for a claim. |

> **Template Section:** For dynamic GUIs, the template section defines the appearance (material, lore, commands) of each dynamically generated item. The plugin fills the GUI with items using this template. Without it, dynamic items won't render.
