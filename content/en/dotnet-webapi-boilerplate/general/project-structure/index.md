---
title: "Project Structure"
description: ".NET TDWebApi Structure"
lead: ".NET TDWebApi Structure"
date: 2021-08-24T11:40:05+05:30
lastmod: 2021-11-28T17:35:38+05:30
draft: false
images: []
menu:
  dotnet-webapi-boilerplate:
    identifier: "general-project-structure"
    name: "Project Structure"
    parent: "general"
weight: 6
toc: true
---

## General Structure

Solution gồm các project sau

```bash

├── src
│   ├── Host
|   |   └── Host.csproj
│   ├── Core
│   |   ├── Application.csproj
│   |   ├── Shared.csproj
│   |   └── Domain.csproj
|   ├── Infrastructure
|   |   └── Infrastructure.csproj
|   ├── Migrators
│   |   ├── Migrators.MSSQL.csproj
│   |   ├── Migrators.MySQL.csproj
│   |   ├── Migrators.PostgreSQL.csproj
│   |   └── Migrators.Oracle.csproj

```

### Host

Project chứa API Controllers, các tệp cấu hình, config email, logs...

Cấu trúc:

```bash
├── Host
|   ├── Configurations
|   ├── Controllers
|   ├── Email Templates
|   ├── Extensions
|   ├── Files
│   |   ├── Images
│   |   └── Documents
|   ├── Localization
|   ├── Logs
|   └── appsettings.json
```

 *Host* project depends on
- Application
- Infrastructure
- Migration Projects

### Application
Project chứa logic ứng dụng, chứa các Abstract Classes và Interfaces được triển khai trong Infrastructure

Cấu trúc:
``` bash
├── Core
|   ├── Application
|   |   ├── Auditing
|   |   ├── Catalog
|   |   ├── Common
|   |   ├── Dashboard
|   |   ├── Identity
|   |   └── Multitenancy

```

 *Application* project depends on
- Shared
- Domain

### Domain

 *Domain* project depends on
- Shared

