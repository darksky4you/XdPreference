# XdPreference

## Overview
`XdPreference` is a custom Android preference library that extends standard preferences to provide additional functionality and flexibility for managing and storing preference values in different storage types (System, Secure, Global) or system properties. This library includes a variety of custom preference components like `XdCheckBoxPreference` and `XdEditTextPreference` for enhanced use cases.

## Key Features
- **Support for Multiple Storage Types**: Easily store and retrieve preference values from different locations, such as `System`, `Secure`, and `Global` Android settings.
- **System Property Integration**: Seamless integration with system properties for specific use cases where system-level preferences need to be stored and accessed.
- **Intent Broadcasts**: Sends custom broadcast intents when preference values are changed, providing easy hooks for other components to react to preference changes.
- **Long Press Reset**: Option to reset preferences to their default value on a long press, providing a simple and intuitive way to restore settings.
- **Dynamic Value Updates**: Non-persistent behavior that ensures preferences are updated dynamically and do not require reloading or restarting the app to reflect changes.

## Props
- **Flexibility**: Offers a flexible solution for managing preferences across different storage types and systems.
- **Customization**: Provides custom preferences like `XdCheckBoxPreference` and `XdEditTextPreference` with built-in support for broadcasting intents and resetting values.
- **Easy to Implement**: Simple XML declarations for integrating into Android projects, allowing developers to quickly implement custom preferences with minimal code.
- **Compatibility**: Compatible with standard Android preferences and seamlessly integrates into preference screens, dialogs, and other UI elements.

## Cons
- **Limited Storage Types**: While supporting System, Secure, and Global storage types, other storage types (like SharedPreferences) are not explicitly supported in the library.
- **Not Fully Automated**: Developers still need to specify storage type and system properties manually for each custom preference.
- **Requires Understanding of Broadcast Intents**: Broadcasting intents on preference changes may require additional configuration in certain app architectures.

## Developer Info
- **Developer**: `@darksky4you (Telegram)`

## Release Page
For the latest releases, check out the [Release Page](https://github.com/darksky4you/XdPreference/releases).
