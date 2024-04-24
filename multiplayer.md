---
title: Multiplayer
layout: default
---
UnrealSharp simplifies multiplayer in Unreal Engine by providing an intuitive way to declare and manage replicated properties and remote procedure calls (RPCs).

## Replicated Properties

Replicated properties are variables whose values are automatically synchronized across the network, from the server to all clients. UnrealSharp allows you to easily define which properties should be replicated and under what conditions.

### Declaring Replicated Properties

To declare a property as replicated, annotate it with the [UProperty] attribute and set the PropertyFlags.Replicated flag:

```c#
[UProperty(PropertyFlags.Replicated)]
public int MyReplicatedInteger { get; set; }
```
### Using OnRep Functions

For more control over replication, you can specify a callback function that the multiplayer system will call when a replicated property changes. This is particularly useful for updating game state or UI in response to property changes.

```c#
[UProperty(ReplicatedUsing = nameof(OnRep_MyReplicatedBool))]
public bool MyReplicatedBool { get; set; }

[UFunction]
void OnRep_MyReplicatedBool()
{
    PrintString($"MyReplicatedBool has been updated to {MyReplicatedBool}");
}
```
### OnRep Function with Old Value

If you need to know the previous value of a property, you can define an OnRep function that takes the old value as a parameter:

```c#
[UFunction]
void OnRep_MyReplicatedBoolWithOldValue(bool oldValue)
{
    PrintString($"MyReplicatedBool has been updated from {oldValue} to {MyReplicatedBool}");
}
```

### Lifetime Conditions

Sometimes, you might want to replicate a property only under specific conditions, such as only to the owning player. You can achieve this by specifying a LifetimeCondition:

```c#
[UProperty(PropertyFlags.Replicated, LifetimeCondition = LifetimeCondition.OwnerOnly)]
public string MyReplicatedString { get; set; }
```

## RPCs (Remote Procedure Calls)

RPCs allow you to invoke functions across the network, enabling communication between the server and clients. These examples are parameterless, but of course they can contain parameters.

**If you want a RPC to be unreliable, just don't declare FunctionFlags.Reliable**

### Run on Server

Use the **[UFunction]** attribute with FunctionFlags.RunOnServer to indicate that a method should be executed on the server:

```c#
[UFunction(FunctionFlags.RunOnServer | FunctionFlags.Reliable)]
public void ServerFunction()
{
    // Server-side code
}
```

### Run on Owning Client

Similarly, to execute a function on the owning client, use FunctionFlags.RunOnClient:

```c#
[UFunction(FunctionFlags.RunOnClient | FunctionFlags.Reliable)]
public void ClientFunction()
{
    // Client-side code
}
```

### Multicast

For functions that should be executed on both the server and all clients, use FunctionFlags.Multicast:

```c#
[UFunction(FunctionFlags.Multicast | FunctionFlags.Reliable)]
public void MulticastFunction()
{
    // Code executed on both server and clients
}
```