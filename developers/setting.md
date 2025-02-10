---
order: 99
---

# Extension Settings

1. When the extension is activated, the main app injects the settings into the extension and override the defaultSettings by using the following function:

```kt
fun init(prefSettings: PrefSettings, httpHelper: HttpHelper) {
    // Initialization logic
}
```

2. Define defaultSettings and Display them in the Main App
To ensure that your extension has default settings and that they appear in the Extension Settings section of the main app, follow these steps:

- Define Default Settings
Implement default values for your extension settings within the extension itself.

- Expose Settings to the Main App
The main app will automatically detect and display these settings in the Extension Settings UI.

```kt
  override val defaultSettings: List<Setting> = listOf(
    SettingMultipleChoice(
      "Providers",
      "active_providers_key",
      "Select Provider to Enable",
      entryTitles = listOf("website1", "website2", "website3", "website4"),
      entryValues = listOf("website1", "website2", "website3", "website4"),
      defaultEntryIndices = setOf(0,1,2,3)
    ),
  )

```
![Exntesion Settings in the main App](/statics/extension-setting.png)--

3. The main app and extensions interact with `SharedPreferences` using the following interface:  
```kt
interface PrefSettings {
  fun getString(key: String): String?
  fun putString(key: String, value: String?)
  fun getStringSet(key: String): Set<String>?
  fun putStringSet(key: String, value: Set<String>?)
  fun getInt(key: String): Int?
  fun putInt(key: String, value: Int?)
  fun getBoolean(key: String): Boolean?
  fun putBoolean(key: String, value: Boolean?)
  fun getLong(key: String): Long?
  fun putLong(key: String, value: Long?)
}

```


