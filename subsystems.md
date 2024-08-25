---
title: Subsystems
layout: default
---

# Subsystems

UnrealSharp supports any of the engine's [subsytem](https://docs.unrealengine.com/4.27/en-US/ProgrammingAndScripting/Subsystems/) classes. These classes are great way to create singletons in Unreal Engine. 

## Subsystem names in UnrealSharp

The only difference is that you need to inherit from the CS wrapper, due to the lack of reflection exposed functions in the engine's subsystem classes.

```c#
// This WorldSubsystem supports Tick aswell. UTickableWorldSubsystem doesn't exist in UnrealSharp.
UWorldSubsystem => UCSWorldSubsystem

UGameInstanceSubsystem => UCSGameInstanceSubsystem

UEngineSubsystem => UCSEngineSubsystem

ULocalPlayerSubsystem => UCSLocalPlayerSubsystem
```

## Getting Subsystems

Getting the subsystems are really simple, you just do any of the following, depending on what type of subsystem you inherit from:

```c#
GetWorldSubsystem<UMyWorldSubsystem>();
GetGameInstanceSubsystem<UMyGameInstanceSubsystem>();
GetLocalPlayerSubsystem<UMyLocalPlayerSubsystem>(OwningPlayerController);
GetEngineSubsystem<UMyEngineSubsystem>();
```

