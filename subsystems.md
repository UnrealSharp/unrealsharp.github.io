---
title: Subsystems
layout: default
---

# Subsystems

UnrealSharp supports any of the engine's [subsytem](https://docs.unrealengine.com/4.27/en-US/ProgrammingAndScripting/Subsystems/) classes. These classes are great way to create singletons in Unreal Engine. 

The only difference is that you need to inherit from the CS wrapper, due to the lack of reflection exposed functions in the engine's subsystem classes.

UWorldSubsystem => CSWorldSubsystem
UGameInstaceSubsystem => CSGameInstanceSubsystem
UEngineSubsystem => CSEngineSubsystem
ULocalPlayerPlayerSubsystem => CSLocalPlayerSubsystem

## Example

UWorldSubsystem in UnrealSharp:

```c#
public class WorldSubsystemExample : CSWorldSubsystem
{
    protected override void PostInitialize()
    {
        base.PostInitialize();
    }

    protected override void Deinitialize()
    {
        base.Deinitialize();
    }

    protected override void Initialize()
    {
        base.Initialize();
    }

    protected override bool ShouldCreateSubsystem()
    {
        return base.ShouldCreateSubsystem();
    }

    protected override void OnWorldBeginPlay()
    {
        base.OnWorldBeginPlay();
    }
}
```

## Getting Subsystems

Getting the subsystems are really simple, you just do any of the following, depending on what type of subsystem you inherit from:

```c#
GetWorldSubsystem<MyWorldSubsystem>();
GetGameInstanceSubsystem<MyGameInstanceSubsystem>();
GetLocalPlayerSubsystem<MyLocalPlayerSubsystem>(OwningPlayerController);
GetEngineSubsystem<MyEngineSubsystem>();
```