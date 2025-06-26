---
icon: building
---

# Available GUIs

The GriefPrevention GUI Addon includes the following default GUIs, each serving a specific purpose. GUIs marked as _Custom_ dynamically populate content and require a specific section in their `items` configuration (e.g., `ICON_SELECTOR` for the Icon Selector GUI).

| GUI Name                 | File Name                 | Custom | Purpose                                                                |
| ------------------------ | ------------------------- | ------ | ---------------------------------------------------------------------- |
| `MAIN_MENU`              | `ClaimMenu.yml`           | No     | Main interface for managing claims and accessing other GUIs.           |
| `CLAIM_INFO`             | `ClaimInfo.yml`           | No     | Displays detailed information about a specific claim.                  |
| `CLAIM_PERMISSIONS`      | `ClaimPermissions.yml`    | No     | Manages trust and permission settings for a claim.                     |
| `CLAIM_BLOCKS`           | `ClaimBlock.yml`          | No     | Handles claim block-related actions.                                   |
| `CLAIM_DELETE`           | `ClaimDelete.yml`         | No     | Confirms deletion of a specific claim.                                 |
| `CLAIM_DELETE_ALL`       | `ClaimDeleteAll.yml`      | No     | Confirms deletion of all claims owned by a player.                     |
| `CLAIM_KICK`             | `ClaimKick.yml`           | No     | Allows kicking players from a claim.                                   |
| `CLAIM_LEAVE`            | `ClaimLeave.yml`          | No     | Confirms leaving a specific claim.                                     |
| `CLAIM_LEAVE_ALL`        | `ClaimLeaveAll.yml`       | No     | Confirms leaving all claims.                                           |
| `CLAIM_UPGRADE_NO_ENTER` | `ClaimUpgradeNoEnter.yml` | No     | Manages upgrades for claims with restricted entry.                     |
| `ICON_SELECTOR`          | `IconSelector.yml`        | Yes    | Allows selection of a claim icon (dynamically populates icons).        |
| `NO_MOB_SPAWNS_TYPE`     | `NoMobSpawnsType.yml`     | Yes    | Configures mob spawn restrictions for a claim.                         |
| `PLAYER_LIST`            | `PlayerList.yml`          | Yes    | Lists players for trust or permission management.                      |
| `WARP`                   | `WarpList.yml`            | Yes    | Displays a list of claims available for teleportation via `ClaimWarp`. |
| `EXPIRING_CLAIMS`        | `ExpiringClaimList.yml`   | Yes    | Shows claims nearing expiration.                                       |
| `CLAIM_LIST`             | `ClaimList.yml`           | Yes    | Lists all claims owned or accessible by a player.                      |
| `CLAIM_TRUST`            | `TrustList.yml`           | Yes    | Manages trusted players for a claim.                                   |
| `BLOCKS`                 | `ClaimBlock.yml`          | Yes    | Manages claim block purchases or allocations.                          |
| `BLACKLIST`              | `BlackList.yml`           | Yes    | Manages blacklisted players for a claim.                               |
| `WHITELIST`              | `Whitelist.yml`           | Yes    | Manages whitelisted players for a claim.                               |
| `CLAIM_INVITES`          | `ClaimInvites.yml`        | Yes    | Manages claim invitations.                                             |
| `CLAIM_UPGRADE`          | `ClaimUpgrade.yml`        | Yes    | Handles claim upgrades (e.g., biome changes).                          |
| `CLAIM_BLOCKS_SELECTOR`  | `ClaimBlockSelector.yml`  | Yes    | Allows selection of claim block options.                               |
