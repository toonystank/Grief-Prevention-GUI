---
icon: plus-circle
---

# Custom User-Defined GUIs

Admins can create entirely new GUI menus beyond the built-in ones. Custom GUIs are registered in `config.yml` and defined in their own YAML files.

---

## Step-by-Step Guide

### 1. Register the GUI in `config.yml`

Add your GUI name to the `custom_guis` list:

```yaml
gui:
  custom_guis:
    - ClaimUpgradeBiomeSelector
    - MyCustomMenu
```

### 2. Create the YAML File

Create a file in the GUI folder with the `_EN` suffix:
- GUI name: `MyCustomMenu`
- File name: `MyCustomMenu_EN.yml`

### 3. Set `gui_type` to Match

The `gui_type` in your file's `data` section must **exactly match** the name in `custom_guis`:

```yaml
data:
  menu_title: '%griefprevgui_title% &7(&2My Menu&7)'
  version: '1.0'
  args:
    - claimid
  rows: 6
  theme: default
  gui_type: MyCustomMenu
```

### 4. Define Items

Add items under the `items` section using all the standard properties (see [GUI Configuration Files](gui-configuration-files.md)):

```yaml
items:
  goback:
    material: OAK_DOOR
    priority: 2
    display_name: '&7⟰ &aGo Back'
    click_commands:
      - '[sound] BLOCK_WOODEN_DOOR_OPEN'
      - '[player] claim'
    slot: 45

  option_one:
    material: DIAMOND
    priority: 2
    display_name: '&aOption One'
    lore:
      - ''
      - '&2Click to activate'
    click_commands:
      - '[player] my_custom_command {claimid}'
      - '[sound] UI_BUTTON_CLICK'
    slot: 22

  option_two:
    material: EMERALD
    priority: 2
    display_name: '&aOption Two'
    lore:
      - ''
      - '&2Click to activate'
    click_commands:
      - '[player] another_command {claimid}'
      - '[sound] UI_BUTTON_CLICK'
    slot: 24
```

### 5. Open the GUI

Open your custom GUI from another GUI's click commands or from a plugin command:

```yaml
# From another GUI item's click_commands:
click_commands:
  - '[player] gpopenGUI MyCustomMenu {claimid}'
```

---

## Full Example

**`config.yml`**:
```yaml
gui:
  custom_guis:
    - ClaimUpgradeBiomeSelector
```

**`ClaimUpgradeBiomeSelector_EN.yml`**:
```yaml
data:
  menu_title: '%griefprevgui_title% &7(&2Biome Selector&7)'
  version: '1.0'
  args:
    - claimid
  rows: 6
  theme: default
  gui_type: ClaimUpgradeBiomeSelector

items:
  goback:
    material: OAK_DOOR
    priority: 2
    display_name: '&7⟰ &aGo Back'
    click_commands:
      - '[sound] BLOCK_WOODEN_DOOR_OPEN'
      - '[player] claim'
    slot: 45

  disabled:
    material: BARRIER
    priority: 1
    display_name: '&cReset Biome'
    lore:
      - ''
      - '    &8• &7Current: &f%griefprevgui_getbyid_flags_parma_ChangeBiome_{claimid}%'
      - '&a&l| &2Click to reset biome to default.'
    slot: 53
    click_commands:
      - '[player] gpguiflags unset {claimid} ChangeBiome true'

  plains:
    material: GRASS_BLOCK
    priority: 2
    display_name: '&7Plains'
    lore:
      - ''
      - '&2Biome Description:'
      - '   &7A peaceful grassy landscape.'
      - ''
      - '    &8• &7Current: &f%griefprevgui_getbyid_flags_parma_ChangeBiome_{claimid}%'
      - ''
      - '&a&l| &2Click to set this biome.'
    click_commands:
      - '[player] gpguiflags set {claimid} ChangeBiome PLAINS'
      - '[sound] UI_BUTTON_CLICK'
    slot: 10
```

---

## Key Rules

| Rule | Detail |
|---|---|
| File naming | Must end with `_EN.yml` (e.g., `MyMenu_EN.yml`) |
| `gui_type` | Must exactly match the name in `config.yml`'s `custom_guis` list |
| File location | Must be in the GUI folder alongside default GUI files |
| Theme support | Custom GUIs can use themes just like built-in ones |
| All features | Custom GUIs support all standard features: arguments, view requirements, pagination, click commands, etc. |
