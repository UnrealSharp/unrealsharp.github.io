# Async

This plugin also supports the abilty to expose latent actions to Blueprint. To do so, just return a `Task` like you normally would. However, when you do the `await` statement, at the end, call the extension method `ConfigureWithUnrealContext()`. This makes sure that all parts of the operation will run on the correct thread. You can also use a cancellation token if you want. Simply add it as a parameter.

The method signature must be `public` and it supports returning `Task` or `Task<T>` where `T` is any type that is supported as a UFunction parameter.

```csharp
[UClass]
public partial class AAsyncActor : AActor
{
    // Cancellation token is optional.
    [UFunction(FunctionFlags.BlueprintCallable)]
    public async Task<int> SlowAdd(int lhs, int rhs, CancellationToken cancellationToken)
    {
        PrintString($"Commencing the world's slowest addition...");

        await Task.Delay(1000, cancellationToken).ConfigureWithUnrealContext();
        if (cancellationToken.IsCancellationRequested || IsDestroyed) { return default; }

        int result = lhs + rhs;
        PrintString($"{lhs} + {rhs} = {result}!");

        return result;
    }
}
```

The code above will generate a node like this in Blueprint:

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
