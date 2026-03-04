# Change Script Directory Name

By default, C# projects is in `ProjectOrPluginRoot/Script`. To customize this, create a `UnrealSharp.Settings.json` file in `ProjectRoot/Config` folder and add the following:

```json
{
  "ScriptDirectoryName": "MyCustomScriptDirectoryName"
}
```

These project-level settings will automatically override the global defaults located in `UnrealSharp/Config/UnrealSharp.Settings.json`.

Make sure to delete `UnrealSharp/Intermediate` for a clean rebuild after changing these settings.

