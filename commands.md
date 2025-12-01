---
icon: terminal
---

# Commands

The main command for the plugin is `/claim` (aliases: `/gpclaim`, `/claimui`).

## General Commands

| Command | Alias | Description | Permission |
| :--- | :--- | :--- | :--- |
| `/claim` | `/gpclaim`, `/claimui` | Open the main claim menu. | - |
| `/claim create [radius]` | `/claimcreate`, `/gpclaimcreate` | Create a new claim. | - |
| `/claim list [parentID]` | `/claimlist`, `/claimslist` | Open the claim list menu. | - |
| `/claim info [claimID]` | `/claiminfo` | Open the claim info menu. | - |
| `/claim claimblocks` | `/gpclaimblocks` | Open the claim blocks menu. | - |
| `/claim purchase [amount\|selector]` | `/gpclaimpurchase` | Purchase claim blocks or open selector. | - |
| `/claim sell [amount\|selector]` | `/gpclaimsell` | Sell claim blocks. | - |
| `/claim tp <claimID> [player]` | `/gpclaimtp` | Teleport to a claim. | `gpgui.admin` or `gpgui.bypass.teleport` (if enabled) |
| `/claim warp <claimID>` | `/gpclaimwarp` | Warp to a claim. | - |
| `/claim fly` | `/gpclaimfly`, `/claimfly` | Toggle claim flight. | - |
| `/claim leave <claimID>` | `/gpclaimleave` | Leave a claim. | - |
| `/claim unclaim <claimID>` | `/gpclaimunclaim`, `/gpunclaim` | Unclaim a land. | - |

## Trust & Permissions

| Command | Alias | Description |
| :--- | :--- | :--- |
| `/claim trust <player> [claimID]` | `/gpclaimtrust` | Open trust menu or trust a player. |
| `/claim untrust <player> [claimID]` | `/gpclaimuntrust` | Open untrust menu or untrust a player. |
| `/claim trustlist [claimID]` | `/gpclaimtrustlist` | Open the trust list menu. |
| `/claim trustgui [player] [claimID]` | `/gpclaimtrustgui` | Open the trust GUI. |
| `/claim invites [claimID]` | `/claiminvites`, `/gpclaiminvites` | Manage claim invites. |
| `/claim accept [claimID]` | `/acceptinvite`, `/gpacceptinvite` | Accept a claim invite. |
| `/claim decline [claimID]` | `/declineinvite`, `/gpdeclineinvite` | Decline a claim invite. |
| `/claim removeinvite <player> [claimID]` | `/removeinvite`, `/gpremoveinvite` | Remove a pending invite. |
| `/claim transferclaim <player> [claimID]` | `/transferclaim`, `/giveclaim` | Transfer claim ownership. |
| `/claim trustplayer <set\|unset> <player> <claimID> [perm] [time]` | `/gptrust` | Set trust with optional permission and time (e.g., 10m, 1h). |
| `/claim kickout <player> [claimID]` | `/claimkickout` | Kick a player from the claim. |
| `/claim ban <player> [claimID]` | `/claimban` | Ban a player from the claim. |
| `/claim unban <player> [claimID]` | `/claimunban` | Unban a player from the claim. |
| `/claim whitelist <player> [claimID]` | `/claimwhitelist` | Whitelist a player in the claim. |
| `/claim unwhitelist <player> [claimID]` | `/claimunwhitelist` | Remove player from whitelist. |

## Administration & Management

| Command | Alias | Description | Permission |
| :--- | :--- | :--- | :--- |
| `/claim setblocks <player> <amount> [bonus]` | `/gpclaimsetblocks` | Set a player's accrued claim blocks. | `gpgui.admin` |
| `/claim addblocks <player> <amount> [bonus]` | `/gpclaimaddblocks` | Add to a player's accrued claim blocks. | `gpgui.admin` |
| `/claim transferblock <player> <amount>` | `/transferblocks` | Transfer claim blocks to another player. | `gpgui.command.transferblock` |
| `/claim timedflight <set\|add\|get> <player> [time]` | `/gpclaimtimedflight` | Manage timed flight for a player. | `gpgui.timedflight` |
| `/claim expirecheck <player>` | `/claimexpirecheck` | Check claim expiration for a player. | - |
| `/claim disableFlag <claimID> <flag> <arg>` | `/gpclaimdisableflag` | Disable a specific flag. | `gpgui.admin` |
| `/claim reload` | `/griefprevguireload`, `/gpguireload` | Reload the plugin. | `gpgui.admin` |
| `/claim debug <arg>` | - | Debug commands. | `gpgui.admin` |

## Menus

| Command | Alias | Description |
| :--- | :--- | :--- |
| `/claim menu customGUI <guiName>` | `/gpclaimcustomgui` | Open a custom GUI. |
| `/claim menu leaveclaim` | `/leaveclaim` | Open leave claim menu. |
| `/claim menu icon` | `/claimicon` | Open icon selector. |
| `/claim menu nomobspawnstype` | `/claimnomobspawnstype` | Open no mob spawn type menu. |
| `/claim menu leaveallclaim` | `/leaveallclaim` | Open leave all claims menu. |
| `/claim menu deleteclaim` | `/deleteclaim` | Open delete claim menu. |
| `/claim menu deleteallclaim` | `/deleteallclaim` | Open delete all claims menu. |
| `/claim menu warp` | `/claimwarp` | Open warp menu. |
| `/claim menu blacklist` | `/gpblacklist` | Open blacklist menu. |
| `/claim menu whitelist` | `/gpwhitelist` | Open whitelist menu. |
| `/claim menu trustplayers` | `/gpclaimplayers` | Open trust players menu. |
| `/claim menu settings` | `/gpclaimsettings` | Open claim settings/upgrade menu. |
| `/claim menu settings noenter` | `/gpclaimnoenter` | Open no-enter settings menu. |
