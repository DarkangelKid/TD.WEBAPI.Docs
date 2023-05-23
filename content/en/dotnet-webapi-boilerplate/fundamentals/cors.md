---
title: "CORS"
description: "CORS trong TD Web API."
lead: "CORS trong TD Web API."
date: 2021-08-24T11:40:05+05:30
lastmod: 2021-10-28T10:07:45+05:30
draft: false
images: []
menu:
  dotnet-webapi-boilerplate:
    identifier: "cors"
    name: "CORS"
    parent: "fundamentals"
weight: 11
toc: true
---

`CORS` là một cơ chế cho phép nhiều tài nguyên khác nhau (fonts, Javascript, v.v…) của một trang web có thể được truy vấn từ domain khác với domain của trang đó. CORS là viết tắt của từ Cross-origin resource sharing.

Cấu hình trong `src/Host/Configurations/cors.json`.

```
{
  "CorsSettings": {
    "Angular": "http://localhost:4200",
    "Blazor": "https://localhost:5002;https://www.mydomain.my"
  }
}
```


