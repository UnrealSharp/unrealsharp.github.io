# Subsystems

UnrealSharp supports any of the engine’s subsytem classes. These classes are great way to create singletons in Unreal Engine.

They get automatically instanced and the engine will manage its lifetime. They don't support replication though.

#### Su~~b~~system names in UnrealSharp <a href="#subsystem-names-in-unrealsharp" id="subsystem-names-in-unrealsharp"></a>

The only difference is that you need to inherit from the CS wrapper, due to the lack of reflection exposed functions in the engine’s subsystem classes.

```csharp
// This WorldSubsystem supports Tick aswell. UTickableWorldSubsystem doesn't exist in UnrealSharp.
UWorldSubsystem => UCSWorldSubsystem

UGameInstanceSubsystem => UCSGameInstanceSubsystem

UEngineSubsystem => UCSEngineSubsystem

ULocalPlayerSubsystem => UCSLocalPlayerSubsystem
```

#### Getting Subsystems <a href="#getting-subsystems" id="getting-subsystems"></a>

Getting the subsystems are really simple, you just do any of the following, depending on what type of subsystem you inherit from:

```csharp
GetWorldSubsystem<UMyWorldSubsystem>();
GetGameInstanceSubsystem<UMyGameInstanceSubsystem>();
GetLocalPlayerSubsystem<UMyLocalPlayerSubsystem>(OwningPlayerController);
GetEngineSubsystem<UMyEngineSubsystem>();
```

#### World Subsystem Example

```csharp
[UClass]
public partial class UMyWorldSubsystem : UCSWorldSubsystem
{
    public override bool DoesSupportWorldType(ECSWorldType worldType)
    {
        return worldType == ECSWorldType.Game || worldType == ECSWorldType.PIE;
    }

    public override void Initialize(FSubsystemCollectionBaseRef collection)
    {
        
    }

    public override void OnWorldBeginPlay()
    {
        
    }
}
```
