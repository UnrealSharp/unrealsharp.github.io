---
description: Get setup and running with your first project using UnrealSharp
icon: bullseye-arrow
---

# Setup

## Prerequisites <a href="#prerequisites" id="prerequisites"></a>

Unreal Engine 5.6 - 5.8

Install the [required build tools](https://dev.epicgames.com/documentation/en-us/unreal-engine/setting-up-visual-studio-development-environment-for-cplusplus-projects-in-unreal-engine) for developing with C++ in UE5

C++ UE5 Project (Highly recommended but not required. See warning under "**Compiling UnrealSharp**")

Install [.NET 10.0 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/10.0) (10.0.5+)

## Clone UnrealSharp to your project <a href="#install-unrealsharp-to-your-project" id="install-unrealsharp-to-your-project"></a>

Clone [this ](https://github.com/UnrealSharp/UnrealSharp)repo and place **UnrealSharp** in the **ProjectRootDirectory/Plugins** folder (make the Plugins folder if it doesn’t exist) in your Unreal Engine project.

```
git clone https://github.com/UnrealSharp/UnrealSharp.git
```

## Compiling UnrealSharp <a href="#compiling-unrealsharp" id="compiling-unrealsharp"></a>

Compile the Unreal Engine project using the IDE of your choice. UnrealSharp will automatically generate bindings and compile them as part of the C++ build process.

{% hint style="danger" %}
Avoid compiling the plugin by clicking on the .uproject file. It introduces several issues, such as outdated binaries even when the source code has changed, which complicates debugging and support.

If you do choose this option, you need to remove **Binaries/Intermediate** folders in the **project/UnrealSharp** folder, whenever you fetch a new version of the plugin from Git.
{% endhint %}

## Launching UnrealSharp <a href="#launching-unrealsharp" id="launching-unrealsharp"></a>

Launch your Unreal Engine project through the **solution file** or **.uproject**. Once Unreal Engine has fully opened, this prompt should appear:

<figure><img src="https://raw.githubusercontent.com/UnrealSharp/unrealsharp.github.io/main/media/get-started/NoProjectFoundPrompt.PNG" alt=""><figcaption></figcaption></figure>

Press **Yes** and the **Create C# Project** menu should appear like this:

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

The C# solution should open when the project has been created, and now you're all set to start coding with UnrealSharp!

## Quick Access to UnrealSharp’s editor features <a href="#quick-access-to-unrealsharps-editor-features" id="quick-access-to-unrealsharps-editor-features"></a>

If you lose track or need to start over, you can easily access the project setup feature again.

Navigate to the top of the editor viewport and you’ll find the **UnrealSharp** logo. Click on **New C# Project** and you’re back on track.
