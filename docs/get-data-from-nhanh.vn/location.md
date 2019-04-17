# /api/shipping/location

* Lấy danh sách thành phố, quận huyện từ Nhanh.vn.

  Các API [đồng bộ đơn hàng](../send-data-to-nhanh.vn/add-2.md), [tính phí vận chuyển](fee.md) sẽ cần sử dụng đến các dữ liệu này.

## Request

* See [common request params](../getting-started/api.md#request)
* The search param - \(Data array\)

| Param |  | Mandatory | Description |
| :--- | :--- | :--- | :--- |
| type | string | No | CITY/DISTRICT \(mặc định là CITY\) |
| parentId | int | No | Nếu type = DISTRICT thì parentId = id của thành phố cần lấy ra danh sách quận huyện. |

## Response

* JSON decode the response to get the structure:

| Key | Data Type\(Max-length\) | Description |
| :--- | :--- | :--- |
| code | int | 1 = success or 0 = failed |
| messages | \[ \] | is an array of error messages if code = 0 |
| data | \[ \] | Mảng danh sách thành phố hoặc quận huyện |

* Nếu **type = CITY**

```javascript
[
    [
      "id": 2, // int
      "name":  "Hà Nội" // string
    ],
    [
      "id": 3,
      "name":  "Hồ Chí Minh"
    ]
    // ...
]
```

* Nếu **type = DISTRICT**

```javascript
[
    [
      "id": 2, // int
      "cityId": 2, // int
      "name": "Quận Hoàn Kiếm" // string
    ],    
    [
      "id": 6,
      "cityId": 2,
      "name": "Quận Hai Bà Trưng"
    ]
    // ...
]
```

