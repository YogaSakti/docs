---
description: The slashing module can unjail your validator
---

# slashing

## Available Commands

| Name | Description |
| :--- | :--- |
| [unjail](slashing.md#tx-slashing-unjail) | Unjail validator previously jailed for downtime or double-sign. |

### tx slashing unjail

Unjail validator previously jailed for downtime.

```text
$BINARY tx slashing unjail [flags]
```

#### Unjail a validator

The following example will unjail a validator using its validator operator \(owner\) key :

```text
$BINARY tx slashing unjail --from juno1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg --chain-id juno
```

{% hint style="info" %}
**TIP**

The validator operator key must be stored in the local keystore. 
{% endhint %}

