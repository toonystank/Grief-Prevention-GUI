---
icon: list-dropdown
---

# GUI Overview

The **GriefPrevention GUI Addon** provides a comprehensive graphical user interface for managing claims, flags, and related features of the GriefPrevention plugin. Each GUI is defined in a separate YAML configuration file, giving server admins full control over appearance, layout, and functionality.

---

## How the GUI System Works

Every GUI follows the same pattern:

1. **A YAML file** defines the GUI's layout — its title, size, theme, and items.
2. Each **item** in the GUI is a named section with a material, display name, lore, slot, and click commands.
3. When a player opens the GUI, the plugin reads the YAML, applies the theme, evaluates view requirements, resolves placeholders, and renders the inventory.
4. Clicking an item executes its configured commands (as player, console, sound, etc.).

### Architecture at a Glance

```
┌──────────────────────────────────────────────────┐
│                   YAML File                      │
│  ┌─────────┐  ┌──────────────────────────────┐   │
│  │  data    │  │  items                       │   │
│  │  - title │  │  - goback (slot 45)          │   │
│  │  - args  │  │  - teleport (slot 31)        │   │
│  │  - rows  │  │  - Previous (slot 47)        │   │
│  │  - theme │  │  - Next (slot 51)            │   │
│  └─────────┘  └──────────────────────────────┘   │
└──────────────────────────────────────────────────┘
        │                    │
        ▼                    ▼
   Theme items          GUI items
   (priority 5)        (priority 1-2)
        │                    │
        └────────┬───────────┘
                 ▼
        Priority resolution
        (lowest number wins)
                 │
                 ▼
        View requirement checks
        (show/hide per player)
                 │
                 ▼
        Rendered inventory
```

---

## Key Features

* **Fully Customizable** — Every GUI is a YAML file you can edit: titles, items, materials, lore, commands, and slots.
* **Click Commands** — Items execute commands on click with 6 command types: `[player]`, `[console]`, `[sound]`, `[close]`, `[reopen]`, `[message]`. Supports delays, anvil input, and pitched sounds.
* **GUI Arguments** — GUIs accept arguments (e.g., claim ID) that can be used as `{argName}` placeholders throughout all text fields and commands.
* **Conditional Visibility** — `view_requirement` blocks let you show/hide items based on permissions, economy balance, or placeholder values. Combined with the priority system, you can swap items per-player.
* **Themes** — Visual themes (e.g., `default`, `nature`, `clean`) provide decorative backgrounds. Theme items load at a high priority number (5), so GUI items with lower priority numbers (1–2) override them.
* **Pagination** — Multi-page GUIs get automatic `Previous`/`Next` navigation with `<page>` and `<max_page>` placeholders.
* **Bedrock Support** — Automatic GUI rendering for Bedrock players via Geyser, with configurable `bedrock_supported` per item and color remapping.
* **Custom GUIs** — Admins can create entirely new GUI menus by adding YAML files and registering them in `config.yml`.
* **Dynamic GUIs** — Some GUIs (e.g., Icon Selector, Chunk Claim) dynamically populate items at runtime and require a matching template section.
* **Special Materials** — Support for `basehead-<texture>` custom skulls and `playerhead-<name>` player heads.

---

## Wiki Pages

| Page | Description |
|---|---|
| [GUI Configuration Files](gui-configuration-files.md) | Complete reference for all YAML properties, command types, arguments, view requirements, and placeholders. |
| [Available GUIs](available-guis.md) | List of all built-in GUIs and their purposes. |
| [Themes](themes.md) | How themes work, default themes, and creating custom themes. |
| [Custom User-Defined GUIs](custom-user-defined-guis.md) | How to create your own custom GUI menus. |
| [GUI Settings in config.yml](gui-settings-in-config.yml.md) | Global GUI configuration options. |
| [Usage Notes and Troubleshooting](usage-notes-and-troubleshooting.md) | Common issues and solutions. |
