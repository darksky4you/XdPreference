# XdDropDownPreference

## Overview

`XdDropDownPreference` is a custom subclass of AndroidX's `DropDownPreference`, designed for advanced configuration in Android settings UIs. It allows preference values to be saved to system-level settings or as system properties, instead of SharedPreferences. It also includes broadcast support on value changes and long-press-to-reset functionality.
---
## Changelog
`12 Aug 2025`
* Fixed Intent Spamming on Fragment opening.
* Fixed Initial Value set Logic.
* Improvement in the logic.
## XML Attributes

### 1. `storeType` (int)

* **Description**: Defines which system settings table is used for storage.
* **Accepted Values**:

  * `0`: `Settings.System`
  * `1`: `Settings.Secure`
  * `2`: `Settings.Global`
* **Default**: `0`
* **Purpose**: Controls where the preference data is written/read.

### 2. `intent` (String)

* **Description**: Broadcast action sent when the preference value changes.
* **Usage**: Useful for reacting to value changes (e.g., updating UI or restarting services).
* **Example**: `"com.next.intent.ACTION_CHANGED"`

### 3. `isProp` (boolean)

* **Description**: Determines whether the value is stored as a system property instead of in settings.
* **Default**: `false`
* **Use Case**: Suitable for low-level features or boot-time configurable flags.

---

## Standard Miui/HyperOS Attributes

* `android:key`: Unique key for the preference.
* `android:title`: Main label shown to the user.
* `android:summary`: Short description or selected entry label.
* `android:defaultValue`: The initial value before any user interaction.
* `app:entries`: Array of display strings.
* `app:entryValues`: Corresponding stored values.

---

---

## Standard Android(Non-HyperOS) Attributes

* `android:key`: Unique key for the preference.
* `android:title`: Main label shown to the user.
* `android:summary`: Short description or selected entry label.
* `android:defaultValue`: The initial value before any user interaction.
* `android:entries`: Array of display strings.
* `android:entryValues`: Corresponding stored values.

---

## Features

### ✅ Custom Storage

Supports saving data in:

* `Settings.System`
* `Settings.Secure`
* `Settings.Global`
* Android system properties

Controlled by `storeType` and `isProp`.

---

### ✅ Broadcast on Value Change

If `intent` is provided, a broadcast will be sent using the specified action after any value change.

---

### ✅ Long-Press to Reset

Users can restore the preference to its original `defaultValue` by long-pressing the item in the UI.

---

### ✅ SharedPreferences-Free

By calling `setPersistent(false)`, this preference avoids the default SharedPreferences mechanism, relying solely on `XdPreferenceHelper`.

---

## Example XML Usage

```xml
<XdDropDownPreference
    android:key="notification_style"
    android:title="Notification Style"
    android:summary="Choose the notification layout"
    android:defaultValue="classic"
    app:entries="@array/notif_style_labels"
    app:entryValues="@array/notif_style_values"
    storeType="2"
    intent="com.next.intent.NOTIFICATION_STYLE_CHANGED"
    isProp="false" />
```

---

## Developer Notes

* **Version**: `v2.0`
* **Helper Class**: Delegates storage logic and broadcasting to `XdPreferenceHelper`.
* **Best Use Case**: Advanced settings in custom Android ROMs, mods, or system-level settings apps.
* **Toast Feedback**: Provides visual confirmation when default is restored.
* **Compatibility Tip**: If anyone wants to use this preference in non-MIUI or HyperOS mods, then search `Lmiuix/preference/` and replace it with `Landroidx/preference/` or use a valid `DropDownPreference` superclass.



---

## License

This component is created and maintained by `@darksky4you`. You are free to modify and use it in your own Android projects, especially those involving advanced customization or ROM development.