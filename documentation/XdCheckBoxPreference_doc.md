# XdCheckBoxPreference

## Overview
`XdCheckBoxPreference` is a custom preference class that extends `SwitchPreference` to store boolean values using different storage types, including system properties and Android Settings (`System`, `Secure`, `Global`).

## Features
- Supports different storage types (`System`, `Secure`, `Global`)
- Reads and writes system properties
- Sends broadcast intents upon value changes
- Allows resetting to default value on long press
- Non-persistent storage behavior to handle dynamic updates

## Changelog
`12 Aug 2025`
* Fixed Intent Spamming on Fragment opening.
* Fixed Initial Value set Logic.
* Improvement in the logic.
## Usage

### XML Declaration
To use `XdCheckBoxPreference` in your preference XML:
```xml
<XdCheckBoxPreference
    android:key="example_key"
    android:title="Example Checkbox"
    android:defaultValue="false"
    storeType="0"  <!-- 0 = System, 1 = Secure, 2 = Global -->
    isProp="false"  <!-- true if using system properties -->
    intent="com.example.ACTION_UPDATE" />
```

### Attributes
| Attribute | Type | Description |
|-----------|------|-------------|
| `android:key` | `String` | Unique key for the preference |
| `android:title` | `String` | Title displayed in the UI |
| `android:defaultValue` | `Boolean` | Default checked state |
| `storeType` | `Integer` | Storage type: `0` (System), `1` (Secure), `2` (Global) |
| `isProp` | `Boolean` | `true` if the preference should be stored in system properties |
| `intent` | `String` | Broadcast intent to send when the value changes |

## Behavior
- The preference value is retrieved and stored in the appropriate storage type.
- When toggled, the value is updated in either system properties or Android Settings.
- On long press, the preference resets to its default value and shows a toast notification.
- If an intent action is specified, it is sent when the value changes.

## License
This project is created and maintained by `@darksky4you`. Feel free to modify and use it in your projects.

