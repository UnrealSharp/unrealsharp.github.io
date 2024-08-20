---
title: Enums
layout: default
nav_order: 3
---

## Classes

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
    public TMap<int, FString> MyMap { get; set; }

    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public TWeakObjectPtr<AMyShowcaseClass> MyWeakObject { get; set; }

    protected override void BeginPlay()
    {
        base.BeginPlay();

        PrintString("BeginPlay called!");

        MyMap.Add(1, "First Value");
        MyMap.Add(2, "Second Value");

        MyFloat = 3.14f;

        MyWeakObject = this;

        UpdateMapWithKey(2, "Updated Second Value");
    }

    [UFunction(FunctionFlags.BlueprintCallable)]
    public void UpdateMapWithKey(int key, FString value)
    {
        if (MyMap.Contains(key))
        {
            MyMap[key] = value;
            PrintString($"Updated key {key} with value '{value}'.");
        }
        else
        {
            MyMap.Add(key, value);
            PrintString($"Added key {key} with value '{value}'.");
        }
    }

    [UFunction(FunctionFlags.BlueprintCallable)]
    public void HandleInteraction(AActor otherActor)
    {
        if (otherActor != null)
        {
            FVector direction = (otherActor.GetActorLocation() - GetActorLocation()).GetSafeNormal();
            PrintString($"Interacted with {otherActor.Name}, moving towards {direction.ToString()}.");

            // Example: applying a simple force
            UPrimitiveComponent primitiveComp = otherActor.FindComponentByClass<UPrimitiveComponent>();
            if (primitiveComp != null)
            {
                primitiveComp.AddImpulse(direction * 500.0f, NAME_None, true);
            }
        }
    }
    
    public void MyInterfaceFunction()
    {
        PrintString("MyInterfaceFunction called!");
    }
}
```