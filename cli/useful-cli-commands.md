
# Useful CLI Commands

Set ENV 

```bash
CHAINID=<chain-id>
BINARY=<binary-name>
KEYNAME=$KEYNAME
```

## NODE

Get standard debug info from the daemon:

```bash
$BINARY status
```

Check if your node is catching up:

```bash
# Query via the RPC (default port: 26657)
curl http://localhost:26657/status | jq .result.sync_info.catching_up
```

Get your node ID:
```bash
$BINARY tendermint show-node-id
```

{% hint style="info" %}
Your peer address will be the result of this plus host and port, i.e. `<id>@<host>:26656` if you are using the default port.
{% endhint %}


Set the default chain for commands to use:
```bash
$BINARY config chain-id $CHAINID
```

## Wallet, Bank, Txs
---
See keys 
```bash
$BINARY keys list
```
Import a key from a mnemonic
```bash
$BINARY keys add <new-key-name> --recover
```

Export a private key (warning: don't do this unless you know what you're doing!)
```bash
$BINARY keys export $KEYNAME --unsafe --unarmored-hex
```

Find out Balance on account
```bash
$BINARY tx bank balances $($BINARY keys show $KEYNAME -a)
```

Send Balance
```bash
$BINARY tx bank send $($BINARY keys show $KEYNAME -a) <recipient addr> <AMOUNT><DENOM>
```

Find out what the JSON for a command would be using `--generate-only`
```bash
$BINARY tx bank send $($BINARY keys show $KEYNAME -a) <recipient addr> <AMOUNT><DENOM> --generate-only
```

See all TXs and their type
```bash
$BINARY query txs --events "message.sender=akash1....." --page 1 --limit 100 -o json  | jq -r '.txs[] | [ .txhash, .timestamp, (.tx.body.messages[] | [  ."@type", .owner, .host_uri ] )[] ] | @csv'
```

See all bank transfers to a specific account
```bash
$BINARY query txs --events "message.module=bank&transfer.recipient=akash1....." --page 1 --limit 100  | jq -r '.txs[] | [.timestamp, .txhash, .height, (.tx | (.auth_info.fee.amount[0].amount|tonumber / pow(10; 6)), (.body.messages[] | ."@type", (.from_address, .to_address, (.amount[].amount|tonumber)/pow(10;6))))] | @csv'
```

Check tx
```bash
$BINARY query tx <hash> -o json | jq -r '.raw_log'
```



## STAKING 
---
Stake
```bash
$BINARY tx staking delegate <valoper1...> <AMOUNT><DENOM> --from $KEYNAME
```

Withdraw Reward
Withdraw all rewards

```bash
... tx distribution withdraw-all-rewards <valoper1...> --from $KEYNAME 
```

Withdraw rewards (including validator commission)
```bash
$BINARY tx distribution withdraw-rewards <valoper1...> --from $KEYNAME --commission
```

## GOV

Vote Proposal
```bash
$BINARY tx gov vote 1 yes --from $KEYNAME
```

Query the results of a gov vote that has ended (NB - you have to specify a height before the vote ended):
```bash
$BINARY q gov votes 1 --height <height-before-vote-ended>
```

## Validator

Get your `valoper` address
```bash
$BINARY keys show $KEYNAME -a --bech val
```

Query the validator set (and jailed status) via CLI
```bash
$BINARY query staking validators --limit 1000 -o json | jq -r '.validators[] | [.operator_address, (.tokens|tonumber / pow(10; 6)), .description.moniker, .jail, .status] | @csv' | column -t -s"," | sort -k2 -n -r | nl
```

Validator info

```bash
$BINARY  q staking validator <valoper1...>
```

Check if you are jailed or tombstoned:
```bash
$BINARY query slashing signing-info $($BINARY tendermint show-validator)
```

Unjail Validator

```bash
$BINARY tx slashing unjail --from $KEYNAME  --chain-id $CHAINID
```