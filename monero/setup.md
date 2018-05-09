Example Monero home screen:

https://imgur.com/a/wOFhhZ1.jpg

#Setup Instructions:

1) Download the KWGT app from the play store. The free version will work fine

2) Download the following image: https://imgur.com/a/wOFhhZ1.jpg to use as your background

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

`Total USD: $mu(round,sh("curl -s https://supportxmr.com/api/miner/<insert your wallet address>/stats | sed 's/,/\n/g' | grep amtDue | grep -Eo '[0-9]+'",600) * 0.000000000001 * sh("curl -s https://api.coinmarketcap.com/v1/ticker/monero/ | grep --color=no price_usd | grep --color=no -Eo '[0-9.]+'") * 1,2)$`
