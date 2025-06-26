---
icon: list-dropdown
---

# GUI Overview

* **Customizable GUIs**: Each GUI is defined in its own file, with additional custom GUIs configurable in config.yml.
* **Dynamic Content**: GUIs use placeholders (e.g., <mark style="color:yellow;">%griefprevgui\_getbyid\_location\_{claimid}%</mark>, \<itemname>) to display claim-specific or context-sensitive information.
* **Interactive Elements**: Items can trigger commands on left or right clicks, such as teleporting, setting flags, or opening other menus.
* **Conditional Display**: Items can have view\_requirement conditions to control visibility based on permissions or settings.
* **Navigation Controls**: Multi-page GUIs include Next and Previous items for easy navigation.
* **Custom GUIs**: Certain GUIs (e.g., ICON\_SELECTOR) dynamically populate content and require specific sections in their configuration. User-defined custom GUIs can be added in config.yml.&#x20;

The GriefPrevention GUI Addon provides a graphical user interface for managing claims, flags, and related features of the GriefPrevention plugin. Each GUI is defined in a separate YAML configuration file, allowing server admins to customize its appearance and functionality. Admins can also define custom GUIs in `config.yml`. This wiki details the structure of the GUI system, themes, available GUIs, their configuration, and general GUI settings.

***

## GUI System

The GUI system enables claim owners and trusted players to interact with claim settings through intuitive menus. GUIs are defined in individual YAML files, each containing a `data` section for overall properties and an `items` section for interactive elements, similar to the structure of `FlagOptions.yml`. The system supports dynamic content via placeholders, custom themes, and special sections for custom GUIs.

### Key Features

* Customizable GUIs: Each GUI is defined in its own file, with additional custom GUIs configurable in `config.yml`.
* Dynamic Content: GUIs use placeholders (e.g., `%griefprevgui_getbyid_location_{claimid}%`, `<itemname>`) to display claim-specific or context-sensitive information.
* Interactive Elements: Items can trigger commands on left or right clicks, such as teleporting, setting flags, or opening other menus.
* Conditional Display: Items can have `view_requirement` conditions to control visibility based on permissions or settings.
* Navigation Controls: Multi-page GUIs include `Previous` and `Next` sections for navigation, defined in the `items` section with specific slots and display names.
* Custom GUIs: Certain GUIs (e.g., `ICON_SELECTOR`) dynamically populate content and require specific sections in their configuration. User-defined custom GUIs can be added in `config.yml`.
* Themes: GUIs can apply visual themes (e.g., `default`, `nature`, `clean`) defined in separate `_EN.yml` files in the theme folder, with high-priority items that can be overridden.&#x20;
