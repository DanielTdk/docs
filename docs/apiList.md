## **交易所**
#### 1.获取交易所列表(有排序)  
    获取按照权重排名的交易所列表  

**HTTP请求**  
* GET /v2/exchange/rank_list/get

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| page_no | true | number | 页码 |
| page_size | true | number | 每页条数 |


**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| exchanges | true | array[exchange] | 交易所信息列表 |
| page_no | true | number | 页码 |
| page_size | true | number | 每页条数 |
| total_size | false | number | 总条数 |
| has_next | true | boolean | 是否有下一页 |

**exchange 参数列表**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| id | true | number | 交易所id |
| name | true | string | 名称 |
| logo | true | string | logo |
| synthetical_rank  | true | number | 排名 |
| tags  | true | array[string] | 类型 |
| coin_num | true | number | 币种数量 |
| subject_num | true | number | 币对数量 |
| spot_amount | true | string | 现货成交额 |

**响应示例**

```
{
    "page_no": 1,
    "page_size": 10,
    "total_size": 24,
    "has_next": true,
    "exchanges": [
        {
            "id": 29,
            "name": "BitMEX",
            "logo": "https://dist.huobicdn.com/8181c5986f654572bd2c38931362458f.jpeg",
            "synthetical_rank": 1,
            "tags": [],
            "coin_num": 6,
            "subject_num": 12,
            "spot_amount": "4820479457.81"
        },
        {
            "id": 4,
            "name": "币安",
            "logo": "http://cdn.san-fan.cn/exChange_0_KeofKG_20180920.png",
            "synthetical_rank": 2,
            "tags": [],
            "coin_num": 144,
            "subject_num": 393,
            "spot_amount": "1269689287.15"
        },
    ]
}
```


#### 2.获取交易所下payment列表  
    获取交易所的payment列表  

**HTTP请求**  
* GET /v2/exchange/payments/get

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| exchange_id | true | number | 交易所id |


**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| exchange_id | true | number | 交易所id |
| payments | true | array[string] | payment列表 |

**返回示例**


```
{
    "exchange_id": 2,
    "payments": [
        "USDT",
        "BTC",
        "ETH",
        "HT",
        "HUSD"
    ]
}
```
#### 3.获取交易所详情  
    获取交易所详情数据  
    fields可以为name,payments,logo,url,introduction等，fields不传默认返回id,name

**HTTP请求**  
* GET /v2/exchange/get

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| exchange_ids | true | number | 交易所id,多个以逗号分隔 |
| fields | false | string | 多个以逗号分隔 |



**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| exchanges | true | array[exchange] | 交易所列表 |

**exchange 参数列表**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| id | true | number | 交易所id |
| name | true | string | 名称 |
| logo | true | string | logo |
| url | true | string | 网址 |
| introduction | true | string |  简介|
| tags | true | array[string] | 类型集合 |
| amount_rank  | true | number | 成交额排名 |
| synthetical_rank  | true | number | 综合排名 |
| subject_num  | true | number | 币对数量 |
| spot_amount| true | string | 24小时现货交易额（人民币计价)|
| contract_amount | true | string | 24小时合约交易额（人民币计价）|
| has_contract | true | number |  是否有合约（0：没有，1：有) |
| btc_rmb_price | true | string |BTC的人民币价格（换算成BTC使用） |
| payments | true | array[string] | payment列表 |


**返回示例**


```
{
    "exchanges": [
        {
            "id": 2,
            "name": "火币",
            "logo": "https://cdn.san-fan.cn/exChange_0_6H3q9x_20180919.png",
            "url": "https://www.huobi.pro",
            "introduction": "",
            "tags": [],
            "amount_rank": 3,
            "synthetical_rank": 3,
            "subject_num": 415,
            "spot_amount": "2335093045.69",
            "contract_amount": "0",
            "has_contract": 0,
            "btc_rmb_price": "78748.89608755",
            "payments": [
                "USDT",
                "BTC",
                "ETH",
                "HT",
                "HUSD"
            ]
        },...
    ]
}
```

## **币种**

#### 1.获取币种详情
    获取币种详情数据  
**HTTP请求**  
* GET /v2/coin/get

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coin_ids | true | string | 币种id,多个以逗号分隔 |
| fields | false | string | 字段集合，fields的值可以为code,name,cn_name,en_name,last,open 等数据字典，多个以逗号分隔 如果fields不传，则默认只返回 id,last 2个字段 |



**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coins | true | array[coin] | 币种信息列表 |

**coin 参数列表**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| id | true | number | id |
| code  | true | string | 币种code |
| brief | true | string | 简介 |
| cn_name| true | string | 中文名|
| en_name | true | string | 英文名|
| volume | true | string | 24小时成交量 |
| amount | true | string | 24小时成交额 |
| circulation_market_value | true | number |  流通市值|
| global_rank | true | number | 全网市值排名 |
| last  | true | number | 当前价 |
| open  | true | number | 收盘价 |

**返回示例**


```
{
    "coins": [
        {
            "circulation_market_value": "204826702577",
            "brief": "点对点价值传输的p2p去中心化支付系统",
            "volume": "2121342.87511344",
            "id": 563,
            "global_rank": 1,
            "code": "BTC",
            "last": "78748.89608755",
            "open": "54693.55840268",
            "cn_name": "比特币",
            "en_name": "Bitcoin Core"
        },...
    ]
}
```
#### 2.获取币种的payment列表
    获取币种的payment列表  

**HTTP请求**  
* GET /v2/coin/payments/get  

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coin_id | true | number | 币种id |
| scopes | false | string | scopes默认传global，即查询整个市场；也可传交易所ids如2,6,12查询某几个交易所 |


**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coin_id | true | number | 币种id |
| payments | true | array[string] | payment列表 |

**返回示例**


```
{
    "coin_id": 627,
    "payments": [
        "USDT",
        "BTC",
        "USD",
        "QC",
        "TUSD"
    ]
}
```
#### 3.获取币种的交易对ID列表(聚合)
    返回币种所有市场下的币对id列表 

**HTTP请求**  
* GET /v2/coin/union_subject/id/get  

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coin_id | true | number | 币种id |


**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coin_id | true | number | 币种id |
| subject_ids | true | array[number] | 币对id列表 |

**返回示例**


```
{
    "coin_id": 627,
    "subject_ids": [
        1183,
        318,
        536,
        1557,
        650
    ]
}
```
#### 4.获取币种上线的交易所列表
    获取币种上线的交易所列表数据(分页)

**HTTP请求**  
* GET /v2/coin/exchanges/id/get   

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coin_id | true | number | 币种id |
| page_no | true | number | 页码 默认1|
| page_size | true | number | 每页条数 默认10 |

**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coin_id | true | number | 币种id |
| exchange_ids | true | array[number] | 交易所id列表 |
| page_no | true | number | 页码 |
| page_size | true | number | 每页条数 |
| total_size | false | number | 总条数 |
| has_next | true | boolean | 是否有下一页 |

**返回示例**

```
{
    "page_no": 1,
    "page_size": 15,
    "total_size": 11,
    "has_next": false,
    "coin_id": 627,
    "exchange_ids": [
        4,
        2,
        3,
        7,
        6,
        1,
        14,
        28,
        5,
        16,
        15
    ]
}
```
#### 5.获取币种的交易对ID列表(区分交易所、payment)
    分页获取单个币种的交易对id列表

**HTTP请求**  
* GET /v2/coin/subjects/id/get    

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coin_id | true | number | 币种id |
| exchange_id | false | number | 交易所id |
| payment | true | string | payment |
| page_no | true | number | 页码 默认1|
| page_size | true | number | 每页条数 默认10 |

**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coin_id | true | number | 币种id |
| subject_ids | true | array[number] | 币对id列表 |
| page_no | true | number | 页码 |
| page_size | true | number | 每页条数 |
| total_size | false | number | 总条数 |
| has_next | true | boolean | 是否有下一页 |

**返回示例**


```
{
    "page_no": 1,
    "page_size": 15,
    "total_size": 10,
    "has_next": false,
    "coin_id": 627,
    "subject_ids": [
        318,
        536,
        650,
        766,
        1183,
        1557,
        2333,
        2674,
        2823,
        3718
    ]
}
```

#### 6.获取币种市值榜单列表
    获取币种市值榜，即按市值排序的币种列表(分页)

**HTTP请求**  
* GET /v2/coin/market_value_rank_list/get    

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| page_no | false | number | 页码 默认1|
| page_size | false | number | 每页条数 默认10 |

**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| coins | true | array[coin] | 币种信息列表 |
| page_no | true | number | 页码 |
| page_size | true | number | 每页条数 |
| total_size | false | number | 总条数 |
| has_next | true | boolean | 是否有下一页 |

**coin 参数列表**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| id | true | number | id |
| code  | true | string | 币种code |
| brief | true | string | 简介 |
| name| true | string | 币种名称|
| market_value  | true | string | 市值|
| volume | true | string | 24小时成交量 |
| amount | true | string | 24小时成交额 |
| global_rank | true | number | 全网市值排名 |
| last  | true | number | 当前价 |
| open  | true | number | 收盘价 |
| trend_chart  | false |object | 趋势图数据(暂不提供) |


**返回示例**


```
{
    "page_no": 1,
    "page_size": 10,
    "total_size": 599,
    "has_next": true,
    "coins": [
        {
            "id": 563,
            "global_rank": 1,
            "code": "BTC",
            "market_value": "204826702577",
            "last": "78748.89608755",
            "open": "54693.55840268",
            "volume": "2523887.52396267",
            "brief": "点对点价值传输的p2p去中心化支付系统",
            "name":"比特币"
        },...
    ]
}
```

#### 7.币种搜索
    币种搜索(分页)  
    模糊搜索币种，code和name必传1个，name范围包含中文名和英文名  

**HTTP请求**  
* GET /v2/coin/query    

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| code | false | string | 币种code|
| name | false | string | 币种名称|
| page_no | false | number | 页码 默认1|
| page_size | false | number | 每页条数 默认10 |

**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| code | true | string | 币种code|
| name | true | string | 币种名称|
| coin_ids | true | array[number] | 币种id列表 |
| page_no | true | number | 页码 |
| page_size | true | number | 每页条数 |
| total_size | false | number | 总条数 |
| has_next | true | boolean | 是否有下一页 |

**返回示例**

```
{
    "page_no": 1,
    "page_size": 10,
    "total_size": 5,
    "has_next": false,
    "code": "b",
    "name": "比特币",
    "coin_ids": [
        563,
        539,
        537,
        540,
        3493
    ]
}
```
## **交易对**
#### 1.获取交易对详情
    交易对信息获取  
    subject_ids，coin_id，code,  exchange_id 四个参数至少传1个
    且code和coin_id不可同时传递
**HTTP请求**  
* GET /v2/subject/get    

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| code | false | string | 币种code|
| coin_id | false | number | 币种id|
| exchange_id | false | number | 交易所id|
| subject_ids | false | string | 币对id集合，多个用逗号分隔|
| fields | false | string | 返回字段集合可以为subject,coin_id,exchange_name,exchange_logo,last,open 等数据字典，多个以逗号分隔，默认为 id,last |
| page_no | false | number | 页码 默认1|
| page_size | false | number | 每页条数 默认10 |

**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| subjects | true | array[subject] | 币对信息列表 |
| page_no | true | number | 页码 |
| page_size | true | number | 每页条数 |
| total_size | false | number | 总条数 |
| has_next | true | boolean | 是否有下一页 |

**subject 参数列表**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| id | true | number | 币对id |
| subject | true | string | 名称 |
| code | true | string | 币种code |
| coin_id | true | number | 币种id|
| exchange_id | true | number | 交易所id|
| exchange_name | true | string | 交易所名称 |
| exchange_logo | true | string | 交易所logo地址 |
| last | true | string | 当前价 |
| open | true | string | 开盘价 |
| high | true | string | 今日最高 |
| low | true | string | 今日最低 |
| volume | true | string | 24小时成交量 |

| amount | false | string | 24小时成交额 |
| payment_rmb_price | true | string | payment对人民币价格 |

**返回示例**

```
{
    "subjects": [
        {
            "id": 255,
            "subject": "BTC/USDT",
            "code": "BTC",
            "coin_id": 563,
            "exchange_id": 2,
            "exchange_name": "火币",
            "exchange_logo": "https://cdn.san-fan.cn/exChange_0_6H3q9x_20180919.png",
            "last": "10375.17",
            "open": "10014.06",
            "high": "10480",
            "low": "9990.85",
            "volume": "0",
            "amount": "0",
            "payment_rmb_price": "6.9338"
        }
    ],
    "page_no": 1,
    "page_size": 2,
    "total_size": 2,
    "has_next": false
}
```

#### 2.获取资金流向数据
    获取资金流向

**HTTP请求**  
* GET /v2/subject/amount_flow/get  

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| subject_id | true | number | 币对id |
| day | false | number | 天数（资金流向为1，7日流入流出为7，目前只支持1和7） |
| style | true | string | 取值plain/combine，当为plain的时候，各个字段分几个数组；当为combine时，数据的所有字段在一个json对象里 |

**响应数据**  

> plain

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| subject_id | true | number | 币对id|
| in_amounts | true | array[string] | 流入 |
| out_amounts | true | array[string] | 流出 |
| times | true | array[number] | 时间列表 |

> combine

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| subject_id | true | number | 币对id|
| data_list | true | array[item] | item数据列表 |

**item 参数列表**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| in_amount | true | string | 流入额 |
| out_amount | true | string | 流出额|
| ts | true | number | 时间 |

**返回示例**

```
style=plain时，返回数据结构：
{
  "subject_id": 255,
  "in_amounts": [
    "657843685.57684",
    "658733.5483",
    "7589329457.75832"
  ],
  "out_amounts": [
    "657843685.57684",
    "658733.5483",
    "7589329457.75832"
  ],
  "times": [
    1507834500000,
    1507834500000,
    1507834500000
  ]
}

style= combine时，返回数据结构：
{
  "subject_id": 255,
  "data_list": [
    {
      "in_amount": "657843685.57684",
      "out_amount": "657843685.57684",
      "ts": 1507834500000
    },
    {
      "in_amount": "657843685.57684",
      "out_amount": "657843685.57684",
      "ts": 1507834500000
    },
    {
      "in_amount": "657843685.57684",
      "out_amount": "657843685.57684",
      "ts": 1507834500000
    }
  ]
}
```


#### 3.获取交易对k线数据
    获取交易对的K线
    
**HTTP请求** 
 
* GET /v2/subject/kline/get   

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| subject_id | true | number | 币对id |
| period | false | string |k线类型 默认1d 取自支持类型 |
| style | true | string | 默认plain,取值plain/combine，当为plain时，各个字段分几个数组；当为combine时，数据的所有字段在一个json对象里 |

**响应数据**  

> plain

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| subject_id | true | number | 币对id|
| price_scale | true | number | 价格精度 |
| supported_resolutions | true | array[string] | 支持类型列表 |
| times | true | array[number] | 时间戳列表 |
| opens | true | array[string] | 开盘价列表 |
| closes | true | array[string] | 收盘价列表 |
| highs | true | array[string] | 今日最高价列表 |
| lows | true | array[string] | 今日最低价列表 |
| volumes | true | array[string] | 数量列表 |


> combine

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| subject_id | true | number | 币对id|
| price_scale | true | number | 价格精度 |
| supported_resolutions | true | array[string] | 日期类型列表 |
| times | true | array[kline] | kline列表 |

**kline 参数列表**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| ts | true | number | 时间戳 |
| open | true | string | 开盘价 |
| close | true | string | 收盘价 |
| high | true | string | 今日最高价 |
| low | true | string | 今日最低价 |
| volume | true | string | 数量 |

**返回示例**


```
当style=plain时,返回的数据结构：
{
  "subject_id": 255,
  "price_scale":1000000000,
  "supported_resolutions": [
    "1m",
    "3m",
    "5m",
    "1h",
    "2h",
    "1d",
    "3d",
    "1w",
    "1M",
    "1y"
  ],
  "times": [
    1519603200000,
    1519689600000,
    1519776000000
  ],
  "opens": [
    "176.35",
    "179.1",
    "179.26"
  ],
  "highs": [
    "179.39",
    "180.48",
    "180.615"
  ],
  "lows": [
    "176.21", 
    "178.16",
    "178.05"
  ],
  "closes": [
    "178.97",
    "178.39",
    "178.12"
  ],
  "volumes": [
    "36886.432",
    "3868.5165",
    "3360.4574"
  ]
}

style= combine时，返回数据结构：
{
  "subject_id": 255,
  "price_scale":1000000000,
  "supported_resolutions": [
    "1m",
    "3m",
    "5m",
    "1h",
    "2h",
    "1d",
    "3d",
    "1w",
    "1M",
    "1y"
  ],
  "klines": [
    {
      "open": "176.35",
      "high": "179.39",
      "low": "178.97",
      "close": "178.97",
      "volume": "36886.432",
      "ts": 1519603200000
    },
    {
      "open": "176.35",
      "high": "179.39",
      "low": "178.97",
      "close": "178.97",
      "volume": "36886.432",
      "ts": 1519603200000
    },
    {
      "open": "176.35",
      "high": "179.39",
      "low": "178.97",
      "close": "178.97",
      "volume": "36886.432",
      "ts": 1519603200000
    }
  ]
}
```

#### 4.获取交易对的交易所列表

查询有这个交易对的交易所列表

**HTTP请求**  
* GET /v2/subject/exchanges/id/query  

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| subject | true | string | 币对名称 |

**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| subject | true | string | 币对名称 |
| exchange_ids | true | array[number] | 交易所id列表 |

**返回示例**

```
{
    "subject": "BTC_USDT",
    "exchange_ids": [
        16,
        1,
        2,
        3,
        4,
        5,
        6,
        28,
        14,
        15
    ]
}
```

#### 5.涨跌幅列表(区分交易所)
  获取某个交易所下币对涨跌幅榜  
    
**HTTP请求**  
* GET /v2/exchange/raise_fall_list    

**请求参数**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| exchange_id | true | number | 交易所id|
| direction | false | number | 1:涨幅 2:跌幅|
| type | false |string | coin/subject|

**响应数据**  

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| exchange_id | true | number | 交易所id |
| direction | false | number | 1:涨幅 2:跌幅|
| subjects | true | array[subject] | 币对信息列表 |
| total_size | true | number | 总数量 |

**subject 参数列表**

| 参数名 | 是否必须 | 类型 | 说明 |
| --- | --- | --- | --- |
| id | true | number | 币对id |
| subject | true | string | 名称 |
| coin_id | true | number | 币种id|
| last | true | string | 当前价 |
| open | true | string | 开盘价 |
| high | true | string | 今日最高 |
| low | true | string | 今日最低 |
| volume | true | string | 24小时成交量 |
| amount | true | string | 24小时成交额 |
| payment_rmb_price | true | string | payment对人民币价格 |

**返回示例**


```
{
    "exchange_id": 2,
    "direction": 2,
    "total_size": 50,
    "subjects": [
        {
            "id": 2250,
            "subject": "FAIR/ETH",
            "last": "0.00002633",
            "open": "0.00003021",
            "high": "0.00003388",
            "low": "0.00002602",
            "volume": "38808493.48",
            "amount": "501.61148947",
            "code_id": 630
        },...
    ]
}
```
## **WEBSOCKET**

#### 建立连接
成功返回：
{
  "status": "ok",
  "ts": 1565695283646
}

失败返回：
{
  "status": "error",
  "error_msg": "network exception",
  "ts": 1565696330367
}  
#### 心跳  
长连接建立成功后服务端每隔10秒会向客户端发送ping消息里面是一整型数据，   
如：{"ping": 1565696330367}  
客户端收到数据后要立即把数据发送回服务器，     
如：{"pong": 1565696330367}       
如果ping的次数超过2次,还没收到客户端的pong，服务端则主动断开本次连接。  

#### 公共参数

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
| globalSwitch | true | number | 0 | socket开关 1：打开 0 关闭 |

#### 关闭连接

**请求参数** 

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
| globalSwitch | true | number | 0 | 传0即可 |

#### 取消主题订阅
**请求参数**    

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
| globalSwitch | true | number | 0 | socket开关 1：打开 0 关闭 |
| params | true | array[param] |  |  |

**param 参数列表**  

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
|    data_type | true | string |  |coin --币种， subject_list --币对列表 subject_detail --币对详情 |
|    typeSwitch | true | number |  |  传0即关闭该data_type主题 |


#### 请求数据
    
**请求参数**    

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
| globalSwitch | true | number | 0 | socket开关 1：打开 0 关闭 |
| params | true | array[param] |  |  |

**param 参数列表**  

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
|    data_type | true | string |  |coin --币种， subject_list --币对列表 subject_detail --币对详情 |
|    ids | true | string |  |  id列表，多个以逗号分隔|
|    typeSwitch | true | number |  |  类型开关1：打开，0：关闭 |
|    fields | true | string |  | 返回字段集合，多个以逗号分隔 可取id，last，open，high，low，volume，amount|

**请求体示例**  

```

{
    globalSwitch : 0,
    params:[
        {
            data_type: "coin",
            ids: "1,2"
            typeSwitch: 1
            fields: "id，last，open，high，low，volume，amount"
        },
    ]
}  
```




-------

**返回数据说明**

> data_type = coin

**返回参数**

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
|    data_type | true | string |  |coin --币种， subject_list --币对列表 subject_detail --币对详情 |
|    data | true | array[item] |  |  数据列表|

**item 参数列表** 

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
|    id | true | number |  | 币种id |
|    last | true | string |  |  最新价|


```
{
  "data_type":"coin",
  "data": [
    {
      "id":23,
      "last":"2342.543"
    },
    {
      "id":13,
      "last":"42.543"
    }
  ]
}
```

>  data_type = subject_list 没传fields时


**返回参数**

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
|    data_type | true | string |  |coin --币种， subject_list --币对列表 subject_detail --币对详情 |
|    data | true | array[item] |  |  数据列表|

**item 参数列表** 

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
|    subject_id | true | number |  | 币对id |
|    last | true | string |  |  最新价|



```
{
  "data_type":"subject_list",
  "data": [
    {
      "id": 419,
      "last": "11424.29"
    },
    {
      "subject_id": 4626,
      "last": "11397.03"
    },
    {
      "subject_id": 4708,
      "last": "11407.43"
    }
  ]
}
```

> data_type = subject_list 返回所有字段数据格式


**返回参数**

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
|    data_type | true | string |  |coin --币种， subject_list --币对列表 subject_detail --币对详情 |
|    data | true | array[item] |  |  数据列表|

**item 参数列表** 

| 参数名称 | 是否必须 | 类型  | 描述 |
| :-- | :-- | :-- | :-- |
| id | true | number | 币对id |
| last | true | string | 当前价 |
| open | true | string | 开盘价 |
| high | true | string | 今日最高 |
| low | true | string | 今日最低 |
| volume | true | string | 24小时成交量 |
| amount | true | string | 24小时成交额 |
| payment_rmb_price | true | string | payment对人民币价格 |



```
{
  "data_type":"subject_list",
  "data": [
    {
      "id": 419,
      "last": "11424.29",
      "open": "11378.95",
      "high": "11599",
      "low": "11301.17",
      "volume": "0",
      "amount": "0",
      "payment_rmb_price":"6.97"
    },
  ]
}
```

> data_type = subject_detail
    
**返回参数**

| 参数名称 | 是否必须 | 类型 | 默认值 | 描述 |
| :-- | :-- | :-- | :-- | :-- |
|    data_type | true | string |  |coin --币种， subject_list --币对列表 subject_detail --币对详情 |
|    data | true | array[item] |  |  数据列表|

**item 参数列表** 

| 参数名称 | 是否必须 | 类型  | 描述 |
| :-- | :-- | :-- | :-- |
| id | true | number | 币对id |
| last | true | string | 当前价 |
| open | true | string | 开盘价 |
| high | true | string | 今日最高 |
| low | true | string | 今日最低 |
| volume | true | string | 24小时成交量 |
| amount | true | string | 24小时成交额 |
| payment_rmb_price | true | string | payment对人民币价格 |
| history_high | true | string | 历史最高价 |
| history_low | true | string | 历史最低价 |
| committee_ratio | true | string | 委比 |
| volume_ratio | true | string | 量比 |
| circulation | true | string | 流通量 |
| market_value | true | string | 流通市值 |
| buy_overview | true | buyOverview | 买单详情 |
| sell_overview | true | sellOverview |卖单详情 |
| asks | true | array[array[string]] | 买十档（二维数组中的一维数组角标0为价格，角标1为数量 |
| bids | true | array[array[string]] | 卖十档（二维数组中的一维数组角标0为价格，角标1为数量）|

**buyOverview 参数列表**

| 参数名称 | 是否必须 | 类型  | 描述 |
| :-- | :-- | :-- | :-- |
| big_volume | true | number | 大单单量 |
| medium_volume | true | string | 中单单量 |
| small_volume | true | string | 小单单量 |
| total_amount | true | string | 今日总流入额 |

**sellOverview 参数列表**

| 参数名称 | 是否必须 | 类型  | 描述 |
| :-- | :-- | :-- | :-- |
| big_volume | true | number | 大单单量 |
| medium_volume | true | string | 中单单量 |
| small_volume | true | string | 小单单量 |
| total_amount | true | string | 今日总流出额 |

```
{
  "data_type":"subject_detail",
  "data": {
    "id": 419,
    "last": "11424.29",
    "open": "11378.95",
    "high": "11599",
    "low": "11301.17",
    "volume": "0",
    "amount": "0",
    "payment_rmb_price":"6.97",
    "history_high": "19700",
    "history_low": "1",
    "committee_ratio": "0.234",
    "volume_ratio": "0.40",
    "circulation": "17870198",
    "market_value": "1434738762345.234",
    "buy_overview": {
      "big_volume": 609,
      "medium_volume": 11655,
      "small_volume": 71357,
      "total_amount": "83998275.34"
    },
    "sell_overview": {
      "big_volume": 500,
      "medium_volume": 8438,
      "small_volume": 62822,
      "total_amount": "65911567.768"
    },
    "asks": [
      [
        "11338.85",
        "0.088195"
      ],
      [
        "11338.91",
        "0.35"
      ],
      [
        "11339.34",
        "0.02"
      ],
      [
        "11339.68",
        "0.00209"
      ],
      [
        "11340.0",
        "0.002643"
      ],
      [
        "11340.02",
        "0.101899"
      ],
      [
        "11341.3",
        "0.8"
      ],
      [
        "11341.31",
        "0.25"
      ],
      [
        "11341.33",
        "0.050841"
      ],
      [
        "11341.34",
        "0.7"
      ]
    ],
    "bids": [
      [
        "11338.07",
        "0.022378"
      ],
      [
        "11337.93",
        "0.0002"
      ],
      [
        "11337.0",
        "0.00064"
      ],
      [
        "11336.72",
        "0.050853"
      ],
      [
        "11336.71",
        "0.503"
      ],
      [
        "11336.68",
        "1.193"
      ],
      [
        "11336.57",
        "0.2"
      ],
      [
        "11336.54",
        "0.37"
      ],
      [
        "11336.22",
        "0.047"
      ],
      [
        "11335.89",
        "0.004962"
      ]
    ]
  }
}

```


