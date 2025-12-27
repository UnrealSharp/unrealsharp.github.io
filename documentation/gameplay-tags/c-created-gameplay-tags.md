# C# Created Gameplay Tags

#### Define Tags

Create a static class to store your tags.

```csharp
public static class IslandGenTags
{
    public static readonly FGameplayTag IslandGen_Island = new FGameplayTag("IslandGen.Island", "Optional Comment");
}
```

#### Tags Registration

{% hint style="danger" %}
Due to initialization timing, these tags are not found in the global `GameplayTags` static class. You must store the returned `FGameplayTag` in your own static field for later use.
{% endhint %}

To ensure tags are available before the editor or other systems attempt to access them, register them early, ideally within your module's `StartupModule`.

```csharp
public class FIslandGen : IModuleInterface
{
    public void StartupModule()
    {
        // Runs the static constructor and registers the gameplay tags
        RuntimeHelpers.RunClassConstructor(typeof(IslandGenTags).TypeHandle);
    }

    public void ShutdownModule()
    {
    }
}
```

