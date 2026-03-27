---
icon: square-info
---

# Usage Notes and Troubleshooting

## Usage Notes

### Accessing GUIs

GUIs are opened via commands or from other GUIs:

| Method | Example |
|---|---|
| Main menu command | `/claim menu` or `/claim` |
| Claim info by ID | `/claiminfo <claimid>` |
| From another GUI's click command | `[player] claiminfo {claimid}` |
| Custom GUI | `[player] gpopenGUI MyCustomMenu {claimid}` |

### Customization Tips

- **Modify safely**: Edit `menu_title`, `rows`, `args`, `theme`, and all item properties freely. Avoid changing `version` or `gui_type` for default GUIs.
- **Test with debug**: Enable debug mode in `config.yml` to see detailed logs of GUI loading, placeholder resolution, and command execution.
- **Use priority for layering**: Place decorative items at priority `3–4` and functional items at `1–2` to ensure buttons always override decorations.
- **Anvil inputs**: Use `<anvilreply>` in commands for free-text input (e.g., renaming claims) and `<anvilplayer>` for player name selection.

---

## Troubleshooting

### GUI Not Opening

| Check | Solution |
|---|---|
| File exists | Ensure the GUI YAML file is in the GUI folder with proper naming. |
| Custom GUI registered | For custom GUIs, verify the name is in `config.yml` under `gui.custom_guis`. |
| File name suffix | Custom GUI files must end with `_EN.yml` (e.g., `MyMenu_EN.yml`). |
| YAML syntax | Check for syntax errors (missing quotes, bad indentation). Server console will show errors on load. |
| GUI disabled | Check `disabled_guis` in `config.yml`. Use `gpgui.bypass.guidisabled` permission to bypass. |
| World disabled | If `disable_gui_on_grief_prevention_disabled_worlds` is `true`, GUIs won't work in non-GP worlds. |

### Item Not Showing

| Check | Solution |
|---|---|
| Valid slot | Slot must be within `0` to `(rows × 9) - 1`. For a 6-row GUI, valid range is `0–53`. |
| View requirements | If the item has `view_requirement`, verify the conditions pass for your player. Use PlaceholderAPI to test placeholder values. |
| Priority conflict | If another item with a lower priority number (higher priority) occupies the same slot and its requirements pass, your item will be hidden. |
| Bedrock support | If `bedrock_supported: false`, the item won't show for Bedrock players. Theme items default to `false`. |

### Commands Not Executing

| Check | Solution |
|---|---|
| Missing prefix | Every command must start with a type prefix: `[player]`, `[console]`, `[sound]`, `[close]`, `[reopen]`, or `[message]`. |
| Wrong command list | `click_commands` overrides both left/right. If you define `click_commands` alongside `left_click_commands`, only `click_commands` runs. |
| Placeholder not resolving | Ensure `{argName}` matches an entry in the GUI's `data.args` list. Check that PlaceholderAPI placeholders are valid. |
| Delay syntax | `<delay=N>` must be appended directly to the command line with no space (e.g., `[player] cmd<delay=20>`, not `[player] cmd <delay=20>`). |

### Theme Not Applying

| Check | Solution |
|---|---|
| File exists | The theme file must be named `<theme_name>_EN.yml` in the theme folder. |
| Name matches | The `theme` field in the GUI's `data` section must exactly match the file name prefix (e.g., `theme: clean_4` loads `clean_4_EN.yml`). |
| YAML syntax | Verify the theme file has valid YAML syntax and all items have `priority: 5`. |

### Navigation Not Working

| Check | Solution |
|---|---|
| Section names | Navigation items must be named exactly `Previous` and `Next` (case-sensitive). |
| Slots | Typically placed in slots `47` and `51`, but any valid slot works. |
| Multi-page only | Navigation only appears when there are enough dynamic items to create multiple pages. |

### Dynamic Items Missing

| Check | Solution |
|---|---|
| Template section | Dynamic GUIs need a matching template section in `items` (e.g., `ICON_SELECTOR` section for the Icon Selector GUI). |
| `gui_type` mismatch | For custom GUIs, `gui_type` must exactly match the name in `config.yml`'s `custom_guis`. |

### Chunk Claim GUI Issues

| Check | Solution |
|---|---|
| Not enabled | Set `experimental.features.chunk_claiming.enable: true` in `config.yml`. |
| Grid too small/large | Adjust `radius` (default: `3`, creating a 7×7 grid). Make sure `rows` in the GUI file can fit the grid. |
| Can't extend | Ensure `extend_adjacent_claims: true` in config. Only owners and managers can extend. Right-click an owned chunk to enter extend mode. |
