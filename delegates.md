---
title: Delegates
layout: default
nav_order: 5
---
# Delegates

**This is only for delegates exposed to Unreal Engine through UFunction/UProperty**

## Delegate Declaration

When exposing delegates to Unreal Engine, some additional steps are required compared to standard C#.

Delegates exposed to Unreal Engine needs to have parameters that are supported by reflection.

```c#
// Multicast delegates.
public delegate void MyShowcaseMulticastDelegate(int a);

// Single delegates. They need the USingleAttribute for UnrealSharp to generate the correct glue to communicate with C++.
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
    public TMulticastDelegate<MyShowcaseMulticastDelegate> TestDelegate { get; set; }
    
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
        // Subscribe to the delegate with a callback
        TestDelegate += MyCallback;
        
        // Invoke the delegate
        TestDelegate.Invoke(1337);

        // Check if the delegate contains the callback
        if (TestDelegate.Contains(MyCallback))
        {
            PrintString("Delegate contains MyCallback");
        }
        
        // Unsubscribe from the delegate
        TestDelegate -= MyCallback;

        base.BeginPlay();
    }
    
    // A callback to an Unreal Engine exposed delegate must be a UFunction.
    [UFunction]
    public void MyCallback(int a)
    {
        PrintString($"MyCallback invoked with {a}");
    }
```











