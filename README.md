# WazirX Public Rest API
Here’s our public API handed to you on a silver platter. You can use it to build tickers, price comparison apps, or anything that helps the crypto community. Use it wisely and responsibily. ❤️

![Be Responsible](https://media2.giphy.com/media/MCZ39lz83o5lC/giphy.gif)

## General Information
1. Base API Endpoint: https://api.wazirx.com
1. All public api will return either JSON or Array object.

### Public API Endpoints

1. GET `/api/v2/market-status`  [Live link](https://api.wazirx.com/api/v2/market-status)

    > Market status will give your an overview of markets and assets. This is great when you want to track the configuration of our markets, get fees or status of withdrawal deposit, market configuration and more. This response is not recommended for price polling because accurate realtime price is not guaranteed as there could be some delays. We recommend using price ticker API for all price tracking activity.
    
    Response object will have 2 keys `markets`(all market related configs will be in this key) and `assets`(all assets related configs will be here). 
    ### Response:
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
                "buy": "485001.0",
                "type": "SPOT"
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
    
    
    1. **`markets` key have multiple market related configuration and description of every field in market is as below:**
    
        1. `baseMarket`: ticker code of base asset
        1. `quoteMarket`: ticker code of quote asset
        1. `minBuyAmount`: Minimum buy amount of base asset
        1. `minSellAmount`: Minumum sell amount of base asset
        1. `fee`: JSON Object consists of `bid` and `ask` order's maker-taker fee percentage
        1. `basePrecision`: Maximum precision of base asset, this the decimal point. 
        1. `quotePrecision`: Maximum  precision of quote asset
        1. `low`: 24 hrs lowest price of base asset
        1. `high`: 24 hrs highest price of base asset
        1. `last`: Last traded price in current market
        1. `open`: Market Open price 24hrs ago
        1. `volume`: Last 24hrs traded volume
        1. `sell`: Top ask order price
        1. `buy`: Top bid order price
        1. `type`: This defines the type of market, currently we have `SPOT` and `P2P`
    1. **`assets` key have multiple asset related configuration as described below:**
    
        1. `type`: asset code
        1. `name`: Display name of asset
        1. `withdrawFee`: Withdrawal fee of asset
        1. `minWithdrawAmount`: Minimum withdrawal amount in single transaction
        1. `maxWithdrawAmount`: Maximum withdrawal amount in single transaction
        1. `deposit`: Denotes whether deposit is enabled or disabled
        1. `withdrawal`: Denotes whether withdrawal is enabled or disabled


1. GET `/api/v2/tickers` [Live link](https://api.wazirx.com/api/v2/tickers)
    > Get the latest market heart-beat for all the market for last 24hrs.
    
    Returns JSON response which has active market data with all ticker related values.
    ### Response:
    ```
    {
        "btcinr": {
            "base_unit": "btc",
            "quote_unit": "inr",
            "low": "472005.0",
            "high": "508102.0",
            "last": "508100.0",
            "open": 490000,
            "volume": "0.2709",
            "sell": "508100.0",
            "buy": "481000.0",
            "name": "BTC/INR",
            "at": 1536732262
        },
        ...
    }
    ```
    Response have multiple key which denotes market data, this is in JSON. Find all the fields below:
    
    1. `base_unit`: ticker code of base market
    1. `quote_unit`: ticker code of quote asset
    1. `low`: 24 hrs lowest price of base asset
    1. `high`: 24 hrs highest price of base asset
    1. `last`: Last traded price in current market
    1. `open`: Market Open price 24hrs ago
    1. `volume`: Last 24hrs traded volume
    1. `sell`: Top ask order price
    1. `buy`: Top bid order price
    1. `name`: Display text of market
    1. `at`: Timestamp when ticker information is fetched
    
If you have any questions regarding APIs please reach out to us at http://support.wazirx.com
