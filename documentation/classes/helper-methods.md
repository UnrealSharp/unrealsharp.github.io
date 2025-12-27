# Helper Methods

## Methods Available for Actor Classes: <a href="#methods-available-for-actor-classes" id="methods-available-for-actor-classes"></a>

### Basic Spawn <a href="#basic-spawn" id="basic-spawn"></a>

```csharp
AStaticMeshActor.Spawn(worldContextObject, MyActorClass);
```

Spawns an instance of the specified class.

### Spawn with Transform <a href="#spawn-with-transform" id="spawn-with-transform"></a>

```csharp
AStaticMeshActor.Spawn(worldContextObject, MyActorClass, GetActorTransform());
```

Spawns an instance of the specified class at a specific transform.

### Spawn with Collision Handling <a href="#spawn-with-collision-handling" id="spawn-with-collision-handling"></a>

```csharp
SpawnActorCollisionHandlingMethod method = SpawnActorCollisionHandlingMethod.AlwaysSpawn;
AStaticMeshActor.Spawn(worldContextObject, MyActorClass, GetActorTransform(), method, instigator, owner);
```

Spawns an instance of the specified class with specified collision handling, instigator, and owner.

## Methods Available for ActorComponent Classes: <a href="#methods-available-for-actorcomponent-classes" id="methods-available-for-actorcomponent-classes"></a>

### Retrieve Component <a href="#retrieve-component" id="retrieve-component"></a>

```csharp
UStaticMeshComponent? Mesh = UStaticMeshComponent.Get(actor);
```

Retrieves the StaticMeshComponent of the specified actor.

### Construct New Components <a href="#construct-new-components" id="construct-new-components"></a>

```csharp
UStaticMeshComponent MyNewMesh = UStaticMeshComponent.Construct(owner);
USkeletalMeshComponent MyNewMesh2 = USkeletalMeshComponent.Construct(owner, manualAttachment, new Transform());
USplineMeshComponent MyNewMesh3 = USplineMeshComponent.Construct(owner, MyComponentClass, manualAttachment, new Transform());
```

Constructs new mesh components with specified owner, attachment settings, and transform.

### Enabling Code Generation <a href="#enabling-code-generation" id="enabling-code-generation"></a>

To use the code generation for your custom classes (it’s already enabled for engine classes), update your project file (csproj) to include the source generator. Add the following lines to your csproj file:

```xml
<ItemGroup>
    <Analyzer Include="..\..\Plugins\UnrealSharp\Binaries\Managed\netstandard2.0\UnrealSharp.ExtensionSourceGenerators.dll" />
</ItemGroup>
```

