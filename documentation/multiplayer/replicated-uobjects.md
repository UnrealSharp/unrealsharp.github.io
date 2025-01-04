# Replicated UObjects

To replicate UObjects you have to make a new `UObject`class inheriting from `UCSReplicatedObject`.&#x20;

```csharp
[UClass]
public class UMyReplicatedUObject : UCSReplicatedObject
{
    
}
```

This object can now replicate variables and send RPCs.

To use your replicated UObject in Unreal's multiplayer system it needs to be registered through an `AActor` or `UActorComponent`.&#x20;

## **Actor Example**

```csharp
[UClass]
public class AMyReplicatedActor : AActor
{
    [UProperty(PropertyFlags.Replicated)]
    public UMyReplicatedUObject ReplicatedObject { get; set; }

    protected override void BeginPlay()
    {
        base.BeginPlay();

        if (HasAuthority())
        {
            ReplicatedObject = NewObject<UMyReplicatedUObject>(this);
            
            // Register the new replicated UObject
            AddReplicatedSubObject(ReplicatedObject);
        }
    }
}
```

## UActorComponent Example

```csharp
[UClass]
public class UMyReplicatedComponent : UActorComponent
{
    [UProperty(PropertyFlags.Replicated)]
    public UMyReplicatedUObject ReplicatedObject { get; set; }

    public override void BeginPlay()
    {
        base.BeginPlay();

        if (Owner.HasAuthority())
        {
            ReplicatedObject = NewObject<UMyReplicatedUObject>(this);
            
            // Register the new replicated UObject
            AddReplicatedSubObject(ReplicatedObject);
        }
    }
}
```
