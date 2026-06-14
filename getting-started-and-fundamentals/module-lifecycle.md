---
icon: heart
---

# Module Lifecycle

In C#, similar to C++, you can define a class to represent your module. These module classes are automatically generated when you create a new module using the UnrealSharp toolbar in the editor.

If your module was created before this feature was available and doesn’t have a module class, you can simply define it manually anywhere in your module. To do this, create a new class and implement the `IModuleInterface`.

Here’s an example of how a module class might look:

```csharp
using UnrealSharp.Engine.Core.Modules;

namespace ModuleShowcase;

[UModule]
public class FModuleShowcase : IModuleInterface
{
    // Called when opening the engine or reloading an assembly during hot reload
    public void StartupModule()
    {
    }

    // Called when the engine is closing or reloading an assembly during hot reload
    public void ShutdownModule()
    {
    }
}
```

`StartupModule` and `ShutdownModule` get called when you start or close the editor, and also during hot reloads. When hot reloading, the old assembly gets unloaded, and the new one is loaded, so these methods handle setting things up and cleaning up as needed.

### Module API

You can get the module anywhere by calling this:

```csharp
FMyModule MyModule = PluginLoader.FindModule<FMyModule>();
```
