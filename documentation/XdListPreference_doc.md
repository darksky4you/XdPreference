
# XdListPreference

## Overview

`XdListPreference` is an enhanced version of Android's `ListPreference`, designed for advanced customization and system integration. It allows saving preference values in various Android settings storage (`Settings.System`, `Settings.Secure`, `Settings.Global`) or as system properties. Additionally, it supports broadcasting intents upon value changes and restoring default values via long press.

This component is ideal for developers looking to build modular and system-aware preferences for custom Android builds or advanced configuration UIs.

---

## XML Attributes

### 1. `storeType` (int)

* **Description**: Determines where the preference value will be stored.
* **Values**:

  * `0`: Save to `Settings.System`.
  * `1`: Save to `Settings.Secure`.
  * `2`: Save to `Settings.Global`.
* **Default**: `0` (System)
* **Purpose**: Enables flexibility in choosing the most appropriate storage type for the preference value.

### 2. `intent` (String)

* **Description**: A custom broadcast intent that is sent whenever the preference value changes.
* **Usage**: Useful for triggering updates in other components like services, receivers, or UI elements based on preference changes.
* **Example**: `"com.example.UPDATE_SETTING"`

### 3. `isProp` (boolean)

* **Description**: When set to `true`, the preference is stored as a system property.
* **Default**: `false`
* **Purpose**: Ideal for low-level or system-wide configurations that depend on Android’s system property mechanism.

---

## Standard Android XML Attributes

* `android:key`: Unique identifier for this preference.
* `android:title`: Display title for the preference.
* `android:summary`: Description or current value display.
* `android:defaultValue`: Default value for the preference.
* `android:entries`: List of display options.
* `android:entryValues`: Corresponding values for the entries.

---

## Example XML Usage

```xml
<XdListPreference
    android:key="custom_theme"
    android:title="Select Theme"
    android:summary="Current theme: %s"
    android:defaultValue="light"
    android:entries="@array/theme_entries"
    android:entryValues="@array/theme_values"
    storeType="1"
    intent="com.example.ACTION_THEME_CHANGED"
    isProp="true" />
```

---

## Key Features

### 1. **Flexible Storage Options**

* Select between `Settings.System`, `Settings.Secure`, or `Settings.Global` using `storeType`.
* Store values in system properties (`isProp="true"`) for low-level configuration.

### 2. **Custom Intent Broadcasting**

* Automatically broadcasts a custom intent when the preference value changes.
* Useful for triggering updates across components and services.

### 3. **Restore Default with Long Press**

* Long-press the preference item to restore the default value.
* Provides user-friendly fallback without additional UI.

### 4. **Auto Summary Update**

* If the summary contains `%s`, it dynamically updates to match the selected entry's label.

---

## Developer Notes

* **Persistence**: This preference disables default `SharedPreferences` persistence by calling `setPersistent(false)`, instead delegating storage to custom settings or properties.
* **Version**: `v2.0`
* **Helper**: Uses `XdPreferenceHelper` to abstract storage, retrieval, and intent handling.
* **System Integration**: Great for system mods, custom ROMs, and power-user tools.

---

## License

This component is created and maintained by `@darksky4you`. You are free to modify and use it in your own Android projects, especially those involving advanced customization or ROM development.