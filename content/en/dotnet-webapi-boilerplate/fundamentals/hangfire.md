---
title: "Hangfire"
description: "Hangfire trong TD Web API."
lead: "Hangfire trong TD Web API."
date: 2021-08-24T11:40:05+05:30
lastmod: 2021-10-28T10:07:45+05:30
draft: false
images: []
menu:
  dotnet-webapi-boilerplate:
    identifier: "hangfire"
    name: "Hangfire"
    parent: "fundamentals"
weight: 11
toc: true
---

- Trong lập trình, bạn sẽ thường gặp 1 số vấn đề timeout như xử lý file lớn, import data, clean up database. Ngoài ra, bạn cần phải thiết lập thời gian để chạy schedule task như gởi report định kỳ theo tuần, theo ngày… Bạn nghĩ ngay đến Windows Service. Nhưng vấn đề là bạn cần phải host trên Windows Server. Nếu chỉ sử dụng IIS thôi thì HangFire có lẽ là sự lựa chọn tốt nhất.
- Bạn có thể xem thêm tài liệu về HangFire tại địa chỉ: `https://www.hangfire.io`
- Cấu hình trong `src/Host/Configurations/hangfire.json`.

```
{
  "HangfireSettings": {
    "Route": "/jobs",
    "Dashboard": {
      "AppPath": "/",
      "StatsPollingInterval": 2000,
      "DashboardTitle": "Jobs"
    },
    "Server": {
      "HeartbeatInterval": "00:00:30",
      "Queues": [
        "default",
        "notdefault"
      ],
      "SchedulePollingInterval": "00:00:15",
      "ServerCheckInterval": "00:05:00",
      "ServerName": null,
      "ServerTimeout": "00:05:00",
      "ShutdownTimeout": "00:00:15",
      "WorkerCount": 5
    },
    "Storage": {
      "StorageProvider": "mssql",
      "ConnectionString": "Server=10.10.10.50,1469; Database=DemoApp_Hangfire;User Id=tdcongdan; Password=Tandan@123; Trusted_Connection=False; MultipleActiveResultSets=true; TrustServerCertificate=true;",
      "Options": {
        "CommandBatchMaxTimeout": "00:05:00",
        "QueuePollInterval": "00:00:01",
        "UseRecommendedIsolationLevel": true,
        "SlidingInvisibilityTimeout": "00:05:00",
        "DisableGlobalLocks": true
      }
    },
    "Credentials": {
      "User": "Admin",
      "Password": "Tandan@123"
    }
  }
}
```
### Create a Background Job
- Code mẫu có trong `src/Application/Catalog/Brands/GenerateRandomBrandRequest.cs` 
