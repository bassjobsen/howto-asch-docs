# Using a second secret

Notice that the preceding only will work after [https://github.com/AschPlatform/asch-cli/pull/33](https://github.com/AschPlatform/asch-cli/pull/33) had been merged!

First create two new users:

```
asch-cli crypto --generate
? Enter number of accounts to generate 2
[ { address: 'AN2QbVk8oT4P8kzRaYyHjmWTjzDHCtTiUq',
    secret: 'garden sun bamboo level local success reason scorpion delay egg fragile child',
    publicKey: '34c6610e1536205e4cd8bf0a57c3dd12d888b64a9dc3f070678a5e132066f581' },
  { address: 'AFPuivqAVsMMFF5UXF9YpGt7mkLXBC2bfn',
    secret: 'observe tired essence art smile calm circle whip embrace silver sudden village',
    publicKey: '1a6083f5608c2f090b1c1507a6caeb650698b6b8b8c635c2bd9afafd55e43c25' } ]
Done
```
Give the account with address `AN2QbVk8oT4P8kzRaYyHjmWTjzDHCtTiUq` some money:

```
asch-cli sendmoney --secret "stone elephant caught wrong spend traffic success fetch inside blush virtual element" --amount 20000000000 --to "AN2QbVk8oT4P8kzRaYyHjmWTjzDHCtTiUq"
3e50063cceb9a003e6fa121fb83d0739f77bedbf01c7302e769e1790ccff6b36
```
### now the account can send money with it's secrect
```
asch-cli sendmoney --secret "garden sun bamboo level local success reason scorpion delay egg fragile child" --amount 100000000 --to "AFPuivqAVsMMFF5UXF9YpGt7mkLXBC2bfn"
d033b35fb01a0033f550c4b4def666e7b00dd6356e8e87617ab75baeb7e0f0a4
```

# Set the second secret
```
asch-cli setsecondsecret -e "garden sun bamboo level local success reason scorpion delay egg fragile child" -s "MySecrect"
bcd329b9470ba612eb311ee36742995c9f4d3e402f846adfca3bf4b809dc6cc3
```

## Try to send some money again
```
./asch-cli/bin/asch-cli sendmoney --secret "garden sun bamboo level local success reason scorpion delay egg fragile child" --amount 100000000 --to "AFPuivqAVsMMFF5UXF9YpGt7mkLXBC2bfn"
Server error: Error: Second signature not provided
```
As you see you'll have to set the Second signature too now. Let's try it:

```
./asch-cli/bin/asch-cli sendmoney --secret "garden sun bamboo level local success reason scorpion delay egg fragile child" --secondSecret "MySecrect" --amount 100000000 --to "AFPuivqAVsMMFF5UXF9YpGt7mkLXBC2bfn"
d962e9c36e62ce6dccd452c26a1b86e2fae4a06026f7e083bfbb4d621c3c015e
```

Et voilà!