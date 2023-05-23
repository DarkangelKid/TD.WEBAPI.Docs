---
title: "Logging"
description: "Logging TD Web API."
lead: "Logging TD Web API."
date: 2021-08-24T11:40:05+05:30
lastmod: 2021-12-12T11:21:11+05:30
draft: false
images: []
menu:
  dotnet-webapi-boilerplate:
    identifier: "logging"
    name: "Logging"
    parent: "fundamentals"
weight: 11
toc: true
---

Cấu hình trong `src/Host/Configurations/logger.json`.


## Console

Mặc định sử dụng Console Logging. Package sử dụng - `Serilog.Sinks.Console`

```
builder.Host.UseSerilog((_, config) =>
{
    config.WriteTo.Console()
    .ReadFrom.Configuration(builder.Configuration);
});
```

## File

Log đuợc ghi dưới định dạng JSON và lưu trong file
Package sử dụng - `Serilog.Sinks.File`

```
"Name": "File",
"Args": {
  "path": "Logs/logs.json",
  "formatter": "Serilog.Formatting.Json.JsonFormatter, Serilog",
  "rollingInterval": "Day",
  "restrictedToMinimumLevel": "Information",
  "retainedFileCountLimit": 5
}
```


## SEQ

Package sử dụng - `Serilog.Sinks.Seq`

Cài đặt SEQ trước nếu có ý định sử dụng
```
"Name": "Seq",
"Args": {
  "serverUrl": "http://localhost:5341"
}
```


## Elastic Search

Điều kiện: đã cài Kibana và ElasticSearch (có thể dùng docker)

Mặc định
- Kibana runs on port 5601 - http://localhost:5601
- Elastic Search runs on port 9200 - http://localhost:9200

Package sử dụng - `Serilog.Sinks.Elasticsearch`

```
"Name": "Elasticsearch",
"Args": {
  "nodeUris": "http://localhost:9200;",
  "indexFormat": "DN.WebApi-logs-{0:yyyy.MM}",
  "numberOfShards": 2,
  "numberOfReplicas": 1,
  "restrictedToMinimumLevel": "Information"
}
```
