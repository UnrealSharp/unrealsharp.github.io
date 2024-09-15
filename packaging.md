---
title: Packaging
layout: default
---
# Packaging 

## Package Your Game

**Currently only Windows/Mac is supported**

Begin by packaging your game as you would normally in Unreal Engine. Ensure you select the correct platform (Windows) and configurations for your game. This initial step does not differ from the standard game packaging procedure in Unreal Engine.

## Packaging via Unreal Editor

You can easily package your C# project and runtime directly through the Unreal Editor. Follow these steps:

### Open the Packaging Tool

In the editor, navigate to the **UnrealSharp** toolbar located at the top of the viewport, and click on **Package Project**.

![PackageProject](https://raw.githubusercontent.com/UnrealSharp/unrealsharp.github.io/main/media/get-started/PackageProject.PNG)

A file explorer dialog will appear, prompting you to choose the directory where your project will be packaged. Select the **root folder** of your packaged project. This is the folder containing your **.exe** file.

After selecting the correct folder, you should see the packaging process start.

![PackagingProcess](https://raw.githubusercontent.com/UnrealSharp/unrealsharp.github.io/main/media/get-started/PackagingProjectPrompt.PNG)

Once the prompt disappears, the packaging is complete, and your game is ready to be launched.

## Packaging via Command Prompt

Open **Command Prompt** or **PowerShell** window and navigate to ```UnrealSharp\Binaries\Managed```

## Package Project Script

```dotnet UnrealSharpBuildTool.dll --Action PackageProject --ProjectDirectory "<YourProjectDirectory>" --ProjectName "<YourProjectName>" --PluginDirectory "<YourPluginDirectory>" --ArchiveDirectory "<YourArchiveDirectory>" --AdditionalArgs BuildConfig=Release```

**--Action:** The action you want UnrealSharpBuildTool to run.

**--ProjectDirectory:** The path to your project root directory (where .uproject resides).

**--ProjectName:** The name of your Unreal Engine project

**--PluginDirectory:** The path to the directory where the UnrealSharp plugin is installed within your project or engine.

**--ArchiveDirectory:** The root directory for where the packaged game is archived.

### Example Usage:
If your project is named "MyGame" and is located at ```C:/Users/CoolName/Documents/Unreal Projects/MyGame```, with the UnrealSharp plugin in the project's "Plugins" folder and you want to archive the packaged game to the desktop, your command would look like this:

```dotnet UnrealSharpBuildTool.dll --Action PackageProject --ProjectDirectory "C:/Users/CoolName/Documents/Unreal Projects/MyGame/" --ProjectName "MyGame" --PluginDirectory "C:/Users/CoolName/Documents/Unreal Projects/MyGame/Plugins/UnrealSharp" --ArchiveDirectory "C:/Users/CoolName/Desktop/Windows" --AdditionalArgs BuildConfig=Release```

## Done and dusted!

Now the ```MyProjectName\Binaries\Managed``` folder in your packaged game should be populated and the game is ready to run.

