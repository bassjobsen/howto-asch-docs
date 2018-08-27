#setup a gateway

To set up a gateway you should preform the following steps:

1. register the gateway (asch-cli registergateway)
2. get enough votes (not implemented yet)
3. then active the proposal (asch-cli activateproposal, first get the tid: curl -k -X GET 'http://localhost:4096/api/v2/proposals)
4. generate 3 new member accounts (asch-cli crypto --generate)
5. send some XAS to the member accounts (asch-cli sendmoney)
6. set a new name for each member account (asch-cli setname)
7. register each member account as a member (asch-cli registermember)
8. initiate the gateway (asch-cli initgateway)
9. get enough votes (not implemented yet)
10. activate the gateway (asch-cli activateproposal, first get the tid: curl -k -X GET 'http://localhost:4096/api/v2/proposals)

With the latest version of asch-cli (and the latest version of asch-js) you can run:

```
./asch-cli registergateway --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --title "new gateway" --desc "new gateway for NEW" --endHeight 50000 --name "newCoin2" --symbol "NEW2" --currencyDesc "a new asset" 

// get enough votes, then active the proposal
```
Read [here](./votingforproposals.md) howto vote for a proposal. 
Notice that the number of votes is checked at [https://github.com/AschPlatform/asch/blob/develop/src/contract/proposal.js#L193](https://github.com/AschPlatform/asch/blob/develop/src/contract/proposal.js#L193):

```
if (validVoteCount <= ((101 * 2) / 3)) return 'Vote not enough'
```
You may comment out this line when testing.

```

//first get the tid: curl -k -X GET 'http://localhost:4096/api/v2/proposals

./asch-cli activateproposal --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --tid 343131b1a18ea72fd60b70fe09d81e3b65fae4aab43bf33b27218dca57756fe4

returns: 07e0ac799179b20281e50ffadeba03e2ac04e7fbb7103c2287705b71fb04ec93


./asch-cli crypto --generate 
? Enter number of accounts to generate 3
[ { address: 'ABb4dQCGPMpUdhHs19AVREDY3GatCP3hBh',
    secret: 'security fluid taxi wasp stem seek urge cushion uniform local tunnel neglect',
    publicKey: 'cb6241d9131fba73fad34080507b5ec284863ba91e5236becb9421ae3b8ba53f' },
  { address: 'AG1Z7QD2XFVPmKHPp5A1PY35ZnJhGzwbaW',
    secret: 'bracket proof blur fame label harvest flight final ordinary detect social ecology',
    publicKey: 'd14a5dcd1bc51637d6dc3843302894b167b6eba1dee8ca09b2a1e1b8c91791b6' },
  { address: 'AENhPf9KNusj9W9ZE8fwPgbSxwyeqeGANo',
    secret: 'turn permit solve tourist carpet daring question ugly cigar weapon family village',
    publicKey: 'afebe6a5685b7061fe5837fd19185d75f9f7e797c8218cd37769ee6981ac5b95' } ]
Done

// send some money to the member to set their name

./asch-cli sendmoney --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --amount 20000000000 --to "ABb4dQCGPMpUdhHs19AVREDY3GatCP3hBh"
./asch-cli sendmoney --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --amount 20000000000 --to "AG1Z7QD2XFVPmKHPp5A1PY35ZnJhGzwbaW"
./asch-cli sendmoney --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --amount 20000000000 --to "AENhPf9KNusj9W9ZE8fwPgbSxwyeqeGANo"


// setnames for the members

./asch-cli setname --secret "security fluid taxi wasp stem seek urge cushion uniform local tunnel neglect" --username "member1"
./asch-cli setname --secret "bracket proof blur fame label harvest flight final ordinary detect social ecology" --username "member2"
./asch-cli setname --secret "turn permit solve tourist carpet daring question ugly cigar weapon family village" --username "member3"

//register the members

./asch-cli registermember --secret "security fluid taxi wasp stem seek urge cushion uniform local tunnel neglect" --gateway "newCoin"
./asch-cli registermember --secret "bracket proof blur fame label harvest flight final ordinary detect social ecology" --gateway "newCoin"
./asch-cli registermember --secret "turn permit solve tourist carpet daring question ugly cigar weapon family village" --gateway "newCoin"


// now we can init the Gateway

./asch-cli initgateway --name "newCoin" --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --members "ABb4dQCGPMpUdhHs19AVREDY3GatCP3hBh,AG1Z7QD2XFVPmKHPp5A1PY35ZnJhGzwbaW,AENhPf9KNusj9W9ZE8fwPgbSxwyeqeGANo"

// get enough votes, then active the proposal

//first get the tid: curl -k -X GET 'http://localhost:4096/api/v2/proposals


./asch-cli activateproposal --tid ca182d2c42e2c9567c009d4e336e2aedc6a6539cc2f3060de44a9a797b0f7852 --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element"
```
