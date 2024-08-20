---
title: Classes
layout: default
nav_order: 3
---

# Classes

To expose C# classes to Unreal Engine, they must be marked with the [UClass] attribute and inherit from a UObject, such as AActor, UActorComponent, or any other subclass. Additionally, all members that are exposed to Unreal Engine through the [UProperty] attribute must be defined as properties.

```c#
[UClass]
public class AMyShowcaseClass : AActor, IMyInterface
{
    [UProperty(DefaultComponent = true, RootComponent = true)]
    public UStaticMeshComponent MyMesh { get; set; }
    
    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public TArray<int> MyArray { get; set; }

    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public TMap<int, string> MyMap { get; set; }

    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public TWeakObjectPtr<AMyShowcaseClass> MyWeakObject { get; set; }

    protected override void BeginPlay()
    {
        base.BeginPlay();

        PrintString("BeginPlay called!");

        MyMap.Add(1, "First Value");
        MyMap.Add(2, "Second Value");

        MyWeakObject = this;

        UpdateMapWithKey(2, "Updated Second Value");
    }

    [UFunction(FunctionFlags.BlueprintCallable)]
    public void UpdateMapWithKey(int key, string newValue)
    {
        if (MyMap.ContainsKey(key))
        {
            MyMap[key] = newValue;
            PrintString($"Updated key {key} with value '{newValue}'.");
        }
        else
        {
            MyMap.Add(key, newValue);
            PrintString($"Added key {key} with value '{newValue}'.");
        }
    }

    [UFunction(FunctionFlags.BlueprintCallable)]
    public void HandleInteraction(AActor otherActor)
    {
        if (otherActor != null)
        {
            FVector direction = (otherActor.GetActorLocation() - GetActorLocation());
            PrintString($"Interacted with {otherActor.ObjectName}, moving towards {direction.ToString()}.");

            // Example: applying a simple force
            UPrimitiveComponent primitiveComp = otherActor.GetComponentByClass<UPrimitiveComponent>();
            if (primitiveComp != null)
            {
                primitiveComp.AddImpulse(direction * 500.0f, FName.None, true);
            }
        }
    }
    
    public void MyInterfaceFunction()
    {
        PrintString("MyInterfaceFunction called!");
    }
}
```