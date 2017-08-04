# /api/order/history 
- Tính năng này dùng để lấy lịch sử thao tác với đơn hàng.

## Request

- The POST params: [common request params](/api.md#request)

- The search param - (Data array)

Param | |  Mandatory | Description
------- | ---------- | ----------- | --------------
orderId | Int | Yes | Id đơn hàng trên Nhanh cần xem lịch sử thao tác đơn hàng.
 
 ## Response
 
-JSON decode the response to get the structure:
 
Key | Data Type(Max-length) | Description
----------- | -------------- | -----------
code | int | 1 = success or 0 = failed
messages | [ ] | is an array of error messages if code = 0
data | [ ] | Mảng danh sách sản phẩm yêu cầu xuất nhập kho
```js
data = [
		[
			step: Hành động,
			createdBy: Được thao tác bởi ai,
			createdDateTime: Thời gian thao tác,
			oldStatus: Trạng thái trước khi thao tác,
			newStatus: Trạng thái sau khi thao tác
	    ],
		….
	    [...]
]
```


