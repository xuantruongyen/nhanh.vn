# /api/order/update
Tính năng này dùng để lấy khiếu lại đơn hàng từ website của bạn và trả lời khiếu lại khi đơn hàng có khiếu lại(Khi website của bạn nhận khiếu nại đơn hàng, website của bạn sẽ gửi thông tin này sang Nhanh.vn.Đội chăm sóc đơn hàng của Nhanh.vn sẽ trả lời khiếu lại và phản hồi lại website của bạn).

## Request

- See [common request params](/api.md#request)

- The data structure of an order complain: 

Key | Data type | Mandatory | Description
---- | ------|------|-----
id | int | Yes | ID đơn hàng bên web đồng bộ
reason | string | No | Lý do
complain | string | Yes | Nội dung khiếu nại

# Response
```js
"code": 1, // 1 is success, 0 is error
	"messages": [ ], // error messages if code is 0
	"data": [
		"3256" => 5174985, // id đơn hàng trên website của bạn => bigint: order id of Nhanh.vn
		"status": "Shipping", // trạng thái hiện tại của đơn hàng
		"shipFee" => 30000, // int: Phí vận chuyển
		"codFee" => 13000, // int: Phí thu tiền hộ
		"shipFeeDiscount" => 0, // int: Phí vận chuyển được giảm giá
		"codFeeDiscount" => 0 // int: Phí thu tiền hộ được giảm giá
	]
}

```

