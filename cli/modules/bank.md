---
description: >-
  bank module allows you to manage assets for accounts loaded into the local
  keys module
---

# bank

## Available Commands

| Name | Description |
| :--- | :--- |
| [balances](bank.md#query-bank-balances) | Query for account balances by address |
| [total](bank.md#query-bank-total) | Query the total supply of coins of the chain |
| [send](bank.md#tx-bank-send) | Create and/or sign and broadcast a MsgSend transaction |

### query bank balances

Query the total balance of an account or of a specific denomination.

```text
$BINARY query bank balances [address] [flags]
```

**Flags:**

| Name, shorthand | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| -h, --help |  |  |  | Help for coin-type |
| --denom | string |  |  | The specific balance denomination to query for |
| --count-total |  |  |  | Count total number of records in all balances to query for |

### query bank total

Query total supply of coins that are held by accounts in the chain.

```text
$BINARY query bank total [flags]
```

**Flags:**

| Name, shorthand | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| -h, --help |  |  |  | Help for coin-type |
| --denom | string |  |  | The specific balance denomination to query for |

### tx bank send

Sending tokens to another address, this command includes `generate`, `sign` and `broadcast` steps.

```text
$BINARY tx bank send [from_key_or_address] [to_address] [amount] [flags]
```

**Flags:**

| Name, shorthand | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| -h, --help |  |  |  | Help for balances |

