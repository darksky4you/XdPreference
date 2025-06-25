# XdAppSelectPreference

## Overview

`XdAppSelectPreference` is a custom dialog-based preference for selecting multiple installed apps on an Android device. Built for advanced customization, it supports saving selected package names in system settings (`Settings.System`, `Settings.Secure`, or `Settings.Global`) or as system properties. It also supports broadcasting a custom intent when the selection changes, and allows restoring the default app list via long press.

---

## XML Attributes

### 1. `storeType` (int)

* **Description**: Specifies where the selected app list will be stored.
* **Values**:

  * `0`: Save to `Settings.System`.
  * `1`: Save to `Settings.Secure`.
  * `2`: Save to `Settings.Global`.
* **Default**: `0` (System)

---

### 2. `intent` (String)

* **Description**: A broadcast intent sent when the selected apps change.
* **Usage**: Trigger other components or services based on app selection.
* **Example**: `"com.example.UPDATE_APPS"`

---

### 3. `isProp` (boolean)

* **Description**: When `true`, stores selected package names as a system property.
* **Default**: `false`

---

### 4. `filterFlag` (int)

* **Description**: Filters the app list by category or type.
* **Values**:

  * `0`: All apps
  * `1`: Only system apps
  * `2`: Only user apps
  * `3`: All apps (no category check)
  * `4`: Audio apps
  * `5`: Video apps
  * `6`: Games
  * `7`: Productivity apps
* **Default**: `0` (All)

---

### 5. `android:entries` (string-array)

* **Description**: Whitelisted packages to always include in the list, even if not normally shown.
* **Usage**: Useful for including hidden or non-launchable apps.

---

### 6. `showPackageName` (boolean)

* **Description**: Controls whether package names are displayed under app titles.
* **Default**: `true`

---

## Standard Android XML Attributes

* `android:key`: Unique identifier for this preference.
* `android:title`: Display title for the preference.
* `android:summary`: Summary with support for dynamic count using `%s`.
* `android:defaultValue`: Comma-separated default package list.

---

## Example XML Usage

```xml
<XdAppSelectPreference
    android:key="blocked_apps"
    android:title="Blocked Applications"
    android:summary="%s"
    android:defaultValue="com.android.chrome,com.android.youtube"
    android:entries="@array/force_included_apps"
    storeType="1"
    intent="com.example.ACTION_BLOCK_APPS"
    isProp="false"
    filterFlag="2"
    showPackageName="true" />
```

---

## Key Features

### 1. **Multi-App Selection Dialog**

* Allows selecting multiple apps using a ListView with checkboxes.
* Dialog UI includes app icons, names, and optionally package names.

---

### 2. **Flexible Data Storage**

* Store values in `Settings.System`, `Settings.Secure`, `Settings.Global`, or as system properties using `XdPreferenceHelper`.

---

### 3. **Custom Broadcast on Value Change**

* Sends broadcast intent (if specified) upon confirming selection to enable dynamic system reactions.

---

### 4. **Restore Defaults via Long Press**

* Long-press the preference to restore the original default value.
* User feedback via toast message.

---

### 5. **Dynamic Summary Update**

* Automatically updates summary to reflect the number of apps selected.
* Supports `%s` placeholder in summary string.

---

### 6. **App Filtering and Whitelisting**

* Filter by app type or category (`filterFlag`).
* Always include whitelisted packages via `android:entries`.

---

## Developer Notes

* **Dialog UI**: Uses a `ListView` with a custom layout (`xd_appselect_preference_layout`).
* **Helper Class**: Relies on `XdPreferenceHelper` to abstract setting access and broadcasting.
* **Whitelisting**: Even non-launchable apps can be force-included using `android:entries`.

---


## License
This project is created and maintained by `@darksky4you`. Feel free to modify and use it in your projects.

