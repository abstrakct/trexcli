# trex

## What?
trex is a python program that can get information from bittrex.com's API.

## Requirements
- API bindings provided by https://github.com/ericsomdahl/python-bittrex - so you need to install that before using the program. It can be installed with pip or from https://pypi.python.org/pypi/python-bittrex
- python 3.5 or higher
- I have personally only tested/used it on linux, but it should work on any platform as long as the above requirements are met.

## Why?
I initially wrote this because I needed a way to get the current value of certain cryptocurrencies in plain and simple text format. Since I later on wanted simple access to information from my account on bittrex, it evolved to retrieve other kinds of information as well.

For now it does NOT support placing buy/sell orders on bittrex, although that would be fairly easy to implement. This is because of the potential security risk involved, and the risk involved in giving a 3rd party app access to buying/selling/withdrawing from your account. I will do more research to find out how it can be done securely before implementing it.

## How?
`trex -h` is good starting point!

But let's look at some examples.

`trex ticker btc neo` will show the current value of BTC-NEO formatted as satoshis (8 decimal places).

`trex ticker usdt neo -f` will show the current value of USDT-NEO formatted as fiat (2 decimal places).



