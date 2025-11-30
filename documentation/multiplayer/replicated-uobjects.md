# Replicated UObjects

To replicate UObjects you have to make a new `UObject`class inheriting from `UCSReplicatedObject`.

```csharp
[UClass]
public class UMyReplicatedUObject : UCSReplicatedObject
{
    
}
```

This object can now replicate variables and send RPCs.

To use your replicated UObject in Unreal's multiplayer system it needs to be registered through an `AActor` or `UActorComponent`.

## **Actor Example**

```csharp
[UClass]
public partial class AMyReplicatedActor : AActor
{
    [UProperty(PropertyFlags.Replicated)]
    public partial UMyReplicatedUObject ReplicatedObject { get; set; }

    public override void BeginPlay()
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
public partial class UMyReplicatedComponent : UActorComponent
{
    [UProperty(PropertyFlags.Replicated)]
    public partial UMyReplicatedUObject ReplicatedObject { get; set; }

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
