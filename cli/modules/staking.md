---
description: >-
  The staking module provides a set of subcommands to query the staking state
  and send staking transactions.
---

# staking

## Available Commands

| Name | Description |
| :--- | :--- |
| [validator](staking.md#query-staking-validator) | Query a validator |
| [validators](staking.md#query-staking-validators) | Query for all validators |
| [delegation](staking.md#query-staking-delegation) | Query a delegation based on address and validator address |
| [delegations](staking.md#query-staking-delegations) | Query all delegations made from one delegator |
| [delegations-to](staking.md#query-staking-delegations-to) | Query all delegations to one validator |
| [unbonding-delegation](staking.md#query-staking-unbonding-delegation) | Query an unbonding-delegation record based on delegator and validator address |
| [unbonding-delegations](staking.md#query-staking-unbonding-delegations) | Query all unbonding-delegations records for one delegator |
| [unbonding-delegations-from](staking.md#query-staking-unbonding-delegations-from) | Query all unbonding delegatations from a validator |
| [redelegations-from](staking.md#query-staking-redelegations-from) | Query all outgoing redelegatations from a validator |
| [redelegation](staking.md#query-staking-redelegation) | Query a redelegation record based on delegator and a source and destination validator address |
| [redelegations](staking.md#query-staking-redelegations) | Query all redelegations records for one delegator |
| [pool](staking.md#query-staking-pool) | Query the current staking pool values |
| [params](staking.md#query-staking-params) | Query the current staking parameters information |
| [historical-info](staking.md#query-staking-historical-info) | Query historical info at given height |
| [create-validator](staking.md#tx-staking-create-validator) | Create new validator initialized with a self-delegation to it |
| [edit-validator](staking.md#tx-staking-edit-validator) | Edit existing validator account |
| [delegate](staking.md#tx-staking-delegate) | Delegate liquid tokens to an validator |
| [unbond](staking.md#tx-staking-unbond) | Unbond shares from a validator |
| [redelegate](staking.md#tx-staking-redelegate) | Redelegate illiquid tokens from one validator to another |

### query staking validator

#### Query a validator by validator address

Query information for validator address `<valoper...>`:

```text
$BINARY query staking validator <valoper...>
```

Will return something similar to:

```text
commission:
  commission_rates:
    max_change_rate: "0.010000000000000000"
    max_rate: "0.200000000000000000"
    rate: "0.110000000000000000"
  update_time: "2021-07-01T09:06:42.110582713Z"
consensus_pubkey:
  '@type': /cosmos.crypto.ed25519.PubKey
  key: +vZPP6QFMUUkCO+MyMdOZGUzuNLAB98ruw6Rjfvnk60=
delegator_shares: "10647850539.181674918343698393"
description:
  details: ""
  identity: FEE30F35994C320D
  moniker: nullmames
  security_contact: ""
  website: ""
jailed: false
min_self_delegation: "1"
operator_address: valoper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
status: BOND_STATUS_BONDED
tokens: "10331782033"
unbonding_height: "631804"
unbonding_time: "2021-08-25T00:26:38.283926951Z"
```

### query staking validators

#### Query all validators

The following will return information for ALL validators:

```text
$BINARY query staking validators
```

The returned values will be similar to those from [`$BINARY query staking validator`](staking.md#query-staking-validator)\`\`

### query staking delegation

Query a delegation based on delegator address and validator address.

```text
$BINARY query staking delegation [delegator-addr] [validator-addr]
```

#### Query a delegation

The following will return delegations for a delegator to a particular validator address `<valoper...>` :

```text
$BINARY query staking delegation <juno...> <valoper...>
```

Returns something similar to:

```text
balance:
  amount: "9159423104"
  denom: <DENOM>
delegation:
  delegator_address: juno1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg
  shares: "9439626961.941610808328957187"
  validator_address: valoper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
```

### query staking delegations

Query all delegations delegated from one delegator.

```text
$BINARY query staking delegations [delegator-address] [flags]
```

#### Query all delegations of a delegator 

The following command will return all delegations from a delegators address `<juno...>`:

```text
$BINARY query staking delegations <juno...>
```

Will return something similar to:

```text
delegation_responses:
- balance:
    amount: "1100000"
    denom: <DENOM>
  delegation:
    delegator_address: juno1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg
    shares: "1100000.000000000000000000"
    validator_address: valoper1ms8tvfkerhyf6mca2qc79t7mr3eh9dsr79mjf2
- balance:
    amount: "9166092794"
    denom: <DENOM>
  delegation:
    delegator_address: juno1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg
    shares: "9446500690.213833508382324426"
    validator_address: valoper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
pagination:
  next_key: null
  total: "0"
```

### query staking delegations-to

Query all delegations to one validator.

```text
$BINARY query staking delegations-to [validator-address] [flags]
```

#### Query all delegations to one validator 

The following command will return all delegations to a validator address `<valoper...>`:

```text
$BINARY query staking delegations-to <valoper...>
```

Will return something similar to:

```text
delegation_responses:
- balance:
    amount: "990000675"
    denom: <DENOM>
  delegation:
    delegator_address: juno1qnshaxp9w7aecthj2sn4c0uct07urg3tsd2rqs
    shares: "1020286644.656983874857994825"
    validator_address: valoper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
- balance:
    amount: "180180122"
    denom: <DENOM>
  delegation:
    delegator_address: juno1na45quuuzuv5xtzl5qqp9zep9rkluqykwtcgd3
    shares: "185692169.327571065224155062"
    validator_address: valoper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
```

### query staking unbonding-delegation

Query an unbonding-delegation record based on delegator and validator address.

```text
$BINARY query staking unbonding-delegation [delegator-addr] [validator-addr] [flags]
```

#### Query an unbonding delegation record

```text
$BINARY query staking unbonding-delegation <juno...> <valoper...>
```

### query staking unbonding-delegations

#### Query all unbonding delegations records of a delegator

```text
$BINARY query staking unbonding-delegations <juno...>
```

### query staking unbonding-delegations-from

#### Query all unbonding delegations from a validator

```text
$BINARY query staking unbonding-delegations-from <valoper...>
```

### query staking redelegations-from

Query all outgoing redelegations of a validator

```text
$BINARY query staking redelegations-from [validator-address] [flags]
```

#### Query all outgoing redelegatations of a validator

```text
$BINARY query staking redelegations-from <valoper...>
```

### query staking redelegation

Query a redelegation record based on delegator and source validator address and destination validator address.

```text
$BINARY query staking redelegation [delegator-addr] [src-validator-addr] [dst-validator-addr] [flags]
```

#### Query a redelegation record

```text
$BINARY query staking redelegation <juno...> <valoper...> <valoper...>
```

### query staking redelegations

#### Query all redelegations records of a delegator

```text
$BINARY query staking redelegations <juno...>
```

### query staking pool

#### Query the current staking pool values

```text
$BINARY query staking pool
```

Returns something similar to:

```text
bonded_tokens: "1547447152807"
not_bonded_tokens: "67232814293"
```

### query staking params

#### Query the current staking parameters information

```text
$BINARY query staking params
```

Returns something similar to:

```text
bond_denom: <DENOM>
historical_entries: 10000
max_entries: 7
max_validators: 100
unbonding_time: 1814400s
```

### query staking historical-info

#### Query historical info at given height

```text
$BINARY query staking historical-info <height>
```

### tx staking create-validator

Send a transaction to apply to be a validator and delegate a certain amount of `juno` to it.

```text
$BINARY tx staking create-validator [flags]
```

**Flags:**

| Name, shorthand | type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| --amount | string | Yes |  | Amount of coins to bond |
| --commission-rate | float | Yes | 0.0 | The initial commission rate percentage |
| --commission-max-rate | float |  | 0.0 | The maximum commission rate percentage |
| --commission-max-change-rate | float |  | 0.0 | The maximum commission change rate percentage \(per day\) |
| --min-self-delegation | string |  |  | The minimum self delegation required on the validator |
| --details | string |  |  | Optional details |
| --genesis-format | bool |  | false | Export the transaction in gen-tx format; it implies --generate-only |
| --identity | string |  |  | Optional identity signature \(ex. UPort or Keybase\) |
| --ip | string |  |  | Node's public IP. It takes effect only when used in combination with |
| --node-id | string |  |  | The node's ID |
| --moniker | string | Yes |  | Validator name |
| --pubkey | string | Yes |  | Go-Amino encoded hex PubKey of the validator. For Ed25519 the go-amino prepend hex is 1624de6220 |
| --website | string |  |  | Optional website |
| --security-contact | string |  |  | The validator's \(optional\) security contact email |

#### Create a validator

```text
$BINARY tx staking create-validator --chain-id=$CHAINID--from=$KEYNAME --fees=0.025juno --pubkey=<validator-pubKey> --commission-rate=0.1 --amount=100000000<DENOM> --moniker=<validator-name>
```

{% hint style="info" %}
**TIP**

Refer to [mainnet](../../validators/mainnet.md) instructions for detailed information.
{% endhint %}

### tx staking edit-validator

Edit an existing validator's settings, such as commission rate, name, etc.

```text
$BINARY tx staking edit-validator [flags]
```

**Flags:**

| Name, shorthand | type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| --commission-rate | float |  | 0.0 | Commission rate percentage |
| --moniker | string |  |  | Validator name |
| --identity | string |  |  | Optional identity signature \(ex. UPort or Keybase\) |
| --website | string |  |  | Optional website |
| --details | string |  |  | Optional details |
| --security-contact | string |  |  | The validator's \(optional\) security contact email |
| --min-self-delegation | string |  |  | The minimum self delegation required on the validator |

#### Edit validator information

```text
$BINARY tx staking edit-validator --from=$KEYNAME --chain-id=$CHAINID--fees=1juno --commission-rate=0.10 --moniker=<validator-name>
```

### tx staking delegate

Delegate tokens to a validator.

```text
$BINARY tx staking delegate [validator-addr] [amount] [flags]
```

```text
$BINARY tx staking delegate <valoper...> <amount> --chain-id=$CHAINID--from=$KEYNAME
```

### tx staking unbond

Unbond tokens from a validator.

```text
$BINARY tx staking unbond [validator-addr] [amount] [flags]
```

#### Unbond some tokens from a validator

```text
$BINARY tx staking unbond <valoper...> 1000000<DENOM> --from=$KEYNAME --chain-id=$CHAINID
```

### tx staking redelegate

Transfer delegation from one validator to another.

{% hint style="info" %}
TIP

There is no `unbonding time` during the redelegation, so you will not miss the rewards. But you can only redelegate once per validator, until a period \(= `unbonding time`\) exceed.
{% endhint %}

```text
$BINARY tx staking redelegate [src-validator-addr] [dst-validator-addr] [amount] [flags]
```

#### Redelegate some tokens to another validator

```text
$BINARY tx staking redelegate <valoper...> <valoper...> 1000000<DENOM> --chain-id=$CHAINID--from=$KEYNAME
```

