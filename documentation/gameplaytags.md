---
description: >-
    Gameplay Tags are user-defined strings that function as conceptual, hierarchical labels. 
    You can apply Gameplay Tags to objects in your project and evaluate them to drive your gameplay implementation, similarly to checking for booleans or flags.
---

# Gameplay Tags

All defined `FGameplayTags` in your project are available in code through the `GameplayTags` static class.

```csharp
FGameplayTag myGameplayTag = GameplayTags.MyGameplayTag;
FGameplayTag myGameplayTagMySubTag = GameplayTags.MyGameplayTag_MySubTag;
```

The GameplayTags class updates in real time as you add more tags to your project.
