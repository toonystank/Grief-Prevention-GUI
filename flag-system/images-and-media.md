---
icon: wrench
---

# Configuration Files

#### FlagDefaults.yml

* **Purpose**: Allows setting the default state (<mark style="color:yellow;">enabled</mark>) and default arguments for flags.
* **Structure**:
  * Each flag is listed by its case-sensitive name (matching <mark style="color:yellow;">FlagOptions.yml</mark>).
  * <mark style="color:yellow;">enabled</mark>: Sets whether the flag is active by default (e.g., <mark style="color:yellow;">false</mark> for <mark style="color:yellow;">EnterMessage</mark>).
  * <mark style="color:yellow;">argument</mark>: Specifies the default argument (e.g., a default message for <mark style="color:yellow;">EnterMessage</mark>).
*   **Example**:

    ```yaml
    EnterMessage:
      enabled: false
      argument: "You are now entering %griefprevgui_getbyid_claimname_{claimid}%"
    ```
* **Notes**: Flags not listed in <mark style="color:yellow;">FlagDefaults.yml</mark> are disabled by default with no default argument.

#### FlagOptions.yml

* **Purpose**: Defines the properties and functionality of each flag for GUI display.
* **Key Fields**:
  * <mark style="color:yellow;">enable</mark>: Determines if the flag is available in the GUI (<mark style="color:yellow;">true</mark>/<mark style="color:yellow;">false</mark>).
  * <mark style="color:yellow;">material</mark>: The item representing the flag in the GUI (e.g., <mark style="color:yellow;">OAK\_SIGN</mark> for <mark style="color:yellow;">EnterMessage</mark>).
  * <mark style="color:yellow;">permission</mark>: Sets permissions for activation (<mark style="color:yellow;">activate</mark>) and usage (<mark style="color:yellow;">usage</mark>), defaulting to NONE.
  * <mark style="color:yellow;">order</mark>: Specifies the flag’s position in the GUI (e.g., <mark style="color:yellow;">1</mark> for <mark style="color:yellow;">EnterMessage</mark>, <mark style="color:yellow;">2</mark> for <mark style="color:yellow;">ExitMessage</mark>).
  * <mark style="color:yellow;">lore</mark>: Descriptive text shown in the GUI, including placeholders for status and arguments.
  * <mark style="color:yellow;">owner\_only</mark>: Restricts flag usage to claim owners (set to <mark style="color:yellow;">false</mark> for all flags).
  * <mark style="color:yellow;">requires\_argument</mark>: Indicates if the flag needs an argument (e.g., <mark style="color:yellow;">true</mark> for <mark style="color:yellow;">EnterMessage</mark>, <mark style="color:yellow;">false</mark> for <mark style="color:yellow;">NoElytra</mark>).
  * <mark style="color:yellow;">special</mark>: Additional notes (e.g., instructions for <mark style="color:yellow;">ClaimWarp)</mark>.
  * <mark style="color:yellow;">custom\_left\_click\_commands</mark> / <mark style="color:yellow;">custom\_right\_click\_commands</mark>: Commands to run on click (e.g., opening a GUI for <mark style="color:yellow;">ClaimIcon</mark>).
  * <mark style="color:yellow;">only\_run\_custom\_commands</mark>: If <mark style="color:yellow;">true</mark>, the flag only runs custom commands and does not enable them by default.
  * <mark style="color:yellow;">only\_run\_custom\_commands\_on\_disabled</mark> / <mark style="color:yellow;">only\_run\_custom\_commands\_on\_enabled</mark>: Restricts command execution based on flag state.
  * <mark style="color:yellow;">model\_data</mark>: Model data support for provided material.
* **Notes**: All built-in flags are enabled (<mark style="color:yellow;">enable: true</mark>) and have no permission requirements by default.

#### flagsettings.yml

* **Purpose**: Contains additional settings for specific flags, primarily <mark style="color:yellow;">ClaimFly</mark>, and general restrictions.
* **Key Sections**:
  * **Restrictions**:
    * <mark style="color:yellow;">NewManagerFlagRestriction</mark>s: Enables a cooldown for new managers (default: <mark style="color:yellow;">1 hour</mark>).
    * <mark style="color:yellow;">HideFlagsNoPermission</mark>: If enabled, hides flags from the GUI if the player lacks activation permission (default: <mark style="color:yellow;">false</mark>).
  *   **Fly Settings** (for <mark style="color:yellow;">ClaimFly</mark>):

      * <mark style="color:yellow;">timedFlight</mark>: Configures timed flight duration (default: disabled, initial value 1 minute).
      * <mark style="color:yellow;">particleEffects</mark>: Enables/disables visual effects for flying (default: <mark style="color:yellow;">true</mark>).
      * <mark style="color:yellow;">permissionSettings</mark>: Optional permission checks for flight (default: no permission required).
      * <mark style="color:yellow;">flagRestrictions</mark>: Controls flight in restricted claims, with bypass options for owners/managers.
      * <mark style="color:yellow;">consoleWarnings</mark>: Suppresses warnings if <mark style="color:yellow;">ClaimFly</mark> is not disabled with bypass permissions.
      * <mark style="color:yellow;">requirePlayerToggleFlight</mark>: If enabled Players must manually toggle flight using _/claim fly_ or _/claimfly_ when entering a claim with flight enabled.

      <mark style="color:yellow;">messages</mark>: Configures entry/exit message display (e.g., title mode, default: <mark style="color:yellow;">false</mark>).
* **Notes**: Most settings are specific to <mark style="color:yellow;">ClaimFly</mark>, but restrictions apply globally.&#x20;
