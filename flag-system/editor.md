---
icon: flag-pennant
---

# Flag Overview

The GriefPrevention GUI Addon enhances the GriefPrevention plugin by providing a graphical user interface for managing claim flags. These flags allow claim owners to customise settings and behaviours within their claims. This wiki details the addon's built-in flags, configuration, and integration with GPFlags (if installed).

***

### Flag System

The flag system is managed through the GUI, where claim owners can enable/disable flags and configure their settings. Flags are defined in <mark style="color:yellow;">FlagOptions.yml</mark>, and their default states can be set in <mark style="color:yellow;">FlagDefaults.yml</mark>. The order field in FlagOptions.yml determines the order of flags in the GUI.&#x20;

#### Key Features

* **Built-in Flags**: The addon provides a set of built-in flags for common claim customisations.
* **GPFlags Integration**: If GPFlags is installed, its flags are automatically added to <mark style="color:yellow;">FlagOptions.yml</mark> but are disabled by default. Server admins can enable them as needed.
* **Permissions**: Flags can have activation and usage permissions set to <mark style="color:yellow;">NONE</mark> by default for accessibility.
* **Custom Commands**: Some flags support custom commands for advanced functionality, such as opening specific GUI menus.
* **Arguments**: Flags may require arguments (e.g., message text, biome type) to function, as specified in <mark style="color:yellow;">requires\_argument</mark>.

{% hint style="info" %}
**Note**: The flags listed here are claim-specific (not admin flags) and are provided by the GriefPrevention GUI Addon. &#x20;
{% endhint %}
