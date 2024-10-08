---
title: Async
layout: default
nav_order: 9
---

# Async

This plugin also supports the abilty to expose latent actions to Blueprint. To do so, just return a `Task` like you normally would. However, when you do the `await` statement, at the end, call the extension method `ConfigureWithUnrealContext()`. This makes sure that all parts of the operation will run on the correct thread. You can also use a cancellation token if you want. Simply add it as a parameter.

The method signature must be `public` and it supports returning `Task` or `Task<T>` where `T` is any type that is supported as a UFunction parameter.

```c#
[UClass]
public class AAsyncActor : AActor
{

    // here we have a cancellation token
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