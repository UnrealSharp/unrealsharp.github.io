# Cheats / Debug Commands

To add cheats or debug commands that can be executed from the in-game console, create a cheat manager extension class.

Example:

```csharp
[UClass]
public partial class UMyCheatManagerExtension : UCSCheatManagerExtension
{
    [UFunction(FunctionFlags.Exec)]
    public void KillAllEnemies()
    {
        // Your cheat logic here
    }
}
```

Any method marked with `FunctionFlags.Exec` will automatically be exposed as a console command.

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
