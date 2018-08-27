# Test the new balance manager for Asch 1.4.1

# install asch
```
```

## install the frontend
apply: https://github.com/AschPlatform/asch/pull/241
and change the server as described at https://github.com/AschPlatform/asch/pull/241#issuecomment-410521986

## make sure we can login
apply: https://github.com/AschPlatform/asch-core/pull/20

# login with the (new) Genesis account

```
{
  "address": "ABuH9VHV3cFi9UKzcHXGMPGnSC4QqT2cZ5",
  "publicKey": "116025d5664ce153b02c69349798ab66144edd2a395e822b13587780ac9c9c09",
  "secret": "stone elephant caught wrong spend traffic success fetch inside blush virtual element" // password  
}
```

# create a new Dapp to test
```
git clone https://github.com/bassjobsen/asch-test-dapp.git asch-test-balance
```

Now create a new contract which can test both the old and new situation:


Also edit init.js as follows:


# Register the Dapp 

https://github.com/AschPlatform/asch-docs/blob/master/dapp/hello_world/en.md

```
? Enter number of accounts to generate 1
[ { address: 'A3GdY2XWVZivp6K2Dq6Y9bU7YFKTvCEUQX',
    secret: 'gesture goose side remember actress frame ceiling buffalo bring slice soap describe',
    publicKey: 'af4db18d47c198056e8ac1855b53308c628d3b553e801fb115d2b90eb7e48292' } ]
Done
```

asch-cli -H 127.0.0.1 -P 4096 sendmoney --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --to "A3GdY2XWVZivp6K2Dq6Y9bU7YFKTvCEUQX" --amount 100000000000

asch-cli -H 127.0.0.1 -P 4096 sendmoney --secret "gesture goose side remember actress frame ceiling buffalo bring slice soap describe" --to "C86R4GGnenbP9p5LLogJPPEGQzzAmU3ce4" --amount 1000000000

 
? Enter number of accounts to generate 5
[ { address: 'A7NMkvGPT4Nqeo9ffoQJbTNfHivh3TFUXm',
    secret: 'actress eyebrow soon crime motor sausage item section company across tonight legal',
    publicKey: '63356ff9c60a2d4f98654f8c5e8bd1f1fb83ff9ef6dc6edde4eec5a750a1bf8b' },
  { address: 'A6H5A4T2ov4b2rSQa4n3gs1RDfL2BDRzT8',
    secret: 'nurse trim ridge tiger finish decrease bid voice false topic battle hill',
    publicKey: '24b68db86257a40024b733aefa6c3f223fdd7717469eb1d768084ae1764ecb6e' },
  { address: 'AA2oirKcPmTTAF84C2nGKHicv4LuYimdqX',
    secret: 'cherry hint stay spy tool cabbage express pill entire matrix depend pistol',
    publicKey: '5ff7715feae008ed32de25a8692a96c231a8f7aea04df91a2826af389f33dfff' },
  { address: 'A3XXjYAx9xJFDpNEVrH7X23r2BY6mMHTaV',
    secret: 'weasel polar desert black loan glimpse already normal crush escape seat churn',
    publicKey: 'c20545851c4b24d9640dbe6e03524e62e3bbbeac414d84304241109696f07b49' },
  { address: 'A5hd2835cZdhYxcX94qKDLdYhW42LbUFMM',
    secret: 'milk jacket dance voice cake book fancy crater true frame fatal planet',
    publicKey: '19d9cdd3f7c27d4fe3bf9c726cee5ba1459ac1fcd21fac842f335591896d69ea' } ]
Done
63356ff9c60a2d4f98654f8c5e8bd1f1fb83ff9ef6dc6edde4eec5a750a1bf8b,24b68db86257a40024b733aefa6c3f223fdd7717469eb1d768084ae1764ecb6e,5ff7715feae008ed32de25a8692a96c231a8f7aea04df91a2826af389f33dfff,c20545851c4b24d9640dbe6e03524e62e3bbbeac414d84304241109696f07b49,19d9cdd3f7c27d4fe3bf9c726cee5ba1459ac1fcd21fac842f335591896d69ea

DappId: f180b812e0c54d6a3732d8a3991127910a33ca63f4e37e149461eb577a9ef236 -> version 2

for delegate:

[ { address: 'AMVNFb1JsocM57iRSScYmnyhUNBa9AA9n4',
    secret: 'flavor struggle fun bullet deposit boost kidney dynamic pink unable spare pool',
    publicKey: '81e454f101907114d668e6d6a3e741d0f1c3fe4bf40c5daf73c9c46ba9c06c1f' } ]
Done



