---
description: >-
  Gameplay Tags are user-defined strings that function as conceptual,
  hierarchical labels.
---

# Gameplay Tags

All defined `FGameplayTags` in your project are available in code through the `GameplayTags`static class.

```csharp
FGameplayTag myGameplayTag = GameplayTags.MyGameplayTag;
FGameplayTag myGameplayTagMySubTag = GameplayTags.MyGameplayTag_MySubTag;
```

The GameplayTags class updates in real time as you add more tags to your project.
