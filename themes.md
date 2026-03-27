---
icon: transporter
---

# Themes

Themes provide decorative backgrounds for GUIs — filling border slots with glass panes, plants, or other items. They are loaded first, and GUI items override them on overlapping slots.

---

## How Themes Work

1. **File naming**: Theme files are named `<theme_name>_EN.yml` and placed in the theme folder (e.g., `default_EN.yml`).
2. **Assignment**: Each GUI file specifies its theme in the `data` section:
   ```yaml
   data:
     theme: default
   ```
3. **Loading order**: Theme items load **first** with a high priority number (`5`). GUI items load **after** with lower priority numbers (`1`, `2`), overriding theme items on the same slot.
4. **Bedrock support**: Theme items default to `bedrock_supported: false`, meaning they won't render for Bedrock players unless explicitly set.

---

## Default Themes

### `default`

Dark border using black stained glass panes.

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

### `nature`

A natural outdoor aesthetic with glass panes, grass, and plants.

```yaml
items:
  blue_glass_pane:
    material: LIGHT_BLUE_STAINED_GLASS_PANE
    priority: 5
    display_name: " &r "
    slots: [5, 6, 7, 26, 27, 35, 36, 44]
  white_glass_pane:
    material: WHITE_STAINED_GLASS_PANE
    priority: 5
    display_name: " &r "
    slots: [1, 3, 4, 17, 18]
  white_glass:
    material: WHITE_STAINED_GLASS
    priority: 5
    display_name: " &r "
    slots: [2, 9]
  tall_grass:
    material: TALL_GRASS
    priority: 5
    display_name: " &r "
    slots: [47, 48, 51, 52]
  rose:
    material: ROSE_BUSH
    priority: 5
    display_name: " &r "
    slots: [46]
  dark_oak:
    material: DARK_OAK_SAPLING
    priority: 5
    display_name: " &r "
    slots: [50]
```

### `clean`

Minimalistic — fills border slots with `AIR` for a transparent background (6-row GUIs).

```yaml
items:
  SKIP:
    material: AIR
    priority: 5
    slots: [0,1,2,3,4,5,6,7,8,9,17,18,26,27,35,36,44,45,46,47,48,49,50,51,52,53]
    display_name: ' &r  '
```

### `clean_4`

Same as `clean` but designed for 4-row GUIs (e.g., `ClaimUpgradeNoEnter`).

```yaml
items:
  SKIP:
    material: AIR
    priority: 5
    slots: [0,1,2,3,4,5,6,7,8,9,17,18,19,20,21,22,23,24,25,26]
    display_name: ' &r  '
```

---

## Creating a Custom Theme

1. Create a new file in the theme folder, e.g., `my_theme_EN.yml`.
2. Define items under the `items` section with `priority: 5`:
   ```yaml
   items:
     border:
       material: BLUE_STAINED_GLASS_PANE
       priority: 5
       display_name: " "
       slots: [0, 1, 2, 3, 4, 5, 6, 7, 8, 45, 46, 47, 48, 49, 50, 51, 52, 53]
     side_accent:
       material: CYAN_STAINED_GLASS_PANE
       priority: 5
       display_name: " "
       slots: [9, 17, 18, 26, 27, 35, 36, 44]
   ```
3. Reference it in any GUI file's `data` section:
   ```yaml
   data:
     theme: my_theme
   ```

> **Tip:** GUI items with a lower priority number (e.g., `1` or `2`) will automatically override theme items (priority `5`) in the same slot. This is how buttons like "Go Back" replace the theme's border decoration.
