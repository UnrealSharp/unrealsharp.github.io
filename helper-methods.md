---
title: Helper Methods
layout: default
---
# Helper Methods

UnrealSharp extends Unreal Engine by providing simplified methods to spawn and manage Actor and ActorComponent objects. Below are the available methods for each class type.

## Methods Available for Actor Classes:

### Basic Spawn:

```c#
AStaticMeshActor.Spawn(worldContextObject, MyActorClass);
```
Spawns an instance of the specified class.

### Spawn with Transform:

```c#
AStaticMeshActor.Spawn(worldContextObject, MyActorClass, GetActorTransform());
```

Spawns an instance of the specified class at a specific transform.

### Spawn with Collision Handling:

```c#
SpawnActorCollisionHandlingMethod method = SpawnActorCollisionHandlingMethod.AlwaysSpawn;
AStaticMeshActor.Spawn(worldContextObject, MyActorClass, GetActorTransform(), method, instigator, owner);
```

Spawns an instance of the specified class with specified collision handling, instigator, and owner.

## Methods Available for ActorComponent Classes:
### Retrieve Component:

```c#
UStaticMeshComponent? Mesh = UStaticMeshComponent.Get(actor);
```

Retrieves the StaticMeshComponent of the specified actor.

### Construct New Components:

```c#
UStaticMeshComponent MyNewMesh = UStaticMeshComponent.Construct(owner);
USkeletalMeshComponent MyNewMesh2 = USkeletalMeshComponent.Construct(owner, manualAttachment, new Transform());
USplineMeshComponent MyNewMesh3 = USplineMeshComponent.Construct(owner, MyComponentClass, manualAttachment, new Transform());
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
public partial class AMyActor : AActor
{
   
}

public partial class UMyComponent : UActorComponent
{

}
```