---
icon: screwdriver-wrench
---

# GUI Settings in config.yml

The `gui` section in `config.yml` configures general GUI behavior and allows defining custom GUIs.

* **Key Settings**:
  * `theme`: Sets the default theme for GUIs (`default`, `nature`, `clean`). Individual GUI files can override this via the `theme` field in their `data` section (e.g., `ClaimUpgradeNoEnter_EN.yml` uses `clean_4`).
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
  * The `theme` setting in `config.yml` sets the default theme, but individual GUIs can override it (e.g., `theme: clean_4` in `ClaimUpgradeNoEnter_EN.yml`).
