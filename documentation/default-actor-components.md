---
description: >-
  In Unreal Engine, actors can be composed of multiple components that represent
  physical parts of the object, such as meshes, cameras, or lights.
---

# Default Actor Components

## Setting a Root Component <a href="#setting-a-root-component" id="setting-a-root-component"></a>

Every actor needs a root component, which serves as the parent for all other components in the actor’s hierarchy. The root component defines the actor’s position, rotation, and scale in the world.

To define a root component using UnrealSharp, you use the **\[UProperty]** attribute with the DefaultComponent and RootComponent flags set to true:

```csharp
[UProperty(DefaultComponent = true, RootComponent = true)]
public USceneComponent MyRootComponent { get; set; }
```

* **DefaultComponent**: This flag indicates that the property should be automatically instantiated as a component when the actor is created.
* **RootComponent**: Setting this flag to true designates this component as the root component of the actor.

## Attaching More Components <a href="#attaching-more-components" id="attaching-more-components"></a>

Once the root component is set, you can begin attaching other components. A common requirement is to attach a visual representation to your actor, like a static mesh.

To attach a component as a child of the root component, use the AttachmentComponent parameter to specify the parent component’s name:

```csharp
[UProperty(DefaultComponent = true, AttachmentComponent = nameof(MyRootComponent))]
public UStaticMeshComponent MyStaticMeshComponent { get; set; }
```

You can also attach components to another component’s socket:

```csharp
[UProperty(DefaultComponent = true, AttachmentComponent = nameof(MyRootComponent), AttachmentSocket = "MySocketName")]
public USkeletalMeshComponent MySkeletalMeshComponent { get; set; }
```
