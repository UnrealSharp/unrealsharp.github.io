---
title: Packaging
layout: default
---


## Package Your Game

**Currently only Windows is supported**

Begin by packaging your game as you would normally in Unreal Engine. Ensure you select the correct platform (Windows) and configurations for your game. This initial step does not differ from the standard game packaging procedure in Unreal Engine.

## Run the UnrealSharp Packaging Script

After packaging your game, you will need to execute a script to include the C# code and the .NET runtime into your packaged game.

Open **Command Prompt** or **PowerShell** window and navigate to ```UnrealSharp\Binaries\Managed```

## Publish Script
```dotnet UnrealSharpBuildTool.dll --Action Publish --ProjectDirectory "<YourProjectDirectory>" --ProjectName "<YourProjectName>" --PluginDirectory "<YourPluginDirectory>" --ArchiveDirectory "<YourArchiveDirectory>"```

**--Action:** The action you want UnrealSharpBuildTool to run.

**--ProjectDirectory:** The path to your project root directory (where .uproject resides).

**--ProjectName:** The name of your Unreal Engine project

**--PluginDirectory:** The path to the directory where the UnrealSharp plugin is installed within your project or engine.

**--ArchiveDirectory:** The root directory for where the packaged game is archived.

### Example Usage:
If your project is named "MyGame" and is located at ```C:/Users/CoolName/Documents/Unreal Projects/MyGame```, with the UnrealSharp plugin in the project's "Plugins" folder and you want to archive the packaged game to the desktop, your command would look like this:

```dotnet UnrealSharpBuildTool.dll --Action Publish --ProjectDirectory "C:/Users/CoolName/Documents/Unreal Projects/MyGame/" --ProjectName "MyGame" --PluginDirectory "C:/Users/CoolName/Documents/Unreal Projects/MyGame/Plugins/UnrealSharp" --ArchiveDirectory "C:/Users/CoolName/Desktop/Windows"```

## Done and dusted!

Now the ```MyProjectName\Binaries\Managed``` folder in your packaged game should be populated and the game is ready to run.

