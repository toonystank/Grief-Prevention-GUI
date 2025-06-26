# GUI System

## Overview

The **GriefPrevention GUI Addon** provides a graphical user interface for managing claims, flags, and related features of the **GriefPrevention** plugin. Each GUI is defined in a separate YAML configuration file, allowing server admins to customize its appearance and functionality. Admins can also define custom GUIs in `config.yml`. This wiki details the structure of the GUI system, the available GUIs, their configuration, and general GUI settings.

***

## GUI System

The GUI system enables claim owners and trusted players to interact with claim settings through intuitive menus. GUIs are defined in individual YAML files, each containing a `data` section for overall properties and an <mark style="color:yellow;">`items`</mark> section for interactive elements, similar to the structure of `FlagOptions.yml`. The system supports dynamic content via placeholders and special sections for custom GUIs.

### Key Features

* **Customizable GUIs**: Each GUI is defined in its own file, with additional custom GUIs configurable in `config.yml`.
* **Dynamic Content**: GUIs use placeholders (e.g., `%gpextension_getbyid_location_{claimid}%`, `<itemname>`) to display claim-specific or context-sensitive information.
* **Interactive Elements**: Items can trigger commands on left or right clicks, such as teleporting, setting flags, or opening other menus.
* **Conditional Display**: Items can have `view_requirement` conditions to control visibility based on permissions or settings.
* **Navigation Controls**: Multi-page GUIs include `Next` and `Previous` items for easy navigation.
* **Custom GUIs**: Certain GUIs (e.g., `ICON_SELECTOR`) dynamically populate content and require specific sections in their configuration. User-defined custom GUIs can be added in `config.yml`.

***

## Available GUIs

The **GriefPrevention GUI Addon** includes the following default GUIs, each serving a specific purpose. GUIs marked as _Custom_ dynamically populate content and require a specific section in their `items` configuration (e.g., `ICON_SELECTOR` for the Icon Selector GUI).

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

***

## Custom User-Defined GUIs

Admins can define custom GUIs in `config.yml` under `gui.custom_guis`. These GUIs are loaded by the plugin and must follow specific naming and configuration rules.

* **Definition**: List custom GUIs in `config.yml` under `gui.custom_guis` (e.g., `ClaimUpgradeBiomeSelector`).
* **File Naming**: The plugin loads the corresponding YAML file with `_EN` appended to the name (e.g., `ClaimUpgradeBiomeSelector` loads `ClaimUpgradeBiomeSelector_EN.yml`).
* **GUI Type**: The `gui_type` in the GUI file’s `data` section must exactly match the name listed in `custom_guis` (e.g., `ClaimUpgradeBiomeSelector`).
* **File Location**: Custom GUI files must be placed in the GUI folder alongside default GUI files.

**Example**:

*   In `config.yml`:

    ```yaml
    gui:
      custom_guis:
        - ClaimUpgradeBiomeSelector
    ```
* The plugin loads `ClaimUpgradeBiomeSelector_EN.yml`, and its `data` section must include `gui_type: ClaimUpgradeBiomeSelector`.

***

## GUI Configuration Files

Each GUI, whether default or custom, is defined in a YAML file with two main sections: `data` and `items`. Below is an overview of these sections and their properties.

### data Section

The `data` section defines the overall properties of the GUI, such as its title and size.

* **Key Fields**:
  * `menu_title`: The title displayed at the top of the GUI, supporting placeholders (e.g., `&7%gpextension_title% (&2/ClaimIcon&7)`).
  * `args`: A list of arguments required by the GUI (e.g., `id`, `itemname` for claim ID or item selection).
  * `rows`: The number of rows in the GUI (e.g., `6` for a 54-slot inventory).
  * `version`: A developer-only field specifying the configuration version (e.g., `1.0`). **Do not edit**, as it may break the plugin.
  * `gui_type`: A developer-only field indicating the type of GUI (e.g., `ICON_SELECTOR`). For custom GUIs, it must match the name in `gui.custom_guis`. **Do not edit** for default GUIs.
* **Notes**:
  * Admins should only modify `menu_title`, `args`, and `rows` as needed.
  * For custom GUIs, ensure `gui_type` matches the `custom_guis` entry in `config.yml`.
  * Editing `version` or `gui_type` for default GUIs can cause compatibility issues.

### items Section

The `items` section defines the interactive elements (buttons, icons, etc.) displayed in the GUI, structured similarly to `FlagOptions.yml`. Each item is configured under a unique section name (e.g., `teleport`, `plains`) and supports properties to control its appearance and behavior.

* **Key Fields**:
  * `material`: The Minecraft item representing the element (e.g., `ENDER_PEARL`, `GRASS_BLOCK`).
  * `display_name`: The name shown in the GUI, supporting color codes and placeholders (e.g., `&7Plains`).
  * `lore`: A list of text lines displayed when hovering, often including descriptions and placeholders (e.g., `&8• &7Current: &f%gpextension_getbyid_flags_parma_ChangeBiome_{claimid}%`).
  * `slot`: The specific slot where the item appears (e.g., `10`, `31`). Can also be a range (e.g., `10-15`) or a list via `slots`.
  * `slots`: A list of slots where the item appears (alternative to `slot`).
  * `amount`: The stack size of the item (defaults to `1` if not specified or invalid).
  * `glow`: If `true`, the item appears enchanted (e.g., `true` for `add`).
  * `model_data`: Custom model data for resource pack textures (optional, e.g., `0`).
  * `left_click_commands`: Commands executed on left-click (e.g., `[player] claim tp {claimid}`).
  * `right_click_commands`: Commands executed on right-click (e.g., `[player] gpguiflags set {claimid} ChangeBiome PLAINS`).
  * `click_commands`: Commands executed for both left and right clicks (used instead of separate left/right commands).
  * `priority`: Determines the rendering order of items (e.g., `1` for `disabled`).
  * `view_requirement`: Conditions for item visibility (e.g., checking if a feature is enabled or if the player has permissions).
  * `isMenuControl`: If `true`, the item is a navigation control (e.g., `Next`, `Previous`).
  * `isTheme`: Indicates if the item is part of a theme (used internally).
  * `sortData`: Configures sorting behavior (managed by the plugin).
* **Special Sections for Custom GUIs**:
  * Some custom GUIs (e.g., `ICON_SELECTOR`, `NO_MOB_SPAWNS_TYPE`) require a specific section in `items` matching their `gui_type` (e.g., `ICON_SELECTOR` for dynamic icon population).
  * User-defined custom GUIs (e.g., `ClaimUpgradeBiomeSelector`) typically use predefined items and may not require a dynamic section.
*   **Example Configurations**:

    **IconSelector.yml** (Default Custom GUI with dynamic content):

    ```yaml
    data:
      menu_title: "&7%gpextension_title% (&2/ClaimIcon&7)"
      args:
        - id
        - itemname
      version: "1.0"
      rows: 6
      gui_type: ICON_SELECTOR
    items:
      mode_selector_category:
        material: CREEPER_BANNER_PATTERN
        model_data: 0
        slot: 0
        display_name: "&7Item Category &7(&a<mode_category>&7)"
        lore:
          - ""
          - "&2Description:"
          - "   &7Change the sorting of materials"
          - ""
          - "   &7Current: &a<mode_category>"
          - ""
          - "&7Categories:"
          - ""
          - "   &8• &7<selected_block>"
          - "   &8• &7<selected_edible>"
          - "   &8• &7<selected_record>"
          - "   &8• &7<selected_allmaterial>"
          - ""
          - "&7Click to change the Item Category."
      add:
        material: PAPER
        glow: true
        model_data: 0
        priority: 1
        display_name: "&7Change by name"
        lore:
          - ""
          - "&2Description"
          - ""
          - "    &8• &7Status: &f%gpextension_getbyid_flags_isactive_ClaimIcon_{id}%"
          - ""
        slot: 8
        click_commands:
          - "[sound] UI_BUTTON_CLICK"
          - "[player] gpguiflags set {id} ClaimIcon <anvilreply>"
      goback:
        material: OAK_DOOR
        model_data: 0
        display_name: "&7⟰ &aGo Back"
        left_click_commands:
          - "[sound] BLOCK_WOODEN_DOOR_OPEN"
          - "[player] claim"
        slot: 45
      Previous:
        material: ARROW
        model_data: 0
        display_name: "&cPrevious Page &7[&a<page>&7/&2<max_page>&7]"
        lore:
          - "&7Go to the previous page"
        slot: 47
      Next:
        material: ARROW
        model_data: 0
        display_name: "&aNext Page &7[&a<page>&7/&2<max_page>&7]"
        lore:
          - "&7Go to the next page"
        slot: 51
      filler:
        material: LIGHT_BLUE_STAINED_GLASS_PANE
        model_data: 0
        display_name: " &r "
      ICON_SELECTOR:
        display_name: "<itemname>"
        lore:
          - ""
          - "&2Description:"
          - ""
          - "    &8• &7Name: &f<itemname>"
          - "    &8• &7Category: &f<itemcategory>"
          - ""
          - "&a&l| &2Click to select"
        click_commands:
          - "[player] gpguiflags set {id} ClaimIcon {itemname}"
          - "[close]"
          - "[sound] UI_BUTTON_CLICK"
    ```

    **ClaimUpgradeBiomeSelector\_EN.yml** (User-Defined Custom GUI with predefined items):

    ```yaml
    data:
      menu_title: "%gpextension_title% &7(&2Biome Selector&7)"
      version: "1.0"
      args:
        - claimid
      rows: 6
      gui_type: ClaimUpgradeBiomeSelector
    items:
      goback:
        material: OAK_DOOR
        priority: 2
        display_name: "&7⟰ &aGo Back"
        click_commands:
          - "[sound] BLOCK_WOODEN_DOOR_OPEN"
          - "[player] claim"
        slot: 45
      disabled:
        material: BARRIER
        priority: 1
        display_name: "&cReset Biome"
        lore:
          - ""
          - "    &8• &7Current: &f%gpextension_getbyid_flags_parma_ChangeBiome_{claimid}%"
          - "&a&l| &2Click to reset biome to default."
        slot: 53
        click_commands:
          - "[player] gpguiflags unset {claimid} ChangeBiome true"
      plains:
        material: GRASS_BLOCK
        priority: 2
        display_name: "&7Plains"
        lore:
          - ""
          - "&2Biome Description:"
          - "   &7A peaceful grassy landscape filled with flowers and animals."
          - ""
          - "    &8• &7Current: &f%gpextension_getbyid_flags_parma_ChangeBiome_{claimid}%"
          - ""
          - "&a&l| &2Click to set this biome."
        click_commands:
          - "[player] gpguiflags set {claimid} ChangeBiome PLAINS"
          - "[sound] UI_BUTTON_CLICK"
        slot: 10
      forest:
        material: OAK_LOG
        priority: 2
        display_name: "&7Forest"
        lore:
          - ""
          - "&2Biome Description:"
          - "   &7A dense forest with tall oak and birch trees."
          - ""
          - "    &8• &7Current: &f%gpextension_getbyid_flags_parma_ChangeBiome_{claimid}%"
          - ""
          - "&a&l| &2Click to set this biome."
        click_commands:
          - "[player] gpguiflags set {claimid} ChangeBiome FOREST"
          - "[sound] UI_BUTTON_CLICK"
        slot: 11
      # Additional biome items omitted for brevity, following the same structure
    ```
* **Notes**:
  * The `ICON_SELECTOR` section in `IconSelector.yml` is required for dynamic icon population.
  * `ClaimUpgradeBiomeSelector_EN.yml` uses predefined items for biomes and does not require a dynamic section.
  * Items like `Previous` and `Next` are navigation controls (`isMenuControl: true`) for multi-page GUIs.
  * Commands use placeholders (e.g., `{claimid}`, `<anvilreply>`) and special actions (e.g., `[close]`, `[sound]`).

***

## GUI Settings in config.yml

The `gui` section in `config.yml` configures general GUI behavior and allows defining custom GUIs.

* **Key Settings**:
  * `theme`: Sets the default theme for GUIs (`default`, `clean`, `nature`). Individual GUI files can override this (e.g., `ClaimUpgradeNoEnter_EN.yml`).
  * `remove_claim_from_warp_list_on_no_enter.enable`: If `true`, claims with the `NoEnter` flag are excluded from the warp list (default: `true`).
  * `disable_gui_on_grief_prevention_disabled_worlds`: If `true`, GUIs are disabled in worlds where GriefPrevention is disabled (default: `false`).
  * `claim_list_size_limit`: Limits the number of claims shown in `CLAIM_LIST` (default: `enable: false`, `size: 45`).
  * `player_list_size_limit`: Limits the number of players shown in `PLAYER_LIST` (default: `enable: true`, `size: 100`).
  * `default_claim_list_icon.material`: Sets the default icon for claims in `CLAIM_LIST` (default: `GRASS_BLOCK`).
  * `default_claim_list_icon.model_data`: Custom model data for the default icon (default: `0`).
  * `default_sort`: Configures default sorting for `CLAIM_LIST` (default: `permission: ALL`, `online_status: Online`, `distance: Nearest`).
  * `fancy_icons_in_claim_list_by_default.enable`: If `true`, `CLAIM_LIST` icons use the claim’s center block once cached (default: `true`).
  * `disabled_guis`: Lists GUIs to disable (e.g., `["Claim_List"]`). Bypassed with `gpgui.bypass.guidisabled` permission (default: `[]`).
  * `custom_guis`: Lists custom GUI names (e.g., `["ClaimUpgradeBiomeSelector"]`). The plugin loads corresponding files with `_EN` appended (e.g., `ClaimUpgradeBiomeSelector_EN.yml`).
*   **Example Configuration**:

    ```yaml
    gui:
      theme: "default"
      remove_claim_from_warp_list_on_no_enter:
        enable: true
      disable_gui_on_grief_prevention_disabled_worlds: false
      claim_list_size_limit:
        enable: false
        size: 45
      player_list_size_limit:
        enable: true
        size: 100
      default_claim_list_icon:
        material: "GRASS_BLOCK"
        model_data: 0
      default_sort:
        permission: ALL
        online_status: Online
        distance: Nearest
      fancy_icons_in_claim_list_by_default:
        enable: true
      disabled_guis: []
      custom_guis:
        - ClaimUpgradeBiomeSelector
    ```
* **Notes**:
  * Custom GUIs listed in `custom_guis` must have corresponding YAML files ending in `_EN` in the GUI folder.
  * The `gui_type` in the custom GUI file must match the name in `custom_guis` exactly.
  * The `theme` setting enhances visual customization, with options like `default`, `clean`, and `nature`.

***

## Usage Notes

* **Accessing GUIs**: GUIs are accessed via commands (e.g., `/claim menu` for `MAIN_MENU`) or by interacting with flags (e.g., clicking `ClaimIcon` to open `ICON_SELECTOR` or `ChangeBiome` to open `ClaimUpgradeBiomeSelector`).
* **Custom GUIs**: Default custom GUIs (e.g., `ICON_SELECTOR`) dynamically populate items and require a matching section in `items`. User-defined custom GUIs (e.g., `ClaimUpgradeBiomeSelector`) are added in `config.yml` and loaded from \`\_
