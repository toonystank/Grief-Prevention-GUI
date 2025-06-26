---
icon: square-info
---

# Usage Notes and Troubleshooting

## Usage Notes&#x20;

* **GUI Navigation**: Flags are displayed in the order specified by the <mark style="color:yellow;">order</mark> field. Use the GUI to toggle flags and input arguments.
* **Permissions**: Most flags require no permissions (<mark style="color:yellow;">NONE</mark>), making them accessible to all claim owners.
* **Custom Commands**: Flags like <mark style="color:yellow;">ClaimIcon</mark>, <mark style="color:yellow;">ChangeBiome</mark>, and <mark style="color:yellow;">NoMobSpawnsType</mark> use custom commands to open specialised GUI menus for configuration.
* **Restrictions**: Some flags (e.g., <mark style="color:yellow;">ClaimFly</mark>) have additional settings in <mark style="color:yellow;">flagsettings.yml</mark> to control behaviour, such as cooldowns or bypass permissions.&#x20;

### Troubleshooting

* **Flag Not Showing in GUI**: Check if <mark style="color:yellow;">enable</mark> is <mark style="color:yellow;">true</mark> in <mark style="color:yellow;">FlagOptions.yml</mark> and verify the <mark style="color:yellow;">order</mark> value.
* **Custom Commands Not Working**: Ensure <mark style="color:yellow;">only\_run\_custom\_commands</mark> is configured correctly and that commands are valid.
* **GPFlags Not Appearing**: Confirm GPFlags is installed and flags are enabled in <mark style="color:yellow;">FlagOptions.yml</mark>.
* **Flight Issues**: Review <mark style="color:yellow;">flagsettings.yml</mark> for <mark style="color:yellow;">ClaimFly</mark> restrictions and permissions.&#x20;
