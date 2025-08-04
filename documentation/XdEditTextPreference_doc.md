# XdEditTextPreference
## Overview

`XdEditTextPreference` is a custom `EditTextPreference` that allows users to manage preferences in a more flexible manner. It supports storing preferences in different storage types (`Settings.System`, `Settings.Secure`, `Settings.Global`) and can send custom broadcast intents when the preference value changes. Additionally, it allows the storage of values as system properties for deeper system-level customization.

This preference supports long-click actions to restore default values, making it a more interactive and customizable option for Android settings.

## Changelog
`04 Aug 2025`
* Fixed `SetProp` Issue.
* Updated Summary Showing Logic, `android:summary="%s"` for showing the Actual Value.
* Improvement in the logic.

## XML Attributes

### 1. `storeType` (int)

- **Description**: Defines the storage type for the preference value.
- **Values**:

  - `0`: Store the value in `Settings.System`.
  - `1`: Store the value in `Settings.Secure`.
  - `2`: Store the value in `Settings.Global`.

  By default, this is set to `0` (use `Settings.System`).

- **Usage**: This attribute controls where the preference value will be saved, providing flexibility in choosing the right location for storing settings.

### 2. `intent` (String)

- **Description**: Specifies a custom intent action to broadcast when the preference value is changed.
- **Usage**: If you want to notify other components (such as services or activities) of the change, you can specify an intent action. For instance, if you are modifying a setting that affects system behavior, you can use this attribute to send a broadcast to notify other parts of your app or system.

  Example value: `"com.example.UPDATE_SETTING"`.

### 3. `isProp` (boolean)

- **Description**: If set to `true`, the preference value will be stored as a system property rather than in `Settings.System`, `Settings.Secure`, or `Settings.Global`.
- **Default Value**: `false` (preference value is stored in settings, not as a property).

  This is useful for storing values that need to be accessed by low-level system services or other components that rely on system properties.

## Example XML Usage

```xml
<XdEditTextPreference
        android:key="setting_key"  <!-- Unique key for the setting -->
        android:title="Custom Setting"  <!-- Title shown in the settings UI -->
        android:summary="This setting allows you to modify system behavior"  <!-- Brief description of the setting -->
        android:defaultValue="Default Value"  <!-- Default value to be used if none is provided -->
        storeType="1"  <!-- Store the value in Settings.Secure -->
        intent="com.example.UPDATE_SETTING"  <!-- Send a custom intent when the value changes -->
        isProp="true"  <!-- Store the value as a system property -->
        android:inputType="text"  <!-- Input type for the EditText field -->
        android:hint="Enter custom value"  <!-- Hint text for the EditText field -->
        android:maxLength="20"  <!-- Optional maximum length for the input -->
        android:selectAllOnFocus="true"  <!-- Automatically select all text when the field is focused -->
/>
```

### Explanation of XML Attributes:

- `android:key`: A unique key for identifying this preference.
- `android:title`: The title displayed for this preference in the settings UI.
- `android:summary`: A brief description of what this preference does.
- `android:defaultValue`: The default value to be used if no value is set.
- `storeType`: Determines where the value is stored (`0`, `1`, or `2`).
- `intent`: Specifies an intent to be broadcast when the preference value changes.
- `isProp`: Whether the value should be stored as a system property (`true`) or not (`false`).
- `android:inputType`: Defines the type of input for the EditText field (e.g., `text`, `number`).
- `android:hint`: The hint text shown in the EditText field when it's empty.
- `android:maxLength`: Optionally limits the number of characters in the input field.
- `android:selectAllOnFocus`: If `true`, all text is selected when the field is focused.

## Key Features:

1. **Multiple Storage Locations**: Use `storeType` to determine whether the preference value should be stored in `Settings.System`, `Settings.Secure`, or `Settings.Global`. This is ideal for different types of system settings.
2. **Custom Intent Broadcast**: With the `intent` attribute, you can trigger broadcasts to other components of your app or system when the preference value changes. This is useful for synchronizing settings across different components.

3. **System Property Support**: If you need to store the preference as a system property (instead of in the settings provider), set `isProp` to `true`. This allows you to manage deeper system-level configurations.

4. **Long Click to Restore Default**: The preference allows users to long-click the preference item to reset it to the default value, providing an easy way to revert settings.

## Conclusion

The `XdEditTextPreference` is a powerful and flexible custom preference for managing settings in Android. It offers multiple storage options, support for system properties, and custom intent broadcasting, making it ideal for both simple and complex configurations in your Android application.

## License
This project is created and maintained by `@darksky4you`. Feel free to modify and use it in your projects.

