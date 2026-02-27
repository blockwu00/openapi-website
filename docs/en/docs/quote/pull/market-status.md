---
id: market_status
title: Market Status
slug: market-status
sidebar_position: 5
---

This API is used to get market rank lists.

<SDKLinks module="quote" klass="QuoteContext" method="market_status" />

:::info

[Business Command](../../socket/biz-command): `14`

:::

## Request

### Parameters

| Name        | Type    | Required | Description                        |
| ----------- | ------- | -------- | ---------------------------------- |
| market      | string  | Yes      | Request Market, for example:`US`   |
| is_delay    | boolean | Yes      | If use delay quote data            |


### Protobuf

```protobuf
message GetMarketStatusForWhaleRequest {
    string market = 1;
    bool is_delay = 2;
}

```

### Request Example

## Response

### Response Properties

| Name          | Type     | Description                                                                    |
| ------------- | -------- | ------------------------------------------------------------------------------ |
| market        | string   | Market                                                                         |
| timestamp     | int64    | Request timestamp                                                              |
| market_status | string   | Market status. US: Trading,PreMarketTrading,PostMarketTrading,Overnight,Closed |

### Protobuf

```protobuf
message GetMarketStatusForWhaleResponse {
    string market = 1;
    int64 timestamp = 2;
    string market_status = 3;
}
```

### Response JSON Example

```json
{
    "market": "US",
    "timestamp": "1772159329",
    "market_status": "Overnight"
}
```

## Error Code

| Protocol Error Code | Business Error Code | Description        | Troubleshooting Suggestions                                   |
| ------------------- | ------------------- | ------------------ | ------------------------------------------------------------- |
