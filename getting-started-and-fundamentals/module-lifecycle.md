---
icon: heart
---

# Module Lifecycle

In C#, similar to C++, you can define a class to represent your module. These module classes are automatically generated when you create a new module using the UnrealSharp toolbar in the editor.

Here’s an example of how a module class might look:

```csharp
using UnrealSharp.Engine.Core.Modules;

namespace ModuleShowcase;

[UModule]
public class FMyModule : IModuleInterface
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
