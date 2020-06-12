# /api/store/depot

* Tính năng này dùng để lấy danh sách kho của doanh nghiệp. Hỗ trợ tìm kiếm thông qua ID kho.

## Request

* See [common request params](../getting-started/api.md#request)
* The search param - \(Data array\)

| Param |  | Mandatory | Description |
| :--- | :--- | :--- | :--- |
| depotId | Int | No | Tìm kiếm theo ID kho |

## Response

JSON decode the response to get the structure:

| Key | Data Type\(Max-length\) | Description |
| :--- | :--- | :--- |
| code | int | 1 = success or 0 = failed |
| messages | \[ \] | is an array of error messages if code = 0 |
| data | \[ \] | Mảng danh sách kho của doanh nghiệp |

```javascript
data = [
   depotId1: [
        'name' => string,
        'city' => string,
        'district' => string,
        'ward' => string,
        'address' => string
   ],
   depotId2: [
        'name' => string,
        'city' => string,
        'district' => string,
        'ward' => string,
        'address' => string
   ]
]
```

