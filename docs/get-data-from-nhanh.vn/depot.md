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
        'name' => Tên kho hàng,
        'cityId' => ID thành phố,
        'cityName' => Tên thành phố,
        'districtId' => ID quận huyện,
        'districtName' => Tên quận huyện,
        'wardId' => ID phường xã,
        'wardName' => Tên phường xã,
        'address' => Địa chỉ kho
   ],
   depotId2: [
        'name' => Tên kho hàng,
        'cityId' => ID thành phố,
        'cityName' => Tên thành phố,
        'districtId' => ID quận huyện,
        'districtName' => Tên quận huyện,
        'wardId' => ID phường xã,
        'wardName' => Tên phường xã,
        'address' => Địa chỉ kho
   ]
]
```

