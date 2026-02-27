---
id: rank_lists
title: Market Rank lists
slug: rank-lists
sidebar_position: 5
---

This API is used to get market rank lists.

<SDKLinks module="quote" klass="QuoteContext" method="rank_lists" />

:::info

[Business Command](../../socket/biz-command): `14`

:::

## Request

### Parameters

| Name        | Type    | Required | Description                                                                    |
| ----------- | ------- | -------- | ------------------------------------------------------------------------------ |
| market      | string  | Yes      | Request Market, for example:`US`                                               |
| quote_level | integer | Yes      | Quote Level(0: Delay 1:Nasdaq Basic 2:UTP)                                     |
| sort_by     | string  | Yes      | Sort Key, supported:last_done,prev_close,change_rate,volume,turnover,market_cap|
| sort_order  | integer | Yes      | Sort Order, 0:Desc 1:Asc                                                       |
| offset      | integer | Yes      | Return Offset                                                                  |
| count       | integer | Yes      | Return Counts                                                                  |



### Protobuf

```protobuf
message GetRankListForWhaleRequest {
    string market = 1;
    int32 quote_level = 2;
    string sort_by = 3;
    int32 sort_order = 4;
    int32 offset = 5;
    int32 count = 6;
}
```

### Request Example

## Response

### Response Properties

| Name            | Type     | Description          |
| --------------- | -------- | -------------------- |
| total_count     | int32    | Results total counts |
| timestamp       | int64    | Market timestamp     |
| list            | object[] | Rank lists           |
| ∟ symbol        | string   | Stock symbol         |
| ∟ name          | string   | Stock name           |
| ∟ last_done     | string   | Last done            |
| ∟ prev_close    | string   | Prev close           |
| ∟ open          | string   | Open price           |
| ∟ high          | string   | High price           |
| ∟ low           | string   | Low price            |
| ∟ change_rate   | string   | Change%              |
| ∟ volume        | string   | Volume               |
| ∟ turnover      | string   | Turnover             |
| ∟ market_cap    | string   | Market cap           |
| ∟ turnover_rate | string   | Turnover rate        |

### Protobuf

```protobuf
message GetRankListForWhaleResponse {
    message Item {
        string symbol = 1;
        string name = 2;
        string last_done = 3;
        string prev_close = 4;
        string open = 5;
        string high = 6;
        string low = 7;
        string change_rate = 8;
        string volume = 9;
        string turnover = 10;
        string market_cap = 11;
        string turnover_rate = 12;
    }

    int32 total_count = 1;
    int64 timestamp = 2;
    repeated Item list = 3;
}
```

### Response JSON Example

```json
{
    "total_count": 11150,
    "timestamp": "1772173505",
    "list": [
        {
            "symbol": "BRK.A",
            "name": "{\"zh-CN\":\"伯克希尔哈撒韦公司\",\"en\":\"Berkshire Hathaway Inc.\",\"zh-HK\":\"伯克希爾哈撒韋公司\"}",
            "last_done": "753250.000",
            "prev_close": "742000.000",
            "open": "742000.000",
            "high": "755500.000",
            "low": "742000.000",
            "change_rate": "1.52",
            "volume": "159",
            "turnover": "119380091",
            "market_cap": "1083686463250",
            "turnover_rate": "0.01"
        },
        {
            "symbol": "AZO",
            "name": "{\"zh-CN\":\"汽车地带公司\",\"en\":\"AutoZone, Inc.\",\"zh-HK\":\"汽車地帶公司\"}",
            "last_done": "3660.000",
            "prev_close": "3671.820",
            "open": "3675.000",
            "high": "3687.165",
            "low": "3620.000",
            "change_rate": "-0.32",
            "volume": "128173",
            "turnover": "468461618",
            "market_cap": "60638224860",
            "turnover_rate": "0.78"
        }
    ]
}
```

## Error Code

| Protocol Error Code | Business Error Code | Description        | Troubleshooting Suggestions                                   |
| ------------------- | ------------------- | ------------------ | ------------------------------------------------------------- |
