---
description: >-
  RPCs allow you to invoke functions across the network, enabling communication
  between the server and clients. These examples are parameterless, but of
  course they can contain parameters.
---

# RPCs (Remote Procedure Calls)

{% hint style="info" %}
_**If you want a RPC to be unreliable, just don’t declare FunctionFlags.Reliable**_
{% endhint %}

## Run on Server <a href="#run-on-server" id="run-on-server"></a>

Use the **\[UFunction]** attribute with FunctionFlags.RunOnServer to indicate that a method should be executed on the server:

```csharp
[UFunction(FunctionFlags.RunOnServer | FunctionFlags.Reliable)]
public partial void ServerFunction();
public partial void ServerFunction_Implementation();
{
    // Server-side code
}
```

## Run on Owning Client <a href="#run-on-owning-client" id="run-on-owning-client"></a>

Similarly, to execute a function on the owning client, use FunctionFlags.RunOnClient:

```csharp
[UFunction(FunctionFlags.RunOnClient | FunctionFlags.Reliable)]
public partial void ClientFunction();
public partial void ClientFunction_Implementation();
{
    // Client-side code
}
```

## Multicast <a href="#multicast" id="multicast"></a>

For functions that should be executed on both the server and all clients, use FunctionFlags.Multicast:

```csharp
[UFunction(FunctionFlags.Multicast | FunctionFlags.Reliable)]
public partial void MulticastFunction();
public partial void MulticastFunction_Implementation();
{
    // Code executed on both server and clients
}
```
