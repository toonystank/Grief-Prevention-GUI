---
icon: wrench
---

# GUI Configuration Files

Each GUI, whether default or custom, is defined in a YAML file with two main sections: `data` and `items`. Below is an overview of these sections and their properties.

### data Section

The `data` section defines the overall properties of the GUI, such as its title, size, and theme.

* **Key Fields**:
  * `menu_title`: The title displayed at the top of the GUI, supporting placeholders (e.g., `&7%gpextension_title% (&2/ClaimIcon&7)`).
  * `args`: A list of arguments required by the GUI (e.g., `id`, `itemname` for claim ID or item selection).
  * `rows`: The number of rows in the GUI (e.g., `6` for a 54-slot inventory).
  * `theme`: Specifies the theme to apply (e.g., `default`, `clean_4`). The plugin loads `<theme_name>_EN.yml` from the theme folder (e.g., `clean_4_EN.yml`).
  * `version`: A developer-only field specifying the configuration version (e.g., `1.0`). Do not edit, as it may break the plugin.
  * `gui_type`: A developer-only field indicating the type of GUI (e.g., `ICON_SELECTOR`). For custom GUIs, it must match the name in `gui.custom_guis`. Do not edit for default GUIs.
*   **Example** (from `ClaimUpgradeNoEnter_EN.yml`):

    ```yaml
    data:
      menu_title: "%griefprevgui_title% &7(&2No Enter&7)"
      version: "1.1"
      args:
        - claimid
      rows: 4
      theme: clean_4
      gui_type: CLAIM_UPGRADE_NO_ENTER
    ```
* **Notes**:
  * Admins should only modify `menu_title`, `args`, `rows`, and `theme` as needed.
  * For custom GUIs, ensure `gui_type` matches the `custom_guis` entry in `config.yml`.
  * Editing `version` or `gui_type` for default GUIs can cause compatibility issues.

### items Section

The `items` section defines the interactive elements (buttons, icons, etc.) displayed in the GUI, structured similarly to `FlagOptions.yml`. Each item is configured under a unique section name (e.g., `teleport`, `plains`) and supports properties to control its appearance and behavior. Multi-page GUIs include `Previous` and `Next` sections for navigation.

* **Key Fields**:
  * `material`: The Minecraft item representing the element (e.g., `ENDER_PEARL`, `GRASS_BLOCK`).
  * `display_name`: The name shown in the GUI, supporting color codes and placeholders (e.g., `&7Plains`).
  * `lore`: A list of text lines displayed when hovering, often including descriptions and placeholders (e.g., `&8• &7Current: &f%gpextension_getbyid_flags_parma_ChangeBiome_{claimid}%`).
  * `slot`: The specific slot where the item appears, as a single integer (e.g., `10`, `31`).
  * `slots`: A list of slots where the item appears (e.g., `[10, 11, 12]`), used instead of `slot`.
  * `amount`: The stack size of the item (defaults to `1` if not specified or invalid).
  * `glow`: If `true`, the item appears enchanted (e.g., `true` for `add`).
  * `model_data`: Custom model data for resource pack textures (optional, e.g., `0`).
  * `left_click_commands`: Commands executed on left-click (e.g., `[player] claim tp {claimid}`).
  * `right_click_commands`: Commands executed on right-click (e.g., `[player] gpguiflags set {claimid} ChangeBiome PLAINS`).
  * `click_commands`: Commands executed for both left and right clicks (used instead of separate left/right commands).
  * `priority`: Determines the rendering order of items (e.g., `1` for `disabled`). Items with lower priority override theme items (priority `5`).
  * `view_requirement`: Conditions for item visibility (e.g., checking if a feature is enabled or if the player has permissions).
* **Navigation Controls**:
  * Multi-page GUIs include `Previous` and `Next` sections to navigate between pages, typically placed in slots `47` and `51`, respectively.
  *   Example configuration:

      ```yaml
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
      ```
* **Special Sections for Custom GUIs**:
  * Some custom GUIs (e.g., `ICON_SELECTOR`, `NO_MOB_SPAWNS_TYPE`) require a specific section in `items` matching their `gui_type` (e.g., `ICON_SELECTOR` for dynamic icon population).
  * User-defined custom GUIs (e.g., `ClaimUpgradeBiomeSelector`) typically use predefined items and may not require a dynamic section.
*   **Example Configurations**:

    **IconSelector.yml** (Default Custom GUI with dynamic content and navigation):

    ```yaml
    data:
      menu_title: "&7%gpextension_title% (&2/ClaimIcon&7)"
      args:
        - id
        - itemname
      version: "1.0"
      rows: 6
      theme: default
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
          - "    &8• &7Status: &f%griefprevgui_getbyid_flags_isactive_ClaimIcon_{id}%"
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
      theme: default
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
          - "    &8• &7Current: &f%griefprevgui_getbyid_flags_parma_ChangeBiome_{claimid}%"
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
          - "    &8• &7Current: &f%griefprevgui_getbyid_flags_parma_ChangeBiome_{claimid}%"
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
          - "    &8• &7Current: &f%griefprevgui_getbyid_flags_parma_ChangeBiome_{claimid}%"
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
  * Navigation controls (`Previous` and `Next`) are defined as specific sections in multi-page GUIs, typically in slots `47` and `51`.
  * Commands use placeholders (e.g., `{claimid}`, `<anvilreply>`) and special actions (e.g., `[close]`, `[sound]`).
  * Theme items (priority `5`) are overridden by GUI items with lower priority (e.g., `1`, `2`).&#x20;
