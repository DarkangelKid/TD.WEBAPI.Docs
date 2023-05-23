---
title: "API Testing"
description: "Testing Web API"
lead: "Testing Web API"
date: 2021-08-30T00:59:34+05:30
lastmod: 2023-04-08T15:31:51+05:30
draft: false
images: []
menu:
  dotnet-webapi-boilerplate:
    identifier: "api-testing"
    name: "API Testing"
    parent: "general"
weight: 4
toc: true
---

Có thể test qua Postman hoặc Swagger. (Cổng mặc định https://[::]:5001 hoặc http://[::]:5000)


## Swagger

Địa chỉ https://localhost:5001/swagger/index.html

{{< img src="swagger.png" >}}

1 vài API sẽ được bảo mật bằng JWT token, sử dụng API /api/tokens để lấy token (lưu ý tenant)

{{< img src="swagger-request.png" >}}

Thông tin người dùng mặc định:

```
{
  "userName": "root.admin",
  "password": "Tandan@123"
}
```

Thông tin tenant mặc định `root`. Sau khi gửi request POST tới /api/tokens, hệ thống sẽ trả về mã JWT hợp lệ, dùng để xác thực cho các API khác.


{{< img src="swagger-response.png" >}}

Sau khi có mã token, copy paste token vào Authorize để sử dụng

{{< img src="swagger-header.png" >}}

## Postman

Tương tự. Khuyến khích sử dụng POSTMAN thay cho Swagger để Test API

