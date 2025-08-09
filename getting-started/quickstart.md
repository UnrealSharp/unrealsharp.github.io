---
description: Get setup and running with your first project using UnrealSharp
icon: bullseye-arrow
---

# Setup

## Prerequisites <a href="#prerequisites" id="prerequisites"></a>

C++ Project (Highly recommended but not required. See warning under "**Compiling UnrealSharp**")

Unreal Engine 5.3 - 5.6

Install the [required build tools](https://dev.epicgames.com/documentation/en-us/unreal-engine/setting-up-visual-studio-development-environment-for-cplusplus-projects-in-unreal-engine) for Unreal Engine

Install [.NET 9.0 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/9.0)

## Clone UnrealSharp to your project <a href="#install-unrealsharp-to-your-project" id="install-unrealsharp-to-your-project"></a>

Clone [this ](https://github.com/UnrealSharp/UnrealSharp)repo and place **UnrealSharp** in the **ProjectRootDirectory/Plugins** folder (make the Plugins folder if it doesn’t exist) in your Unreal Engine project.

```
git clone https://github.com/UnrealSharp/UnrealSharp.git
```

## Generate Project Files

Right click on your project's **.uproject** file and generate project files

## Compiling UnrealSharp <a href="#compiling-unrealsharp" id="compiling-unrealsharp"></a>

Compile the plugin as any other Unreal Engine plugin using the IDE of your choice.

{% hint style="danger" %}
Avoid compiling the plugin by clicking on the .uproject file. It introduces several issues, such as outdated binaries even when the source code has changed, which complicates debugging and support.

If you do choose this option, you need to remove **Binaries/Intermediate** folders in the **project/UnrealSharp** folder, whenever you fetch a new version of the plugin from Git.
{% endhint %}

## Launching UnrealSharp <a href="#launching-unrealsharp" id="launching-unrealsharp"></a>

Launch your Unreal Engine project through the **solution file** or **.uproject**. Once Unreal Engine has fully opened, this prompt should appear:

<figure><img src="https://raw.githubusercontent.com/UnrealSharp/unrealsharp.github.io/main/media/get-started/NoProjectFoundPrompt.PNG" alt=""><figcaption></figcaption></figure>

Press **Yes** and the **Create C# Project** menu should appear like this:

<figure><img src="../.gitbook/assets/Screenshot 2025-08-03 205817.png" alt=""><figcaption></figcaption></figure>

You can choose a custom project name, and the project will be located in the **ProjectRootFolder/Script** directory. Subdirectories within Script are also supported, allowing you to organize your project files in any folder structure you prefer.

Owner is either a plugin or the project. UnrealSharp supports having C# code in a plugin.

{% hint style="info" %}
**By default it’ll create a new folder for each new project!**
{% endhint %}

## Quick Access to UnrealSharp’s editor features <a href="#quick-access-to-unrealsharps-editor-features" id="quick-access-to-unrealsharps-editor-features"></a>

If you lose track or need to start over, you can easily access the project setup feature again.

Navigate to the top of the editor viewport and you’ll find the **UnrealSharp** logo. Click on **New C# Project** and you’re back on track.

## Project Setup Completed <a href="#project-setup-completed" id="project-setup-completed"></a>

Once the project is created and the solution opens, you will see two projects in the Solution Explorer.

**ProjectName.Glue**: This project contains the automatically generated glue code that is related to your C++ API. It's part of the interop process, and it will be regenerated with each build that trigger UnrealHeaderTool.&#x20;

Therefore, do not modify or directly use this project. Any changes made here will be overwritten.

**Plugins:** Here any plugins within the project will reside. The glue for each plugin will be in **PluginRootFolder\Script\PluginName.Glue**

<figure><img src="../.gitbook/assets/Screenshot 2025-08-09 121710.png" alt=""><figcaption></figcaption></figure>
