# WazirX Public Rest API
Here’s our public API handed to you on a silver platter. You can use it to build tickers, price comparison apps, or anything that helps the crypto community. Use it wisely and responsibily. ❤️

## General Information
1. Base API Endpoint: https://api.wazirx.com
1. All public api will return either JSON or Array object.

### Public API Endpoints

1. GET `/api/v2/market-status`

    Returns JSON object which has current market and currency status. Response object will have 2 keys `markets`(all market related configs will be in this key) and `assets`(all currency related configs will be here). 
    ##### Response:
    ```
    {
        "markets": [
            {
                "baseMarket": "btc",
                "quoteMarket": "inr",
                "minBuyAmount": 0.001,
                "minSellAmount": 0.001,
                "fee": {
                    "bid": {
                        "maker": 0.001,
                        "taker": 0.0025
                    },
                    "ask": {
                        "maker": 0.001,
                        "taker": 0.0025
                    }
                },
                "basePrecision": 4,
                "quotePrecision": 2,
                "low": "460001.01",
                "high": "505000.0",
                "last": "480102.0",
                "open": 505002,
                "volume": "0.2071",
                "sell": "490000.0",
                "buy": "485001.0"
            },
            ...
        ],
        "assets": [
            {
                "type": "inr",
                "name": "Rupee",
                "withdrawFee": 0,
                "minWithdrawAmount": 50,
                "maxWithdrawAmount": 50000,
                "deposit": "enabled",
                "withdrawal": "enabled"
            },
            ...
        ]
    }
    ```
    
    `markets` key have multiple market related configuration and description of every field in market is as below:
    
    1. `baseMarket`: code of base currency
    1. `quoteMarket`: code of quote currency
    1. `minBuyAmount`: Minimum buy amount of base currency
    1. `minSellAmount`: Minumum sell amount of base currency
    1. `fee`: JSON Object consists of `bid` and `ask` order's maker-taker fee percentage
    1. `basePrecision`: Maximum precision of base currency 
    1. `quotePrecision`: Maximum  precision of quote currency
    1. `low`: 24 hrs lowest price of base currency
    1. `high`: 24 hrs highest price of base currency
    1. `last`: Last traded price in current market
    1. `open`: Market Open price
    1. `volume`: Last 24hrs traded volume
    1. `sell`: Top ask order price
    1. `buy`: Top bid order price
    
    `assets` key have multiple currency related configuration as described below:
    
    1. `type`: Currency code
    1. `name`: Display name of asset
    1. `withdrawFee`: Withdrawal fee of asset
    1. `minWithdrawAmount`: Minimum withdrawal amount in single transaction
    1. `maxWithdrawAmount`: Maximum withdrawal amount in single transaction
    1. `deposit`: Denotes whether deposit is enabled or disabled
    1. `withdrawal`: Denotes whether withdrawal is enabled or disabled


    If you have any questions regarding APIs please reach out to us at http://support.wazirx.com
