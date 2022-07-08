# Setup for IntelliJ IDEA

## Install
```bash
# Windows
winget install --id JetBrains.IntelliJIDEA.Community
```

## Sync Settings
* *File | Manage IDE Settings | Sync Settings to JetBrains Account* (For Ultimate Edition)
* *File | Manage IDE Settings | Settings Repository...* (For Community Edition) 

## Preferences
* *Preferences | Appearance & Behavior | System Settings*
  * Startup/Shutdown | Reopen last project on startup: ❎
* *Preferences | Editor | Font*
  * Font: Cascadia Code
* *Preferences | Editor | Color Scheme | Color Scheme Font*
  * Scheme: Material Oceanic
  * Use color scheme font instead of the default: ❎

## Custom VM Options
Increase memory for the following custom VM options (*Help > Edit Custom VM Options...*)
```
-Xms4g
-Xmx6g
-XX:ReservedCodeCacheSize=1g
```

## Keymap
Add new Keymap file to `~/Library/Application Support/JetBrains/<product><version>/keymaps
`:

```xml
<keymap version="1" name="_Personal" parent="Mac OS X 10.5+">
  <action id="SearchEverywhere">
    <keyboard-shortcut first-keystroke="shift meta p" />
  </action>
</keymap>
```

## Plugins

### Languages
* [Go](https://plugins.jetbrains.com/plugin/9568-go) *Requires Ultimate Edition
* [HOCON](https://plugins.jetbrains.com/plugin/10481-hocon)
* [Kotlin](https://plugins.jetbrains.com/plugin/6954-kotlin)
* [Markdown](https://plugins.jetbrains.com/plugin/7793-markdown/)
* [Scala](https://plugins.jetbrains.com/plugin/1347-scala)
* [Terraform](https://plugins.jetbrains.com/plugin/7808-hashicorp-terraform--hcl-language-support)
  * *Preferences | Editor | Code Style | Terraform Config*
    * Other | Formatting Options | Align properties: On equals
* [TOML](https://plugins.jetbrains.com/plugin/8195-toml/)

### Tools
* [Grep Console](https://plugins.jetbrains.com/plugin/7125-grep-console)
* [String Manipulation](https://plugins.jetbrains.com/plugin/2162-string-manipulation)

### Visual
* [Atom Material Icons](https://plugins.jetbrains.com/plugin/10044-atom-material-icons)
* [Material Theme UI](https://plugins.jetbrains.com/plugin/8006-material-theme-ui)
  * *Preferences | Appearance & Behavior | Material Theme*:
    * Main Settings | Selected Theme: Arc Dark
    * Main Settings | Contrast Mode: ✅
    * Main Settings | High Contrast: ✅
    * Advanced Settings | Features | Material Fonts: ✅
