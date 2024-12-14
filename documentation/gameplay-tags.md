---
description: >-
  Gameplay Tags are user-defined names that function as conceptual, hierarchical
  labels.
---

# Gameplay Tags

All defined `FGameplayTags` in your project are available in code through the `GameplayTags`static class.

```csharp
FGameplayTag myGameplayTag = GameplayTags.MyGameplayTag;
FGameplayTag myGameplayTagMySubTag = GameplayTags.MyGameplayTag_MySubTag;
```

The `GameplayTags` class updates in real time as you add more tags to your project.

## Gameplay Tag Container

`FGameplayTagContainer` is a wrapper around an array of `FGameplayTag`. UnrealSharp provides a intuitive API to work with them with C# features:

#### Constructing a `FGameplayTagContainer`

1. **Using a list of `FGameplayTag`:**

```csharp
List<FGameplayTag> tags = new List<FGameplayTag>
{
    GameplayTags.MyGameplayTag,
    GameplayTags.MyGameplayTag_MySubTag
};

FGameplayTagContainer containerInitWithList = new FGameplayTagContainer(tags);
```

2. **Using Array Parameters:**

```csharp
FGameplayTagContainer containerInitWithArrayParams = new FGameplayTagContainer(
    GameplayTags.MyGameplayTag,
    GameplayTags.MyGameplayTag_MySubTag
);
```

#### Appending Tags

1. **Appending a List of Tags:**

```csharp
gameplayTagContainer.AppendTags(tags);
```

2. **Appending Individual Tags:**

```csharp
gameplayTagContainer.AppendTags(
    GameplayTags.MyGameplayTag,
    GameplayTags.MyGameplayTag_MySubTag
);
```

3. **Appending Another Container:**

```csharp
gameplayTagContainer.AppendTags(containerInitWithList);
```
