  # /api/shipping/location

- Lấy danh sách thành phố, quận huyện từ Nhanh.vn.
Các API [đồng bộ đơn hàng](/order/add.md), [tính phí vận chuyển](/shipping/fee.md) sẽ cần sử dụng đến các dữ liệu này.

## Request
- See [common request params](/api.md#request)

- The search param - (Data array)

Param | | Mandatory | Description
----| ----------- | ----------- | -------
type | string | No | CITY/DISTRICT (mặc định là CITY)
parentId | int | No | Nếu type = DISTRICT thì parentId = id của thành phố cần lấy ra danh sách quận huyện.

## Response 
- JSON decode the response to get the structure:

Key | Data Type(Max-length) | Description
------| ------- | ---------
code | int | 1 = success or 0 = failed
messages | [ ] |is an array of error messages if code = 0
data | [ ] | Mảng danh sách thành phố hoặc quận huyện

- Nếu **type = CITY**

```js
[
    [
      "id": 2,
      "name":  "Hà Nội"
    ],
    [
      "id": 3,
      "name":  "Hồ Chí Minh"
    ]
    // ...
]
```

- Nếu **type = DISTRICT**

```js
[
    [
      "id": 2,
      "cityId": 2,
      "name": "Quận Hoàn Kiếm"
    ],	
    [
      "id": 6,
      "cityId": 2,
      "name": "Quận Hai Bà Trưng"
    ]
    // ...
]
```
 
