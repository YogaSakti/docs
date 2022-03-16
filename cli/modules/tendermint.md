---
description: The tendermint module allows for querying of validator and node addresses.
---

# tendermint

## Available Commands

| Name, shorthand | Description |
| :--- | :--- |
| [show-address](tendermint.md#tendermint-show-address) | Shows this node's tendermint validator consensus address |
| [show-node-id](tendermint.md#tendermint-show-node-id) | Show this node's ID |
| [show-validator](tendermint.md#tendermint-show-validator) | Show this node's tendermint validator info |
| [version](tendermint.md#tendermint-version) | Print tendermint libraries' version |

### tendermint show-address

The following command will show the tendermint validator address of the local node.

```text
$BINARY tendermint show-address
```

Returns the bech32 encoded validator consensus address `<junovalcon...>`:

```text
junovalcons1xyld7wpwjwx5reu8k0rrveceqztyp3h3fy3m6m
```

### tendermint show-node-id <a id="tendermint-show-node-id"></a>

The following command will show the nodes ID

```text
$BINARY tendermint show-node-id
```

Returns something similar to:

```text
ec730773944fbdc6a8c4918984f571aa57c975a3
```

### tendermint show-validator <a id="tendermint-show-validator"></a>

The following command will show the validators tendermint consensus pubkey:

```text
$BINARY tendermint show-validator
```

Returns something similar to:

```text
junovalconspub1zcjduepqltmy70ayq5c52fqga7xv336wv3jn8wxjcqra72amp6gcm7l8jwkss0ekqe
```

### tendermint version <a id="tendermint-version"></a>

```text
$BINARY tendermint version
```

Returns something similar to:

```text
tendermint: ""
abci: 0.17.0
blockprotocol: 11
p2pprotocol: 8
```

