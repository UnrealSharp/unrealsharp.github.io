# Logging

**Define Custom Log Categories**

The `[CustomLog]` attribute is used on a `partial` (and preferably `static`) class to define a custom log category, for the Unreal Engine output log.&#x20;

The category's API will then generate automatically with methods such as `Log` / `LogWarning` / `LogError` / `LogFatal`.

```csharp
[CustomLog]
public static partial class LogMyFirstLog;

[CustomLog(ELogVerbosity.Verbose)]
public static partial class LogMySecondLog;
```

* **`LogMyFirstLog`**: Defaults to `ELogVerbosity.Display` when no verbosity is specified.
* **`LogMySecondLog`**: Explicitly uses `ELogVerbosity.Verbose`.

***

**Use the Log Categories**

Here’s an example of how to integrate your custom log categories into an actor:

```csharp
[UClass]
public class ALogShowcase : AActor
{
    public ALogShowcase()
    {
        LogMyFirstLog.Log("ALogShowcase constructor executed");
    }

    protected override void BeginPlay()
    {
        LogMyFirstLog.Log("BeginPlay executed");
        base.BeginPlay();
    }
}
```
