---
title: Delegates
layout: default
nav_order: 7
---
# Delegates

**This is only for C# delegates you want to expose to Unreal Engine through UFunction/UProperty.**

## Delegate Declaration

When exposing delegates to Unreal Engine, some additional steps are required compared to standard C#.

Delegates exposed to Unreal Engine needs to have parameters that are supported by reflection.

```c#
// Delegates need the attribute to generate the correct glue for the type.

// Multicast delegates.
[UMultiDelegate]
public delegate void MyShowcaseMulticastDelegate(int a);

// Single delegates.
[USingleDelegate]
public delegate void MyShowcaseDelegate(int a);
```

## Class Member Declaration

In UnrealSharp, delegates can be exposed as class members in the following ways:

```c#
[UClass]
public class ADelegateShowcaseClass : AActor
{
    [UProperty(PropertyFlags.BlueprintAssignable)]
    public TMulticastDelegate<MyShowcaseMulticastDelegate> MyMulticastDelegate { get; set; }
    
    [UFunction(FunctionFlags.BlueprintCallable)]
    public void MyFunctionWithCallback(TDelegate<MyShowcaseDelegate> singleDelegate)
    {
        
    }

    // Single delegates as properties can't be Blueprint exposed, but reflection exposed. Unreal Engine limitation.
    [UProperty]
    TDelegate<MyShowcaseDelegate> MySingleDelegate { get; set; }
}
```

## Delegate API Example

Delegates exposed to Unreal Engine follow the same syntax as standard C# delegates, with some additional features.

```c#
    protected override void BeginPlay()
    {
        // Subscribe with a lambda. Must have a UFunction attribute
        MyMulticastDelegate += [UFunction](int a) =>
        {
            PrintString($"MyCallback invoked with {a}");
        };

        // Subscribe to the delegate with a callback
        MyMulticastDelegate += MyFunctionCallback;
        
        // Invoke the delegate
        MyMulticastDelegate.Invoke(1337);

        // Check if the delegate contains the callback
        if (MyMulticastDelegate.Contains(MyCallback))
        {
            PrintString("Delegate contains MyCallback");
        }
        
        // Unsubscribe from the delegate
        MyMulticastDelegate -= MyCallback;

        base.BeginPlay();
    }
    
    // A callback to an Unreal Engine exposed delegate must be a UFunction.
    [UFunction]
    public void MyFunctionCallback(int a)
    {
        PrintString($"MyCallback invoked with {a}");
    }
```











