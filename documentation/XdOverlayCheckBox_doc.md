
# **XdOverlayCheckBox**

## **Overview**
`XdOverlayCheckBox` is a custom checkbox component designed for Android settings or preferences. It is used to enable or disable overlay packages, supporting both single and multiple overlays. This component provides options to debug errors, manage overlays efficiently, and optionally trigger intents.

## **Features**
- **Multiple overlays support**: Use one or more overlay packages for turning on/off.
- **Debug logging**: Optionally log debug information to assist with troubleshooting.
- **Customizable intent**: Trigger custom intents when the checkbox state changes.
- **Easy integration**: Simple to use within preference or settings XML.

---
## Changelog

`12 Aug 2025`
* Improvement in the logic.

## **Attributes**

The `XdOverlayCheckBox` component supports the following attributes:

### 1. **`android:entries`** (`String[]`)

- **Description**: Specifies the list of overlay package names.
- **Usage**: You should provide an array resource containing the names of the overlay packages you wish to use when `multiOverlays` is set to `true`.
- **Example**: 
  ```xml
  android:entries="@array/monet_overlay_packages"
  ```

### 2. **`android:title`** (`String`)

- **Description**: The title displayed next to the checkbox.
- **Usage**: Provide a user-friendly title for the checkbox that describes its purpose.
- **Example**:
  ```xml
  android:title="Overlay Test"
  ```

### 3. **`android:key`** (`String`)

- **Description**: The key used to store and retrieve the preference value.
- **Usage**: A unique string that identifies the checkbox preference.
- **Example**:
  ```xml
  android:key="system_monet_overlay"
  ```

### 4. **`android:defaultValue`** (`Boolean`)

- **Description**: The default value of the checkbox when first initialized.
- **Usage**: Set this to `"true"` or `"false"`, depending on whether you want the checkbox checked or unchecked by default.
- **Example**:
  ```xml
  android:defaultValue="true"
  ```

### 5. **`multiOverlays`** (`Boolean`)

- **Description**: Defines whether multiple overlays can be applied.
- **Default**: `false`
- **Usage**: Set this attribute to `true` to support multiple overlays. If using a **single overlay**, do not use this attribute and place the package name directly in the `key` attribute.
- **Example**:
  ```xml
  multiOverlays="true"
  ```

### 6. **`debug`** (`Boolean`)

- **Description**: Enables debug logging for troubleshooting purposes.
- **Default**: `false`
- **Usage**: Set to `true` if you're encountering issues, and you want to log more detailed error messages.
- **Example**:
  ```xml
  debug="false"
  ```

### 7. **`intent`** (`String`)

- **Description**: An optional intent to be triggered when the checkbox is clicked.
- **Usage**: If you need to perform an action when the checkbox state changes, such as launching another activity or performing a system-level action, you can specify the intent here.
- **Example**:
  ```xml
  intent="com.example.overlay_action"
  ```

---

## **Usage Guidelines**

### **1. Multiple Overlays Configuration**
To use multiple overlay packages, reference the overlay package names in an array and set the `multiOverlays` attribute to `true`. This allows for applying multiple overlays.

```xml
<XdOverlayCheckBox
    android:entries="@array/monet_overlay_packages"
    android:title="Overlay Test"
    android:key="system_monet_overlay"
    android:defaultValue="true"
    multiOverlays="true"
    debug="false"
    intent=""/>
```

- **`android:entries`**: Contains a list of overlay package names (defined in `@array/monet_overlay_packages`).
- **`multiOverlays`**: Set to `true` to enable multiple overlays.

### **2. Single Overlay Configuration**
For a single overlay, you can simply set the overlay package name in the `android:key` attribute and omit the `multiOverlays` attribute.

```xml
<XdOverlayCheckBox
    android:title="Single Overlay Test"
    android:key="com.example.single_overlay"
    android:defaultValue="true"
    debug="false"
/>
```

- **`android:key`**: Directly provides the overlay package name.

---

## **Important Notes**

- **Static Overlays**: Ensure that the overlay packages are **not static**. Static overlays may not be compatible with the `XdOverlayCheckBox` component.
  
- **Debug Mode**: If you encounter issues with the overlays, enable the `debug` mode by setting it to `true`. This will allow you to view logs for more detailed error information.

- **Intent**: The `intent` attribute allows you to specify an action that should be triggered when the checkbox state is changed, such as launching an activity or performing a system-level task.

---

## **Example Array (monet_overlay_packages)**

When using multiple overlays, you must define the overlay package names in an array resource.

### `res/values/arrays.xml`

```xml
<resources>
    <string-array name="monet_overlay_packages">
        <item>com.example.overlay1</item>
        <item>com.example.overlay2</item>
        <item>com.example.overlay3</item>
    </string-array>
</resources>
```

This array can then be referenced in your `XdOverlayCheckBox` component via the `android:entries` attribute.

---

## **Example Use Cases**

### **Use Case 1: Multiple Overlays**

```xml
<XdOverlayCheckBox
    android:entries="@array/monet_overlay_packages"
    android:title="Overlay Test"
    android:key="system_monet_overlay"
    android:defaultValue="true"
    multiOverlays="true"
/>
```

### **Use Case 2: Single Overlay**

```xml
<XdOverlayCheckBox
    android:title="Single Overlay Test"
    android:key="com.example.single_overlay"
    android:defaultValue="true"
    debug="false"
/>
```

---

## **Conclusion**
The `XdOverlayCheckBox` component provides a flexible and customizable way to manage overlay preferences in Android. By supporting both multiple and single overlays, offering debug logging, and providing the ability to trigger custom intents, it simplifies overlay management for developers.

For more information, refer to the XML attributes and usage examples above to integrate this component into your Android project.



## License
This project is created and maintained by `@darksky4you`. Feel free to modify and use it in your projects.

