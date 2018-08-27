# Voting for proposals

First make a proposal for a new Gateway, as described at [./setupgateways.md](setupgateways.md).

```
./asch-cli registergateway --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --title "new gateway" --desc "new gateway for NEW" --endHeight 50000 --name "newCoin" --symbol "NEW" --currencyDesc "a new asset" 
aa8aa91588dc87b62d5d2cbdcc26e7c475fc6775cb7b80d3769dc9e5923029bf
```

## what is a bookkeeper?
See: https://github.com/AschPlatform/asch/blob/develop/src/contract/proposal.js#L166:

```
if (!app.isCurrentBookkeeper(this.sender.address)) return 'Permission denied'
```

### try to vote

#### create a new user

```
./asch-cli crypto --generate
? Enter number of accounts to generate 1
[ { address: 'A8j4iHChYCPfNA6PDLsNAWvR1aGwwSnK1J',
    secret: 'above eternal sugar kingdom arch soup forward pluck hope senior peace clarify',
    publicKey: '82f803f7254008afa8295884b99d932872ac40736d4617ee159401c6bbc41402' } ]
Done
```

#### voting

```
./asch-cli upvoteproposal --secret "above eternal sugar kingdom arch soup forward pluck hope senior peace clarify" --tid "aa8aa91588dc87b62d5d2cbdcc26e7c475fc6775cb7b80d3769dc9e5923029bf"
#error
Server error: Error: Sender account not found
```

The error above is caused by the account does not have any XAS on its balance, so send some XAS to the account and try again:

```
./asch-cli sendmoney --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --amount 20000000000 --to "A8j4iHChYCPfNA6PDLsNAWvR1aGwwSnK1J"
```

Now the result is:
```
Server error: Error: Permission denied
```

The above brings us back to the original question what is a bookkeeper? Only the 101 most voted delegates may vote.
For the localnet these delgates are preconfigured in the `asch/config.json` file. The first account on the list has got the following secret: `praise modify banner vacant steak forest gravity code scene ensure street note`. When we look up the account we will find that shown beneath:

```
./asch-cli openaccount "praise modify banner vacant steak forest gravity code scene ensure street note"
{
  "address": "A7Vbt5h3WgaXLSJhUeHnRRcwvkGF3ecS7r",
  "unconfirmedBalance": 0,
  "balance": 0,
  "secondPublicKey": null,
  "lockHeight": 0,
  "publicKey": "4110e2ab06a075ff540cbcd9af5d7cce3a416595e7c259f15065895f7c84d16f"
}

./asch-cli getaccount "A7Vbt5h3WgaXLSJhUeHnRRcwvkGF3ecS7r"
{
  "success": true,
  "account": {
    "address": "A7Vbt5h3WgaXLSJhUeHnRRcwvkGF3ecS7r",
    "name": "asch_g1",
    "xas": 0,
    "publicKey": null,
    "secondPublicKey": null,
    "isLocked": 0,
    "isAgent": 0,
    "isDelegate": 1,
    "role": 1,
    "lockHeight": 0,
    "agent": null,
    "weight": 0,
    "agentWeight": 0,
    "_version_": 3
  }
}

```
As you can see the account has `"isDelegate": 1` and `"role": 1`. There are three roles now:

```
DELEGATE: 1,
AGENT: 2,
GATEWAY_VALIDATOR: 3,
``

#### Voting with the delgate found above
```
./asch-cli upvoteproposal --secret "praise modify banner vacant steak forest gravity code scene ensure street note" --tid "aa8aa91588dc87b62d5d2cbdcc26e7c475fc6775cb7b80d3769dc9e5923029bf"
```

Which returns as expected `Server error: Error: Insufficient sender balance`, so give the delegate some XAS too:

```
./asch-cli sendmoney --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --amount 20000000000 --to "A7Vbt5h3WgaXLSJhUeHnRRcwvkGF3ecS7r"
```

Now are vote can succefully be registered.

#### Let our new user vote too

Our user with address `A8j4iHChYCPfNA6PDLsNAWvR1aGwwSnK1J` got already got some XAS on its balance. Now let's preform the following steps:

##### Give the user a name
```
./asch-cli setname --secret "above eternal sugar kingdom arch soup forward pluck hope senior peace clarify" --username "bass"
```
##### Make the user a delegate
```
./asch-cli registerdelegate --secret "above eternal sugar kingdom arch soup forward pluck hope senior peace clarify"
```
##### now start gaining votes
But for the `localnet` it seems that i can already vote yet?!
```
./asch-cli upvoteproposal --secret "above eternal sugar kingdom arch soup forward pluck hope senior peace clarify" --tid "aa8aa91588dc87b62d5d2cbdcc26e7c475fc6775cb7b80d3769dc9e5923029bf"
a09fc5a19008ce6c96df49c7d716ff154c96b768b2af69329f44f90fddd1e7be

```

Maybe because of all 101 delegate which are added by default got 0 votes too?!
The above can be confirmed because we'll find the public key (`82f803f7254008afa8295884b99d932872ac40736d4617ee159401c6bbc41402`) of our account in the list of public keys in the `variables` table of the blockchain database. The list of public keys is hold by the `round_bookkeeper` variable, which will be use by the code in `` file to build a list of delegate which may forge blocks and vote for proposals. `app.isCurrentBookkeeper()` at the start of this story checks this list of delegates.




