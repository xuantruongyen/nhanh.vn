# /api/order/update
- Tính năng này dùng để cập nhật thông tin đơn hàng khi khách hàng thực hiện việc chuyển khoản online (Khi website của bạn nhận được cập nhật từ cổng thanh toán, website của bạn sẽ gửi thông tin này sang Nhanh.vn) hoặc khi khách hàng hủy đơn hàng. Hoặc dùng trong tình huống website của bạn muốn gửi đơn hàng qua các hãng vận chuyển.

- The POST params:

Param | Data type(Max-length)|Description
---- | ------|------
version|string|“1.0”
apiUsername|string(32)|_YOUR_API_USERNAME_
storeId|string(20)|id của gian hàng trên các sàn thương mại điện tử (các website bình thường không cần quan tâm đến tham số này)
data|string|JSON encoded string, see structure in the table below
checksum|string(32)|use **secretKey** and received **data** param to create the checksum and compare with **checksum param**.

- The structure of an order:

Key | Data type | Mandatory | Description
---- | ------|------|-----
id | string(20) | Yes | the order’s id in merchant website
autoSend | int | No | Biến đánh dấu gửi luôn đơn hàng sang hãng vận chuyển (Dùng trong tình huống bạn có hệ thống xác nhận đơn hàng từ trước, chỉ dùng Nhanh để hỗ trợ vận chuyển).<br>Set value = 1 để gửi đơn hàng sang hãng vận chuyển.
moneyTransfer | int | No | Số tiền khách đã chuyển khoản
paymentCode | string(255) | No | Mã giao dịch thanh toán
paymentGateway | string(255) | No | Tên của cổng thanh toán
status | string | No | Trạng thái đơn hàng, có thể là:<br>Confirmed //Đã xác nhận<br>Canceled // Khách hủy<br>Aborted //Hệ thống hủy
reasonDescription | string | No | Mô tả lý do hủy đơn hàng

- Response from Nhanh.vn
```js
{
	"code": 1, // 1 is success, 0 is error
	"messages": [ ], // error messages if code is 0
	"data": [
		"3256" => 5174985, // id đơn hàng trên website của bạn => bigint: order id of Nhanh.vn
		"status": "Shipping", // trạng thái hiện tại của đơn hàng
		"shipFee" => 30000, // int: Phí vận chuyển
		"codFee" => 13000, // int: Phí thu tiền hộ
		"shipFeeDiscount" => 0, // int: Phí vận chuyển được giảm giá
		"codFeeDiscount" => 0, // int: Phí thu tiền hộ được giảm giá
	]
}
```
**Chú ý**: 
- **shipFee **và **codFee **dùng trong tình huống đơn hàng có sử dụng dịch vụ vận chuyển, thông tin đơn hàng gửi sang có kèm theo carrierId, carrierServiceId và weight.
- **shipFeeDiscount **là phí vận chuyển được chiết khấu, VD **shipFee **= 25.000, **shipFeeDiscount **= 7.000 thì **shipFee **thực tế của đơn hàng này sẽ chỉ = 18.000
- **codFeeDiscount **là phí thu tiền hộ được chiết khấu, VD **codFee **= 15.000, **codFeeDiscount **= 3.000 thì **codFee **thực tế của đơn hàng này sẽ chỉ = 12.000




