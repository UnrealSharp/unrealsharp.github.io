# Delegates

## Delegate Declaration <a href="#delegate-declaration" id="delegate-declaration"></a>

When exposing delegates to Unreal Engine, some additional steps are required compared to standard C#.

Delegates exposed to Unreal Engine needs to have parameters that are supported by reflection.

{% code fullWidth="false" %}
```csharp
// Delegates need the attribute to generate the correct glue for the type.

// Multicast delegates.
[UMultiDelegate]
public delegate void FMyShowcaseMulticastDelegate(int a);

// Single delegates.
[USingleDelegate]
public delegate void FMyShowcaseDelegate(int a);
```
{% endcode %}

## Class Member Declaration <a href="#class-member-declaration" id="class-member-declaration"></a>

Delegates can be exposed as class members in the following ways:

{% code fullWidth="false" %}
```csharp
[UClass]
public class ADelegateShowcaseClass : AActor
{
    [UProperty(PropertyFlags.BlueprintAssignable)]
    public partial TMulticastDelegate<FMyShowcaseMulticastDelegate> MyMulticastDelegate { get; set; }
    
    [UFunction(FunctionFlags.BlueprintCallable)]
    public void MyFunctionWithCallback(TDelegate<MyShowcaseDelegate> singleDelegate)
    {
        
    }

    // Single delegates as properties can't be Blueprint exposed, but reflection exposed. Unreal Engine limitation.
    [UProperty]
    public partial TDelegate<FMyShowcaseDelegate> MySingleDelegate { get; set; }
}
```
{% endcode %}

## Delegate API Example <a href="#delegate-api-example" id="delegate-api-example"></a>

Delegates exposed to Unreal Engine follow the same syntax as standard C# delegates, with some additional features.

```csharp
public override void BeginPlay()
{
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
