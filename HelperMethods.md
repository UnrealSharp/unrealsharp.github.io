---
title: Helper Methods
layout: default
---

UnrealSharp extends Unreal Engine by providing simplified methods to spawn and manage Actor and ActorComponent objects. Below are the available methods for each class type.

## Methods Available for Actor Classes:

### Basic Spawn:

```c#
StaticMeshActor.Spawn(worldContextObject, MyActorClass);
```
Spawns an instance of the specified class.

### Spawn with Transform:

```c#
StaticMeshActor.Spawn(worldContextObject, MyActorClass, GetActorTransform());
```

Spawns an instance of the specified class at a specific transform.

### Spawn with Collision Handling:

```c#
SpawnActorCollisionHandlingMethod method = SpawnActorCollisionHandlingMethod.AlwaysSpawn;
StaticMeshActor.Spawn(worldContextObject, MyActorClass, GetActorTransform(), method, instigator, owner);
```

Spawns an instance of the specified class with specified collision handling, instigator, and owner.

## Methods Available for ActorComponent Classes:
### Retrieve Component:

```c#
StaticMeshComponent? Mesh = StaticMeshComponent.Get(actor);
```

Retrieves the StaticMeshComponent of the specified actor.

### Construct New Components:

```c#
StaticMeshComponent MyNewMesh = StaticMeshComponent.Construct(owner);
SkeletalMeshComponent MyNewMesh2 = SkeletalMeshComponent.Construct(owner, manualAttachment, new Transform());
SplineMeshComponent MyNewMesh3 = SplineMeshComponent.Construct(owner, MyComponentClass, manualAttachment, new Transform());
```
Constructs new mesh components with specified owner, attachment settings, and transform.

### Enabling Code Generation:

To use the code generation for your custom classes (it's already enabled for engine classes), update your project file (csproj) to include the source generator. Add the following lines to your csproj file:

```xml
<ItemGroup>
  <Analyzer Include="..\Plugins\UnrealSharp\Binaries\Managed\UnrealSharp.ExtensionSourceGenerators.dll" />
</ItemGroup>
```

### Class Requirements:
For the generated methods to be applicable, your classes must be declared as partial:

```c#
public partial class MyActor : Actor
{
   
}

public partial class MyComponent : ActorComponent
{

}
```