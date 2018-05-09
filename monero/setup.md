Example Monero home screen:

![Monero Home Screen](https://i.imgur.com/qAezO2a.png)

#Setup Instructions:

1) Download the KWGT app from the play store. The free version will work fine

2) Download the following image: https://i.imgur.com/BqrkIgg.png to use as your background

3) Place a new KWGT widget on your home screen, wherever you want it

4) Using the KWGT app, create a text field in the new widget

# Different sample codes for text widgets

XMR Price updates:

`XMR Price: $$$mu(round,sh("curl -s https://api.coinmarketcap.com/v1/ticker/monero/ | grep --color=no price_usd | grep --color=no -Eo '[0-9.]+'") * 1,2)$`

Getting amount due from supportxmr.com:

`Mined: $mu(round,sh("curl -s https://supportxmr.com/api/miner/<insert your wallet address>/stats | sed 's/,/\n/g' | grep amtDue | grep -Eo '[0-9]+'",600) * 0.000000000001,4)$`

Check the hashrate of an xmr-stak mining rig:

`Hashrate: $mu(round,sh("curl -s http://<your mining rig address>/api.json | sed 's/,/\n/g' | grep total | grep -v '_' | grep -Eo '[0-9.]+'") * 1)$ H/s`

Your total XMR balance (mined and held):

`Total XMR: $mu(round,sh("curl -s https://supportxmr.com/api/miner/<insert your wallet address>/stats | sed 's/,/\n/g' | grep amtDue | grep -Eo '[0-9]+'",600) * 0.000000000001 + <Your wallet balance>,4)$`

Your Total XMR balance in terms of USD:

`Total USD: $mu(round,(sh("curl -s https://supportxmr.com/api/miner/<insert your wallet address>/stats | sed 's/,/\n/g' | grep amtDue | grep -Eo '[0-9]+'",600) * 0.000000000001 + <your wallet balance>) * sh("curl -s https://api.coinmarketcap.com/v1/ticker/monero/ | grep --color=no price_usd | grep --color=no -Eo '[0-9.]+'") * 1,2)$`

Text box details:

- Font: size 40

- Color: FF000000

If anyone finds this cool/useful I always appreciate donations:

XMR: 45d4VHWboXGV5sgvZ8hMFqdqnyku4vni33pbtMEFMGVk7ZcsHbwKepUFvhNsVEEu4Gd4F6KpJPZ1JZjSXUMY6eA7KJZA75P

BTC: 1HqWUi2KVF5WZ2meJcYcnCmyua3SrMubNC

ETH: 0x20cb37136936ee535bde314036e73a99d70c1566
