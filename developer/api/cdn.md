---
title: 'S4 静态CDN API'
sidebarTitle: '静态 CDN'
description: '介绍缤纷云 S4 的静态 CDN API。'
---

<Warning>
**注意**
当前处于测试阶段，暂不收费。收费时间及标准会另行通知，请您及时关注相应通知。
</Warning>

## 流量

<Tip>

**参数说明**

start_time - 起始时间，timestamp，秒

end_time   - 截止时间，timestamp，秒

period     - 统计宽度，hourly / daily / monthly 3 个值可选

</Tip>

### 边缘流量
```shell
curl "https://api.bitiful.com/cdn/data/<-- cdn domain -->/traffic?start_time=1719763200&end_time=1720108800&period=<-- hourly / daily / monthly -->" \
     -H 'Authorization: <-- API Token from: https://console.bitiful.com/apiToken -->'
```

### 回源流量
```shell
curl "https://api.bitiful.com/cdn/data/<-- cdn domain -->/traffic_origin?start_time=1719763200&end_time=1720108800&period=<-- hourly / daily / monthly -->" \
     -H 'Authorization: <-- API Token from: https://console.bitiful.com/apiToken -->'
```

## 请求

<Tip>

**参数说明**

start_time   起始时间，timestamp，秒

end_time     截止时间，timestamp，秒

period       统计宽度，hourly / daily / monthly 3 个值可选

</Tip>

### 边缘请求数
```shell
curl "https://api.bitiful.com/cdn/data/<-- cdn domain -->/request?start_time=1719763200&end_time=1720108800&period=<-- hourly / daily / monthly -->" \
     -H 'Authorization: <-- API Token from: https://console.bitiful.com/apiToken -->'
```

### 回源请求数
```shell
curl "https://api.bitiful.com/cdn/data/<-- cdn domain -->/request_origin?start_time=1719763200&end_time=1720108800&period=<-- hourly / daily / monthly -->" \
     -H 'Authorization: <-- API Token from: https://console.bitiful.com/apiToken -->'
```

## CDN 实时日志
仅支持 3 天内日志

<Tip>

**参数说明**

start_time - 起始时间，timestamp，纳秒，用作分页

codes      - 过滤 httpcode，英文逗号分隔

limit      - 一次性返回条数，最大值 1000

</Tip>

```shell
curl "https://api.bitiful.com/cdn/data/<-- cdn domain -->/logs?start_time=1720281600000000000&codes=200,403&limit=100" \
     -H 'Authorization: <-- API Token from: https://console.bitiful.com/apiToken -->'
```