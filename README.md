# trex

## What?
trex is a python program that can get information from bittrex.com's API and display it as plain text.

## Requirements
- API bindings provided by https://github.com/ericsomdahl/python-bittrex - so you need to install that before using the program. It can be installed with pip or from https://pypi.python.org/pypi/python-bittrex
- python 3.5 or higher
- I have personally only tested/used it on linux, but it should work on any platform as long as the above requirements are met.

## Why?
I initially wrote this because I needed a way to get the current value of certain cryptocurrencies in plain and simple text format. Since I later on wanted simple access to information from my account on bittrex, it evolved to retrieve other kinds of information as well.

For example, if I want to see the balance of all my wallets on bittrex, I used to have to: open a browser, go to the site, log in, enter 2FA code, click on wallets, and finally find what I was looking for. Now I can open a terminal and enter `trex balances` and BOOM! I have everything I need nicely displayed in plain text, ready to interact with grep or awk or whatnot if I want to.

For now it does NOT support placing buy/sell orders on bittrex, although that would be fairly easy to implement. This is because of the potential security risk involved, and the risk involved in giving a 3rd party app access to buying/selling/withdrawing from your account. I will do more research to find out how it can be done securely before implementing it.

## How?
`trex -h` is good starting point!

But let's look at some examples.

`trex ticker btc neo` will show the current value of BTC-NEO formatted as satoshis (8 decimal places).

`trex ticker usdt neo -f` will show the current value of USDT-NEO formatted as fiat (2 decimal places).

To retrieve information from your account, you need to do the following:
- Create an API key on bittrex.com - log in, click "Settings", click "API keys" and then "Add new key". Give your new key ONLY access to "Read info"! If you give your key access to buy/sell/withdraw you do so on your own risk and this program and its creator  is NOT responsible for anything that happens to your account, including, but not limited to, your funds or other assets you have on bittrex.com! This program will only read information from bittrex.com.
- Take the values you get for "key" and "secret" and enter them in the included secrets.json file.
- On unix/linux, make a directory called `trex` in the directory `.config` in your home directory.
- On Windows, it should work to make a directory called `.config` in `C:\Users\{yourusername}`, and then a directory called `trex` in the `.config` directory.
- Move the secrets.json file to the `trex` directory you created in the previous step.

Now you can read info from your account!

Examples:

`trex balances` will show the balance of all wallets where you have or have had anything.

`trex balances -n` will show the balance of all wallets with a non-zero balance.

`trex wallet neo` will show only your NEO wallet. Currently, this will fail if you try to look up a wallet where you have never had any funds/coins.

`trex orderhistory` will show the (recent) order history of your account. For some reason it seems to only go back about 1 month. I'll try to figure out how to go back further.

`trex orderhistory neo` will show the (recent) order history for NEO in your account. Replace NEO with any currency you want.

`trex openorders` will show any open orders you have.
`trex openorders neo` will show any open orders you have for NEO. Replace NEO with any currency you want.

`trex deposithistory` will show your deposit history.

`trex withdrawalhistory` will show your withdrawal history.
