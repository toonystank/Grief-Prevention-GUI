---
icon: screwdriver-wrench
---

# GUI Settings in config.yml

The `gui` section in `config.yml` controls global GUI behavior. These settings apply across all GUIs unless overridden by individual GUI files.

---

## Settings Reference

### Theme

```yaml
gui:
  theme: "default"
```

Sets the default theme for all GUIs. Individual GUI files can override this via the `theme` field in their `data` section.

Available built-in themes: `default`, `nature`, `clean`, `clean_4`.

---

### Bedrock Support

```yaml
gui:
  bedrockGuiSupport:
    enable: true
    color_replace: "&7"
```

| Setting | Default | Description |
|---|---|---|
| `enable` | `true` | Enables automatic Bedrock-compatible GUI rendering for Geyser players. |
| `color_replace` | `&7` | Replaces `&7` / `§7` color codes with this value for Bedrock players (since gray text may be hard to read on Bedrock). |

---

### Warp List Filtering

```yaml
gui:
  remove_claim_from_warp_list_on_no_enter:
    enable: true
```

If `true`, claims with the `NoEnter` flag are excluded from the warp list GUI.

---

### World Restrictions

```yaml
gui:
  disable_gui_on_grief_prevention_disabled_worlds: false
```

If `true`, GUIs are disabled in worlds where GriefPrevention itself is disabled.

---

### Claim List Settings

```yaml
gui:
  claim_list_size_limit:
    enable: false
    size: 45
  default_claim_list_icon:
    material: "GRASS_BLOCK"
    model_data: 0
  fancy_icons_in_claim_list_by_default:
    enable: true
```

| Setting | Default | Description |
|---|---|---|
| `claim_list_size_limit.enable` | `false` | Limits the number of claims shown in `CLAIM_LIST`. |
| `claim_list_size_limit.size` | `45` | Maximum number of claims when the limit is enabled. |
| `default_claim_list_icon.material` | `GRASS_BLOCK` | Default material used for claim icons in the claim list. |
| `default_claim_list_icon.model_data` | `0` | Custom model data for the default claim icon. |
| `fancy_icons_in_claim_list_by_default.enable` | `true` | If enabled, claim list icons use the claim's center block (once cached) instead of the default icon. |

---

### Player List Settings

```yaml
gui:
  player_list_size_limit:
    enable: true
    size: 100
```

| Setting | Default | Description |
|---|---|---|
| `enable` | `true` | Limits the number of players shown in the `PLAYER_LIST` GUI. |
| `size` | `100` | Maximum number of players when the limit is enabled. |

---

### Default Sorting

```yaml
gui:
  default_sort:
    permission: ALL
    region_type: ALL
    online_status: Online
    distance: Nearest
```

| Setting | Default | Options | Description |
|---|---|---|---|
| `permission` | `ALL` | `ALL`, `OWNER`, `PUBLIC`, `SUBDIVISION`, `MANAGER`, `TRUSTED`, `CONTAINER`, `ACCESS_TRUSTED` | Default permission filter for claim/warp lists. |
| `region_type` | `ALL` | `ALL`, `REGION`, `SUB_REGION` | Default region type filter. |
| `online_status` | `Online` | `ALL`, `Online`, `Offline` | Default online status filter for player lists. |
| `distance` | `Nearest` | `Nearest`, `Largest`, `Smallest` | Default distance/size sort for claim lists. |

---

### Disabled GUIs

```yaml
gui:
  disabled_guis: []
```

A list of GUI names to disable (e.g., `["CLAIM_LIST"]`). Players with the `gpgui.bypass.guidisabled` permission can still access disabled GUIs.

---

### Custom GUIs

```yaml
gui:
  custom_guis:
    - ClaimUpgradeBiomeSelector
```

Register custom GUI names here. The plugin loads the corresponding file with `_EN` appended (e.g., `ClaimUpgradeBiomeSelector_EN.yml`). See [Custom User-Defined GUIs](custom-user-defined-guis.md) for details.

---

### Chunk Claiming (Experimental)

```yaml
experimental:
  features:
    chunk_claiming:
      enable: false
      mode: "both"
      radius: 3
      extend_adjacent_claims: true
```

| Setting | Default | Description |
|---|---|---|
| `enable` | `false` | Enables the Chunk Claim GUI system. |
| `mode` | `both` | Claim mode — `both` allows standard and chunk claiming. |
| `radius` | `3` | Number of chunks visible in each direction from the player (grid size = `2 × radius + 1`). |
| `extend_adjacent_claims` | `true` | Allows extending existing claims into adjacent unclaimed chunks via right-click in the Chunk Claim GUI. |

---

## Full Example

```yaml
gui:
  theme: "default"
  bedrockGuiSupport:
    enable: true
    color_replace: "&7"
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
    region_type: ALL
    online_status: Online
    distance: Nearest
  fancy_icons_in_claim_list_by_default:
    enable: true
  disabled_guis: []
  custom_guis:
    - ClaimUpgradeBiomeSelector

experimental:
  features:
    chunk_claiming:
      enable: false
      mode: "both"
      radius: 3
      extend_adjacent_claims: true
```
