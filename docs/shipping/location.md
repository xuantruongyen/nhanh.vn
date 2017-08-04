  # /api/shipping/location

- Lấy danh sách thành phố, quận huyện từ Nhanh.vn.
Các API [đồng bộ đơn hàng](/order/add.md), [tính phí vận chuyển](/shipping/fee.md) sẽ cần sử dụng đến các dữ liệu này.

- The POST params:

| Key | Data type  | Mandatory| Description|
|---------| ---------- | ---------- |------|
|version | string | Yes | 1.0|
|apiUsername | string | Yes| _YOUR_API_USERNAME_
|data| string | Yes| The json encoded string of search params array (see the table structure below), nếu data để trống mặc định sẽ lấy ra danh sách thành phố hỗ trợ vận chuyển.|
|checksum | string | Yes |<p></p> |

- The search param - (Data array)

Param | | Mandatory | Description
----| ----------- | ----------- | -------
type | string | No | CITY/DISTRICT (mặc định là CITY)
parentId | int | No | Nếu type = DISTRICT thì parentId = id của thành phố cần lấy ra danh sách quận huyện.

- The response: JSON decode the response to get the structure:

Key | Data Type(Max-length) | Description
------| ------- | ---------
code | int | 1 = success or 0 = failed
messages | [ ] |is an array of error messages if code = 0
data | [ ] | Mảng danh sách thành phố hoặc quận huyện

- Nếu **type = CITY**
```js
  data = [
            [
     	       id: id của thành phố,
                name:  Tên thành phố
            ],
            [...]
        ]
```
- Nếu **type = DISTRICT**
```js
 data = [
		    [
				id: id của quận huyện,
				cityId: id của thành phố
				name: Tên quận huyện
		    ],
		    [...]
         ]
```
 
