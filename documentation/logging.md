# Logging

**Enable Custom Logs**

Need to include this assembly in your csproj:

```
<Reference Include="UnrealSharp">
  <HintPath>..\..\Plugins\UnrealSharp\Binaries\Managed\net9.0\UnrealSharp.Logging.dll</HintPath>
</Reference>
```

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

Here’s an example of how to log with your custom categories:

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

And they will show up like this in the output log in the engine:

```
LogMyFirstLog: Display: ALogShowcase constructor executed
LogMyFirstLog: Display: BeginPlay executed
```
