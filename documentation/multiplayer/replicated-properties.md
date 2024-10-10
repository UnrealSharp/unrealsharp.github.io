---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Replicated Properties

Replicated properties are variables whose values are automatically synchronized across the network, from the server to all clients. UnrealSharp allows you to easily define which properties should be replicated and under what conditions.

## Declaring Replicated Properties <a href="#declaring-replicated-properties" id="declaring-replicated-properties"></a>

To declare a property as replicated, annotate it with the \[UProperty] attribute and set the PropertyFlags.Replicated flag:

```csharp
[UProperty(PropertyFlags.Replicated)]
public int MyReplicatedInteger { get; set; }
```

## Using OnRep Functions <a href="#using-onrep-functions" id="using-onrep-functions"></a>

For more control over replication, you can specify a callback function that the multiplayer system will call when a replicated property changes. This is particularly useful for updating game state or UI in response to property changes.

```csharp
[UProperty(ReplicatedUsing = nameof(OnRep_MyReplicatedBool))]
public bool MyReplicatedBool { get; set; }

[UFunction]
void OnRep_MyReplicatedBool()
{
    PrintString($"MyReplicatedBool has been updated to {MyReplicatedBool}");
}
```

## OnRep Function with Old Value <a href="#onrep-function-with-old-value" id="onrep-function-with-old-value"></a>

If you need to know the previous value of a property, you can define an OnRep function that takes the old value as a parameter:

```csharp
[UFunction]
void OnRep_MyReplicatedBoolWithOldValue(bool oldValue)
{
    PrintString($"MyReplicatedBool has been updated from {oldValue} to {MyReplicatedBool}");
}
```

## Lifetime Conditions <a href="#lifetime-conditions" id="lifetime-conditions"></a>

Sometimes, you might want to replicate a property only under specific conditions, such as only to the owning player. You can achieve this by specifying a LifetimeCondition:

```csharp
[UProperty(PropertyFlags.Replicated, LifetimeCondition = LifetimeCondition.OwnerOnly)]
public string MyReplicatedString { get; set; }
```

