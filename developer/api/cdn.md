---
title: 'S4 静态CDN API'
sidebarTitle: '静态 CDN'
description: '介绍缤纷云 S4 的静态 CDN API。'
---

## 获取控制台 API Token

前往控制台获取：[https://console.bitiful.com/apiToken](https://console.bitiful.com/apiToken)

## 流量

<Tip>

**参数说明**

**start_time** - 起始时间, timestamp, 秒

**end_time**   - 截止时间, timestamp, 秒

**period**     - 统计宽度, hourly / daily / monthly 3 个值可选

</Tip>

### 边缘流量
```shell
curl --get -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}" "https://api.bitiful.com/cdn/data/{cdn-domain}/traffic?start_time={start_time}&end_time={end_time}&period={period}"
```

### 回源流量
```shell
curl --get -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}" "https://api.bitiful.com/cdn/data/{cdn-domain}/traffic_origin?start_time={start_time}&end_time={end_time}&period={period}"
```

## 请求

<Tip>

**参数说明**

**start_time**   起始时间, timestamp, 秒

**end_time**     截止时间, timestamp, 秒

**period**       统计宽度, hourly / daily / monthly 3 个值可选

</Tip>

### 边缘请求数
```shell
curl --get -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}" "https://api.bitiful.com/cdn/data/{cdn-domain}/request?start_time={start_time}&end_time={end_time}&period={period}"
```

### 回源请求数
```shell
curl --get -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}" "https://api.bitiful.com/cdn/data/{cdn-domain}/request_origin?start_time={start_time}&end_time={end_time}&period={period}"
```

## CDN 实时日志
仅支持 3 天内日志

<Tip>

**参数说明**

**start_time**   起始时间,timestamp,纳秒,用作分页,例如:1723046499000000000

**codes**        过滤 httpcode. 2XX / 3XX / 4XX / 5XX / ALL 选其一，默认为 ALL

**limit**        一次性返回条数，最大值 1000

</Tip>

```shell
curl -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}" "https://api.bitiful.com/cdn/data/{cdn-domain}/logs?start_time={start_time}&codes={codes}&limit={limit}"
```

## CDN 刷新缓存

<Tip>

**请求说明**

Method: POST

Content-Type: application/json

**参数说明**

**type**          刷新类型，值为 url 或者 directory, 分别代表 刷新url 和 刷新目录

**url_list**     类型为字符串数组, 刷新的url/目录列表, 数组中元素数量不大于20, URL不能包含星号字符'*'. 如果URL中的目录或文件名包含'%'等特殊符号, 需要先进行URL编码.

</Tip>
```shell
curl -X POST -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}" "https://api.bitiful.com/cdn/cache/refresh" -d '{"type": "url", "url_list": ["https://xxx.com/yyy/zzz.png", "https://aaa.com/bbb/ccc.png"]}'
```
