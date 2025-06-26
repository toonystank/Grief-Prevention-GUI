---
icon: gear
---

# Custom User-Defined GUIs

Admins can define custom GUIs in `config.yml` under `gui.custom_guis`. These GUIs are loaded by the plugin and must follow specific naming and configuration rules.

* **Definition**: List custom GUIs in `config.yml` under `gui.custom_guis` (e.g., `ClaimUpgradeBiomeSelector`).
* **File Naming**: The plugin loads the corresponding YAML file with `_EN` appended to the name (e.g., `ClaimUpgradeBiomeSelector` loads `ClaimUpgradeBiomeSelector_EN.yml`).
* **GUI Type**: The `gui_type` In the GUI file’s `data` section must exactly match the name listed in `gui.custom_guis` (e.g., `ClaimUpgradeBiomeSelector`).
* **File Location**: Custom GUI files must be placed in the GUI folder alongside default GUI files.

**Example**:

*   In `config.yml`:

    ```yaml
    gui:
      custom_guis:
        - ClaimUpgradeBiomeSelector
    ```
* The plugin loads `ClaimUpgradeBiomeSelector_EN.yml`, and its `data` section must include `gui_type: ClaimUpgradeBiomeSelector`.&#x20;
