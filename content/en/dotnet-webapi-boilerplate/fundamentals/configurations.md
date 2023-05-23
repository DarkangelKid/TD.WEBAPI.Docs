---
title: "Configurations"
description: "Configurations trong TD Web API."
lead: "Configurations trong TD Web API."
date: 2021-08-24T11:40:05+05:30
lastmod: 2021-10-28T10:07:45+05:30
draft: false
images: []
menu:
  dotnet-webapi-boilerplate:
    identifier: "configurations"
    name: "Configurations"
    parent: "fundamentals"
weight: 8
toc: true
---

Trong `Host` project có thư mục `Configurations` chứa toàn bộ config của dự án

## Cấu trúc

```bash
├── Host.csproj
│   ├── Configurations
│   |   ├── cache.json
│   |   ├── cors.json
│   |   ├── database.json
│   |   ├── firebase_admin_sdk.json
│   |   ├── hangfire.json
│   |   ├── ldap.json
│   |   ├── localization.json
│   |   ├── logger.json
│   |   ├── mail.json
│   |   ├── middleware.json
│   |   ├── minio.json
│   |   ├── openapi.json
│   |   ├── security.json
│   |   ├── securityheaders.json
│   |   └── signalr.json
|   ├── appsettings.json
|
```

> appsettings.json ở thư mục gốc vẫn có tác dụng nếu như bạn không muốn tạo cấu hình trong file json riêng

 **`Startup` class** bên trong thư mục có nhiệm vụ load toàn bộ cấu hình bên trong. Nếu có thêm cấu hình khác, bạn nên tạo thêm .json trong thư mục này (Ví dụ cấu hình MQTT server,...)

## Cache

Mặc định, ứng dụng sử dụng bộ nhớ `in-memory cache`, để sử dụng `Redis`, set `UseDistributedCache` và `PreferRedis` thành `true` và cấu hình URL hợp lệ

```json
{
  "CacheSettings": {
    "UseDistributedCache": false,
    "PreferRedis": false,
    "RedisURL": "localhost:6379"
  }
}
```

## CORS
Cấu hình CORS cho ứng dụng

```json
{
  "CorsSettings": {
    "Angular": "http://localhost:4200",
    "Blazor": "https://localhost:5002;https://www.mydomain.my",
    "React": "http://localhost:3000"
  }
}
```

## Database


```json
{
  "DatabaseSettings": {
    "DBProvider": "postgresql",
    "ConnectionString": "Host=localhost;Port=5432;Database=fshDb;Username=postgres;Password=admin;Include Error Detail=true"
  }
}
```

## Logger

Hệ thống sử dụng `Serilog`, cấu hình có thể nâng cao hơn, vui lòng tìm hiểm thêm `Serilog`
```json
{
  "LoggerSettings": {
    "AppName": "FSH.WebApi",
    "ElasticSearchUrl": "http://localhost:9200",
    "WriteToFile": true,
    "StructuredConsoleLogging": false
  }
}
```

## Mail

Cấu hình tài khoản mail gửi qua SMTP Service, thay đổi lại cho phù hợp

```json
{
  "MailSettings": {
    "DisplayName": "Tan Dan demo",
    "From": "tandandemo@gmail.com",
    "Host": "smtp.gmail.com",
    "Password": "ruiocarhtleehhtx",
    "Port": 587,
    "UserName": "tandandemo@gmail.com"
  }
}
```

### Security
- `JwtSettings`: Cấu hình JWT token private key, thời gian hết hạn, refresh của token. Khi tạo solution mới, nhớ thay lại `key`
- `RequireConfirmedAccount` true : Yêu cầu tài khoản đã được xác nhận thì mới truy cập được hệ thống. Đọc thêm phần này trong code
```json
{
  "SecuritySettings": {
    "Provider": "Jwt",
    "RequireConfirmedAccount": true,
    "JwtSettings": {
      "key": "PRIVATEKEY_JWT",
      "tokenExpirationInMinutes": 60,
      "refreshTokenExpirationInDays": 7
    },
    "Swagger": {
      "AuthorizationUrl": "https://login.microsoftonline.com/organizations/oauth2/v2.0/authorize",
      "TokenUrl": "https://login.microsoftonline.com/organizations/oauth2/v2.0/token",
      "ApiScope": "api://<Your ClientId of the AzureAd Server App Registration>/access_as_user",
      "OpenIdClientId": "<Your ClientId of the AzureAd Client App Registration>"
    }
  }
}
```
