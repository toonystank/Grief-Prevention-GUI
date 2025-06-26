---
icon: transporter
---

# Themes

The GriefPrevention GUI Addon supports customizable themes to enhance the visual appearance of GUIs. Themes are defined in individual YAML files located in the theme folder, with names matching the theme specified in the GUI’s `data` section, appended with `_EN.yml` (e.g., `default` uses `default_EN.yml`). Themes are loaded first during GUI initialization, with items set to a high priority (e.g., `5`), allowing GUI items with lower priority to override them.

### Theme Configuration

* **File Naming**: Theme files must be named `<theme_name>_EN.yml` (e.g., `default_EN.yml`, `nature_EN.yml`) and placed in the theme folder.
* **Structure**: Each theme file contains an `items` section defining decorative items (e.g., glass panes, grass) that fill specific slots in the GUI.
* **Priority**: Theme items are assigned a high priority (e.g., `5`) so that GUI items with lower priority (e.g., `1`, `2`) can replace them in overlapping slots.
* **Application**: The theme is specified in the GUI’s `data` section via the `theme` field (e.g., `theme: clean_4` for `ClaimUpgradeNoEnter_EN.yml`).
* **Custom Themes**: Admins can create custom themes by adding new `<theme_name>_EN.yml` files and specifying the theme name in the GUI’s `data` section.

### Default Themes

The GriefPrevention GUI Addon includes the following default themes:

1. **default** (`default_EN.yml`):
   * Uses black stained glass panes to create a dark border around the GUI.
   *   Configuration:

       ```yaml
       items:
         BACKGROUND_2:
           priority: 5
           material: BLACK_STAINED_GLASS_PANE
           slots:
             - 0
             - 1
             - 2
             - 3
             - 4
             - 5
             - 6
             - 7
             - 8
             - 9
             - 17
             - 18
             - 26
             - 27
             - 35
             - 36
             - 44
             - 45
             - 46
             - 47
             - 48
             - 49
             - 50
             - 51
             - 52
             - 53
           display_name: " "
       ```
2. **nature** (`nature_EN.yml`):
   * Uses a mix of glass panes, grass, and plants for a natural, outdoor aesthetic.
   *   Configuration:

       ```yaml
       items:
         blue_glass_pane:
           material: LIGHT_BLUE_STAINED_GLASS_PANE
           priority: 5
           display_name: " &r "
           slots:
             - 5
             - 6
             - 7
             - 26
             - 27
             - 35
             - 36
             - 44
         white_glass_pane:
           material: WHITE_STAINED_GLASS_PANE
           priority: 5
           display_name: " &r "
           slots:
             - 1
             - 3
             - 4
             - 17
             - 18
         white_glass:
           material: WHITE_STAINED_GLASS
           priority: 5
           display_name: " &r "
           slots:
             - 2
             - 9
         tall_grass:
           material: TALL_GRASS
           priority: 5
           display_name: " &r "
           slots:
             - 47
             - 48
             - 51
             - 52
         rose:
           material: ROSE_BUSH
           priority: 5
           display_name: " &r "
           slots:
             - 46
         dark_oak:
           material: DARK_OAK_SAPLING
           priority: 5
           display_name: " &r "
           slots:
             - 50
       ```
3. **clean** (`clean_EN.yml`):
   * Uses air (`AIR`) to create a minimalistic, transparent background for standard-sized GUIs.
   *   Configuration:

       ```yaml
       items:
         SKIP:
           material: AIR
           priority: 5
           slots:
             - 0
             - 1
             - 2
             - 3
             - 4
             - 5
             - 6
             - 7
             - 8
             - 9
             - 17
             - 18
             - 26
             - 27
             - 35
             - 36
             - 44
             - 45
             - 46
             - 47
             - 48
             - 49
             - 50
             - 51
             - 52
             - 53
           display_name: ' &r  '
       ```
4. **clean\_4** (`clean_4_EN.yml`):
   * A specialized version of the `clean` theme designed for the smaller `ClaimUpgradeNoEnter` GUI (4 rows), using air (`AIR`) for a transparent background.
   *   Configuration:

       ```yaml
       items:
         SKIP:
           material: AIR
           priority: 5
           slots:
             - 0
             - 1
             - 2
             - 3
             - 4
             - 5
             - 6
             - 7
             - 8
             - 9
             - 17
             - 18
             - 19
             - 20
             - 21
             - 22
             - 23
             - 24
             - 25
             - 26
           display_name: ' &r  '
       ```

### Theme Loading and Priority

* **Loading Process**: Themes are loaded first when a GUI is initialized, populating the specified slots with theme items (e.g., glass panes, air) at priority `5`.
* **Item Override**: GUI items with a lower priority (e.g., `1` or `2`) override theme items in the same slots. For example, in `ClaimUpgradeBiomeSelector_EN.yml`, the `goback` item (priority `2`, slot `45`) will replace a `default` theme’s `BACKGROUND_2` item (priority `5`, slot `45`).
* **Customization**: Admins can create custom themes by adding new `<theme_name>_EN.yml` files in the theme folder and referencing them in the GUI’s `data` section (e.g., `theme: my_custom_theme`).&#x20;
