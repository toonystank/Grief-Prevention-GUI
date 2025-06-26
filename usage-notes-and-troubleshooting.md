---
icon: square-info
---

# Usage Notes and Troubleshooting

## Usage Notes

* **Accessing GUIs**: GUIs are accessed via commands (e.g., `/claim menu` for `MAIN_MENU`) or by interacting with flags (e.g., clicking `ClaimIcon` to open `ICON_SELECTOR` or `ChangeBiome` to open `ClaimUpgradeBiomeSelector`).
* **Custom GUIs**: Default custom GUIs (e.g., `ICON_SELECTOR`) dynamically populate items and require a matching section in `items`. User-defined custom GUIs (e.g., `ClaimUpgradeBiomeSelector`) are added in `config.yml` and loaded from `_EN`-suffixed files.
* **Themes**: Apply themes via the `theme` field in the GUI’s `data` section (e.g., `clean_4` for `ClaimUpgradeNoEnter`). Custom themes can be created by adding `<theme_name>_EN.yml` files.
* **Customization**: Admins can modify `menu_title`, `rows`, `args`, `theme`, item properties, and `config.yml` settings to tailor the GUI experience.
* **Placeholders**: Use placeholders (e.g., `%griefprevgui_getbyid_flags_parma_ChangeBiome_{claimid}%`, `<itemname>`) to display dynamic information.
* **Navigation**: Multi-page GUIs include `Previous` and `Next` sections for easy navigation, typically in slots `47` and `51`.

***

## Troubleshooting

* **GUI Not Opening**: Verify that the GUI file exists and is correctly formatted. For custom GUIs, ensure they are listed in `config.yml` under `gui.custom_guis` and the file name ends in `_EN` (e.g., `ClaimUpgradeBiomeSelector_EN.yml`). Check for errors in the server console.
* **Theme Not Applied**: Ensure the `theme` field in the GUI’s `data` section matches a `<theme_name>_EN.yml` file in the theme folder (e.g., `default_EN.yml`). Verify the theme file’s syntax.
* **Items Not Displaying**: Ensure `slot` is a valid integer (0–53 for a 6-row GUI) or `slots` is a valid list of integers, and that `view_requirement` conditions are met. Check that GUI item priorities are lower than theme item priorities (e.g., `1` or `2` vs. `5`).
* **Navigation Not Working**: Confirm that `Previous` and `Next` sections are defined in the `items` section for multi-page GUIs, typically in slots `47` and `51`.
* **Dynamic Items Missing**: For default custom GUIs, confirm that the required section (e.g., `ICON_SELECTOR`) is present in `items`.
* **Commands Not Executing**: Check that `left_click_commands`, `right_click_commands`, or `click_commands` are correctly defined and use valid syntax.
* **Broken GUI**: Avoid editing `version` or `gui_type` in the `data` section for default GUIs. For custom GUIs, ensure `gui_type` matches the `custom_guis` entry.
* **Disabled GUIs**: If a GUI is disabled in `config.yml` (`disabled_guis`), use the `gpgui.bypass.guidisabled` permission to access it.&#x20;
