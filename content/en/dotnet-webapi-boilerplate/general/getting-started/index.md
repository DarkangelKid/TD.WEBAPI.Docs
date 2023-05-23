---
title: "Getting Started 🚀"
description: "Tài liệu này nhằm mục đích tạo và chạy một dự án dựa trên .NET TD WebAPI chỉ trong 5 phút."
lead: "Tài liệu này nhằm mục đích tạo và chạy một dự án dựa trên .NET TD WebAPI chỉ trong 5 phút."
date: 2021-08-30T00:59:34+05:30
lastmod: 2023-04-08T15:32:05+05:30
draft: false
images: []
menu:
  dotnet-webapi-boilerplate:
    identifier: "general-getting-started"
    name: "Getting Started 🚀"
    parent: "general"
weight: 3
toc: true
---

  <p>

Đảm bảo cài đặt môi trường phát triển đầy đủ. Tham khảo [Development Environment](/dotnet-webapi-boilerplate/general/development-environment/).


## Forking the Repository & Creating your New Solution!

- Fork hoặc Clone `TD.WebApi`.
- Thiết lập riêng Solution cho bạn

## Running the Application

Mở Solution thông qua VS Code hoặc Visual Studio
### Thiết lập Connection String

Để chạy được ứng dụng, đổi lại connection strings. Truy cập tới thư mục`src/Host/Configurations` và mở file `database.json`. Tại đây bạn sửa lại chuỗi kết nối tới Database `DatabaseSettings` (hỗ trợ MSSQL,  MySQL , PostgreSQL, SQLite, Oracle). Ví dụ

#### PostgreSQL

```powershell
"DatabaseSettings": {
    "ConnectionString": "Host=localhost;Database=rootTenantDb;Username=postgres;Password=root;Include Error Detail=true",
    "DBProvider": "postgresql"
  }
```

#### MySQL

```powershell
"DatabaseSettings": {
    "ConnectionString": "server=localhost;uid=root;pwd=root;database=defaultRootDb;Allow User Variables=True",
    "DBProvider": "mysql"
  }
```
#### MSSQL

```powershell
"DatabaseSettings": {
    "DBProvider": "mssql",
    "ConnectionString": "Data Source=(localdb)\\mssqllocaldb;Initial Catalog=rootTenantDb;Integrated Security=True;MultipleActiveResultSets=True"
  }
```
#### Oracle

```powershell
{
  "DatabaseSettings": {
    "DBProvider": "oracle",
    "ConnectionString": "Data Source=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=127.0.0.1)(PORT=49154))(CONNECT_DATA =(SERVER=DEDICATED)(SERVICE_NAME=ORCLPDB1.localdomain)));User Id=fullstack;Password=password123"
  }
}
```

Sau khi chỉnh sửa chuỗi kết nối database, đã có thể chạy ứng dụng. Chạy lệnh sau

```powershell
 cd src/Host
 dotnet build
 dotnet run
```


{{< img src="running-api-1.png" >}}

-  Lưu ý: Connection String khai báo trong appSettings là connection mặc định của tenant `root`. Tất cả thông tin tenant khác sẽ được lưu trong bảng Tenants.

