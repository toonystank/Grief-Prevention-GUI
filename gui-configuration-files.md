---
icon: wrench
---

# GUI Configuration Files

Each GUI is defined in a YAML file with two main sections: **`data`** (overall properties) and **`items`** (interactive elements). This page is the complete reference for every configuration option.

---

## `data` Section

The `data` section defines the overall properties of the GUI.

```yaml
data:
  menu_title: '%griefprevgui_title% &7(&2/claim&7)'
  version: '1.2'
  args:
    - claimid
  rows: 6
  gui_type: CLAIM_INFO
  theme: default
```

| Field | Editable | Description |
|---|---|---|
| `menu_title` | ✅ | Title displayed at the top of the GUI inventory. Supports color codes (`&7`), placeholders (`%griefprevgui_title%`), and argument replacements (`{claimid}`). |
| `args` | ✅ | A list of argument names the GUI expects. Values are passed at runtime from the command that opens the GUI. See [GUI Arguments](#gui-arguments-system) below. |
| `rows` | ✅ | Number of inventory rows (1–6). A 6-row GUI has 54 slots (0–53). |
| `theme` | ✅ | Name of the theme to apply (e.g., `default`, `clean`, `nature`, `clean_4`). Loads `<theme_name>_EN.yml` from the theme folder. |
| `version` | ❌ | Internal version tracking. **Do not edit** — may break auto-updates. |
| `gui_type` | ❌ | Internal GUI type identifier. For custom GUIs this must match the name in `config.yml`'s `custom_guis` list. **Do not edit** for default GUIs. |

---

## `items` Section

The `items` section defines every button, icon, and decoration in the GUI. Each item is a named sub-section under `items`.

### Item Properties Reference

```yaml
items:
  teleport:
    material: ENDER_PEARL
    display_name: '&7Teleport &7(&aView&7)'
    lore:
      - ''
      - '&2Description'
      - '   &7Teleport to this claim'
      - ''
      - '    &8• &7Location: &f%griefprevgui_getbyid_location_{claimid}%'
      - ''
      - '&a&l| &2Left Click to Teleport'
      - '&a&l| &2Right Click to Change location'
    slot: 31
    amount: 1
    glow: true
    model_data: 0
    priority: 1
    bedrock_supported: true
    left_click_commands:
      - '[player] claim tp {claimid}'
      - '[sound] UI_BUTTON_CLICK'
    right_click_commands:
      - '[player] claim tp {claimid} set'
      - '[sound] UI_BUTTON_CLICK'
      - '[close]'
      - '[player] claiminfo {claimid}<delay=20>'
```

| Property | Type | Default | Description |
|---|---|---|---|
| `material` | String | `STONE` | The Minecraft item material. Also supports [special material types](#special-material-types). Can contain argument placeholders (e.g., `{material_arg}`). |
| `display_name` | String | — | Item name in the GUI. Supports `&` color codes, PlaceholderAPI placeholders, and `{arg}` replacements. |
| `lore` | List | `[]` | Hover text lines. Same formatting support as `display_name`. |
| `slot` | String/Int | — | Where to place the item. Accepts a single integer (`10`), or a range (`10-15` which expands to slots 10, 11, 12, 13, 14, 15). |
| `slots` | List | `[]` | Alternative to `slot` — a list of slot integers (e.g., `[10, 11, 12]`). |
| `amount` | Int | `1` | Item stack size. |
| `glow` | Boolean | `false` | If `true`, the item has an enchantment glow effect. |
| `model_data` | Int | `0` | Custom model data for resource pack textures. |
| `priority` | Int | auto | Determines which item shows when multiple items target the same slot. **Lower number = higher priority**. Theme items default to `5`; GUI items that don't specify a priority get the lowest available number starting from `1`. |
| `bedrock_supported` | Boolean | `true` | Whether this item renders for Bedrock players (via Geyser). Theme items default to `false`. |

---

## Click Commands

Commands are executed when a player clicks an item. There are three ways to define them:

| Field | When it runs |
|---|---|
| `left_click_commands` | Left-click only |
| `right_click_commands` | Right-click only |
| `click_commands` | **Both** left and right click (shorthand — if present, it is used for both) |

Each entry in the list must start with a **command type prefix**.

### Command Type Prefixes

| Prefix | Description | Example |
|---|---|---|
| `[player]` | Runs the command **as the player** | `[player] claim tp {claimid}` |
| `[console]` | Runs the command **as the console** | `[console] eco give %player_name% 100` |
| `[sound]` | Plays a Minecraft sound effect | `[sound] UI_BUTTON_CLICK` |
| `[close]` | Closes the GUI | `[close]` |
| `[reopen]` | Reopens/refreshes the current GUI | `[reopen]` |
| `[message]` | Sends a formatted chat message to the player | `[message] &aYou clicked this item!` |

### Command Modifiers

You can append inline modifiers to any command line:

| Modifier | Description | Example |
|---|---|---|
| `<delay=N>` | Delays execution by `N` ticks (20 ticks = 1 second) | `[player] claiminfo {id}<delay=20>` |
| `<pitch=N>` | Sets the pitch of a `[sound]` command | `[sound] ENTITY_EXPERIENCE_ORB_PICKUP<pitch=2>` |

### Anvil Input Placeholders

These special placeholders open an anvil GUI for the player to type input before the command executes:

| Placeholder | Description | Example |
|---|---|---|
| `<anvilreply>` | Opens an anvil for free-text input. The typed text replaces this placeholder. | `[player] gpguiflags set {id} ClaimIcon <anvilreply>` |
| `<anvilplayer>` | Opens an anvil for player name input. | `[player] trust {claimid} <anvilplayer>` |

### Full Click Command Example

```yaml
teleport:
  left_click_commands:
    - '[sound] UI_BUTTON_CLICK'
    - '[player] claim tp {claimid}'
  right_click_commands:
    - '[sound] UI_BUTTON_CLICK'
    - '[player] claim tp {claimid} set'
    - '[close]'
    - '[player] claiminfo {claimid}<delay=20>'
```

In this example:
- **Left-click** plays a sound, then teleports the player to the claim.
- **Right-click** plays a sound, sets the teleport location, closes the GUI, then re-opens the claim info after a 1-second delay.

---

## GUI Arguments System

GUI arguments allow you to pass dynamic values into a GUI and use them throughout all text fields.

### How It Works

1. **Declare** arguments in the `data` section:
   ```yaml
   data:
     args:
       - claimid
       - itemname
   ```

2. **Pass** values when the GUI opens. The plugin maps values by **position** in the args list:
   - Argument 0 → `claimid`
   - Argument 1 → `itemname`

   For example, the command `/claiminfo 123` passes `123` as argument 0 (`claimid`).

3. **Use** `{argName}` anywhere in text fields — `display_name`, `lore`, commands, even `material`:
   ```yaml
   display_name: '&7Claim &a{claimid}'
   lore:
     - '&8• &7ID: &f{claimid}'
   click_commands:
     - '[player] claim tp {claimid}'
   ```

4. At render time, `{claimid}` is replaced with the actual value (e.g., `123`).

> **Tip:** Arguments can also be used inside `material` fields. For example, if `args: [material_type]`, you can write `material: '{material_type}'` and it will resolve to whatever value was passed.

---

## View Requirements (Conditional Visibility)

Items can be conditionally shown or hidden based on requirements. This is powerful for showing different items to different players (e.g., owners vs. trusted players).

### Structure

```yaml
view_requirement:
  requirements:
    my_requirement_name:
      type: string equals
      input: '%griefprevgui_isenabled_teleport%'
      output: 'true'
```

Multiple requirements under the same item act as **AND** conditions — all must pass for the item to show.

### Requirement Types

| Type | Description |
|---|---|
| `string equals` | `input` must exactly match `output` |
| `string contains` | `input` must contain `output` as a substring |
| `string equals ignorecase` | Case-insensitive version of `string equals` |
| `has permission` | Player must have the specified permission node |
| `has money` | Player must have at least the specified amount of money (economy) |

### Inverting Requirements

Prefix any type with `!` to **invert** the check:

```yaml
view_requirement:
  requirements:
    not_a_subdiv:
      type: '!string equals'
      input: '%griefprevgui_getbyid_issubdiv_{claimid}%'
      output: 'true'
```

This item will only show if the claim is **not** a subdivision.

### Priority + Requirements: Conditional Item Swapping

When multiple items target the **same slot** with different priorities and requirements, the system picks the first item (lowest priority number) whose requirements pass.

**Example:** Show "Delete Claim" to owners, but "Leave Claim" to everyone else, both on slot 53:

```yaml
claim_delete:
  material: RED_CONCRETE
  priority: 1
  slot: 53
  display_name: '&7Claim Delete'
  view_requirement:
    requirements:
      is_owner:
        type: string equals ignorecase
        input: '%griefprevgui_getbyid_owner_{claimid}%'
        output: '%player_name%'
  click_commands:
    - '[player] unclaim {claimid}'

claim_leave:
  material: RED_CONCRETE
  priority: 2
  slot: 53
  display_name: '&7Leave Claim'
  click_commands:
    - '[player] leaveclaim {claimid}'
```

- Priority `1` item (`claim_delete`) is checked first — if the player is the owner, it shows.
- If not, priority `2` item (`claim_leave`) shows instead.

---

## Navigation Controls (Pagination)

Multi-page GUIs automatically support pagination. Items with the section names **`Previous`** and **`Next`** are automatically recognized as navigation controls — no extra configuration needed.

```yaml
Previous:
  material: ARROW
  display_name: '&cPrevious Page &7[&a<page>&7/&2<max_page>&7]'
  lore:
    - '&7Go to the previous page'
  slot: 47

Next:
  material: ARROW
  display_name: '&aNext Page &7[&a<page>&7/&2<max_page>&7]'
  lore:
    - '&7Go to the next page'
  slot: 51
```

### Pagination Placeholders

| Placeholder | Description |
|---|---|
| `<page>` | Current page number |
| `<max_page>` | Total number of pages |

---

## Special Material Types

Beyond standard Minecraft material names, the `material` field supports two special prefixes:

| Prefix | Description | Example |
|---|---|---|
| `basehead-` | Custom skull using a Base64 texture string | `basehead-eyJ0ZXh0dXJlcyI6ey...` |
| `playerhead-` | Player head skull. Supports placeholders. | `playerhead-%player_name%` |

---

## Dynamic Placeholders

In addition to `{arg}` replacements and PlaceholderAPI, these built-in placeholders are available in specific contexts:

| Placeholder | Context | Description |
|---|---|---|
| `<page>` | Navigation items | Current page number |
| `<max_page>` | Navigation items | Total page count |
| `<current_blocks>` | Claim block GUIs | Player's current block count |
| `<claimname>` | Claim-context GUIs | Name of the claim |
| `<id>` | Claim-context GUIs | Claim ID |
| `<description>` | Claim-context GUIs | Claim description (from the ClaimDescription flag). If no description is set, the lore line is hidden. |
| `<expiretime>` | Claim-context GUIs | Expiration countdown |
| `<itemname>` | Icon Selector GUI | Material name of the current item |
| `<itemcategory>` | Icon Selector GUI | Category of the current material |
| `<EorS>` | Mob type GUIs | Entity or spawn reason name |
| `<mode_permission>` | Sort selectors | Current permission filter text |
| `<mode_parameter>` | Sort selectors | Current distance sort text |
| `<mode_flag>` | Sort selectors | Current flag filter name |
| `<mode_category>` | Sort selectors | Current category filter text |
| `<mode_online_status>` | Sort selectors | Current online status filter |
| `<mode_type>` | Sort selectors | Current region type filter |
| `<selected_*>` | Sort selectors | Highlights the currently active sort option with green + underline formatting |

> All standard [PlaceholderAPI](https://github.com/PlaceholderAPI/PlaceholderAPI) placeholders and [GriefPrev-GUI placeholders](placeholders.md) (e.g., `%griefprevgui_getbyid_location_{claimid}%`) also work in any text field.
