---
title: 'S4 静态CDN API'
sidebarTitle: '静态 CDN'
description: '介绍缤纷云 S4 的静态 CDN API。'
---

## 获取 API Token

前往控制台获取：[https://console.bitiful.com/apiToken](https://console.bitiful.com/apiToken)

## 流量

<Tip>

**参数说明**

**start_time** - 起始时间，timestamp，秒

**end_time**   - 截止时间，timestamp，秒

**period**     - 统计宽度，hourly / daily / monthly 3 个值可选

</Tip>

### 边缘流量
```shell
curl --get "https://api.bitiful.com/cdn/data/{cdn-domain}/traffic" \ 
    -d "start_time=1719763200" \
    -d "end_time=1720108800" \
    -d "period={hourly | daily | monthly}" \
    -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}"
```

### 回源流量
```shell
curl --get "https://api.bitiful.com/cdn/data/{cdn-domain}/traffic_origin" \ 
    -d "start_time=1719763200" \
    -d "end_time=1720108800" \
    -d "period={hourly | daily | monthly}" \
    -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}"
```

## 请求

<Tip>

**参数说明**

**start_time**   起始时间，timestamp，秒

**end_time**     截止时间，timestamp，秒

**period**       统计宽度，hourly / daily / monthly 3 个值可选

</Tip>

### 边缘请求数
```shell
curl --get "https://api.bitiful.com/cdn/data/{cdn-domain}/request" \ 
    -d "start_time=1719763200" \
    -d "end_time=1720108800" \
    -d "period={hourly | daily | monthly}" \
    -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}"
```

### 回源请求数
```shell
curl --get "https://api.bitiful.com/cdn/data/{cdn-domain}/request_origin" \ 
    -d "start_time=1719763200" \
    -d "end_time=1720108800" \
    -d "period={hourly | daily | monthly}" \
    -H "Authorization: {API Token from: https://console.bitiful.com/apiToken}"
```

## CDN 实时日志
仅支持 3 天内日志

<Tip>

**参数说明**

**start_time**   起始时间，timestamp，纳秒，用作分页

**codes**        过滤 httpcode，2XX / 3XX / 4XX / 5XX / ALL 选其一，默认为 ALL

**limit**        一次性返回条数，最大值 1000

</Tip>

```shell
curl --get "https://api.bitiful.com/cdn/data/<-- cdn domain -->/logs"
    -d "start_time=1720281600000000000" \
    -d "codes={2XX | 3XX | 4XX | 5XX | ALL}" \
    -d "limit=100" \
    -H 'Authorization: {API Token from: https://console.bitiful.com/apiToken}'
```