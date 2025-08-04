# XdSeekBarPreference

## Overview

`XdSeekBarPreference` is a custom `Preference` component that displays a `SeekBar` with optional increment/decrement buttons, value display, and reset functionality. It supports various storage mechanisms including Android `System`, `Secure`, and `Global` settings, as well as system properties.

## Features

* Configurable min, max, interval (step), and units
* Optional `+/-` buttons and reset functionality
* Supports system properties and multiple settings storage types
* Broadcasts intents when value changes
* Default value text support
* Continuous or on-release value updates
* Long-click midpoint or min/max behavior for faster control
* Optional hiding of navigation buttons

## Changelog
`04 Aug 2025`
* Updated The Layout a bit.
* New attr `hideReset` to Hide the Reset Button.
* Improvement in the logic.

## Usage

### XML Declaration

To use `XdSeekBarPreference` in your XML preferences:

```xml
<XdSeekBarPreference
    android:key="example_seekbar"
    android:title="Example Seek Bar"
    android:defaultValue="50"
    min="0"
    max="100"
    step="5"
    units="%"
    showSign="true"
    storeType="0"         <!-- 0 = System, 1 = Secure, 2 = Global -->
    isProp="false"        <!-- true if using system properties -->
    continuousUpdates="true"
    defaultValueText="Default"
    hideNav="false"
    hideReset="false"
    intent="com.example.ACTION_UPDATE" />
```

### Attributes

| Attribute              | Type      | Description                                            |
| ---------------------- | --------- | ------------------------------------------------------ |
| `android:key`          | `String`  | Unique preference key                                  |
| `android:title`        | `String`  | Title of the preference                                |
| `android:defaultValue` | `Integer` | Default progress value                                 |
| `min`                  | `Integer` | Minimum value                                          |
| `max`                  | `Integer` | Maximum value                                          |
| `step`                 | `Integer` | Value increment/decrement interval                     |
| `units`                | `String`  | Units string to display beside the value               |
| `showSign`             | `Boolean` | Whether to display a '+' sign for positive values      |
| `continuousUpdates`    | `Boolean` | Whether to update persistently during seek             |
| `defaultValueText`     | `String`  | Optional text to show for default value                |
| `storeType`            | `Integer` | Storage type: `0` (System), `1` (Secure), `2` (Global) |
| `isProp`               | `Boolean` | Whether to use system properties                       |
| `hideNav`              | `Boolean` | If true, hides the +/- buttons
| `hideReset`              | `Boolean` | If true, hides the Reset button                         |
| `intent`               | `String`  | Optional broadcast intent to send on value change      |

## Behavior

* The preference reads and stores its value using `XdPreferenceHelper`.
* Supports Android Settings (`System`, `Secure`, `Global`) or system properties.
* Shows the current value with optional units and sign.
* Resets to default value on reset button click.
* On long-press, the +/- buttons go to min/max or midpoint based on current value.
* If an `intent` is specified, it is broadcast when the value changes.

## Notes
* Preference Posted based on `HyperOS`.
* For using in `Non-Hyper/Miui` roms, we need to modify the layout. Just change miuix seekbar to Normal.

## Events

* `onProgressChanged` updates the value based on user interaction.
* `onStartTrackingTouch` and `onStopTrackingTouch` manage tracking logic.
* All changes trigger `persistInt()` and storage updates via `setKeyValues()`.

## License

This project is created and maintained by `@darksky4you`. You are free to modify, distribute, and integrate it into your own Android projects.