---
description: Attribute flags for UFunction and their purpose
---

# Specifiers

<table data-full-width="true"><thead><tr><th>Function Flag</th><th>Effect</th></tr></thead><tbody><tr><td><strong>BlueprintAuthorityOnly</strong></td><td>This function will only execute from Blueprint code if running on a machine with network authority (a server, dedicated server, or single-player game).</td></tr><tr><td><strong>BlueprintCallable</strong></td><td>The function can be executed in a Blueprint or Level Blueprint graph.</td></tr><tr><td><strong>BlueprintCosmetic</strong></td><td>This function is cosmetic and will not run on dedicated servers.</td></tr><tr><td><strong>BlueprintEvent</strong></td><td>This function is designed to be overridden by a Blueprint, but also has a default C# implementation.</td></tr><tr><td><strong>BlueprintPure</strong></td><td><p>The function does not affect the owning object in any way and can be executed in a Blueprint or Level Blueprint graph.</p><pre class="language-csharp"><code class="lang-csharp">[UFunction(FunctionFlags.BlueprintPure)]
public int BlueprintPureFunction()
{
  return 1;
}
 
[UFunction(FunctionFlags.BlueprintCallable)]
public int BlueprintCallableFunction()
{
  return 1;
}

</code></pre><p><img src="https://d1iv7db44yhgxn.cloudfront.net/documentation/images/99304a15-d36b-4ef2-adc6-2fd2e0894c0a/bpcallable.png" alt=""></p><p>Pure functions do not cache their results, therefore you should be cautious when doing any non-trivial amount of work with a blueprint function. It is good practice to avoid outputting array properties in Blueprint pure functions.</p></td></tr><tr><td><strong>Client</strong></td><td>The function is only executed on the client that owns the Object on which the function is called.</td></tr><tr><td><strong>Exec</strong></td><td>The function can be executed from the in-game console. Exec commands only function when declared within certain Classes.</td></tr><tr><td><strong>NetMulticast</strong></td><td>The function is executed both locally on the server, and replicated to all clients, regardless of the Actor's <code>NetOwner</code>.</td></tr><tr><td><strong>Reliable</strong></td><td>The function is replicated over the network, and is guaranteed to arrive regardless of bandwidth or network errors. Only valid when used in conjunction with <code>Client</code> or <code>Server</code>.</td></tr><tr><td><strong>Server</strong></td><td>The function is only executed on the server.</td></tr></tbody></table>

### Metadata Specifiers <a href="#metadataspecifiers" id="metadataspecifiers"></a>
