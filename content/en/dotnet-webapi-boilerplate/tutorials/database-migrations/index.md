---
title: "Adding Database Migrations for Entity Framework Core"
description: "Adding Database Migrations for Entity Framework Core with TD Web API"
lead: "Adding Database Migrations for Entity Framework Core with TD Web API"
date: 2022-01-15T21:31:40+05:30
lastmod: 2022-01-15T21:31:44+05:30
draft: false
images: []
menu:
  dotnet-webapi-boilerplate:
    identifier: "database-migrations"
    name: "Database Migrations"
    parent: "tutorials"
weight: 12
toc: true
---
Hỗ trợ các DB Providers sau:
1. MSSQL
2. MySQL
3. PostgreSQL
4. Oracle

Cấu hình trong `src/Host/Configurations/database.json`.

Các loại database được hỗ trợ
- MSSQL - **mssql**
- MySQL - **mysql**
- PostgreSQL - **postgresql**
- Oracle - **oracle**

TD Web API gồm các EF Core DB Context sau:
1. ApplicationDbContext - Entities của ứng dụng được tham chiếu ở đây
2. TenantDbContext - Liên quan tới Finbuckle's Multitenancy.

Sau khi đã thêm các `entities` vào `Domain project` và thêm cấu hình phù hợp trong `TD.WebApi.Infrastructure.Persistence.Configuration` và `TD.WebApi.Infrastructure.Persistence.Context`, cách để tạo migrations:

- Mở command terminal trên thư mục của `Host Project` và dùng lệnh:

```
dotnet ef migrations add <CommitMessage> --project .././Migrators/Migrators.<DBProvider>/ --context ApplicationDbContext -o Migrations/Application
```
Trong đó
- `<CommitMessage>` mô tả Migration
- `<DBProvider>`  Database Provider (`MSSQL`, `MySQL`, `Oracle` hoặc `PostgreSQL`)

Ví dụ Tạo migrations cho ApplicationDbContext,

```dotnet ef migrations add AddedMenuEntity --project .././Migrators/Migrators.MSSQL/ --context ApplicationDbContext -o Migrations/Application```

Tạo migrations cho  TenantDbContext,

```dotnet ef migrations add ModifiedTenantTable --project .././Migrators/Migrators.MSSQL/ --context TenantDbContext -o Migrations/Tenant```

