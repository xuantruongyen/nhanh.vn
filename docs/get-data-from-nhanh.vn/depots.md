# /api/store/depots

* Tính năng này dùng để lấy danh sách kho của doanh nghiệp. Hỗ trợ tìm kiếm thông qua ID kho.
* Deprecated feature: please use [/api/store/depot](depot.md)

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
   depotId1: Tên kho 1,
   depotId2: Tên kho 2,
   [...]
]
```

