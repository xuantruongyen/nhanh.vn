# Listen order status

- Website của bạn cần đăng kí một URL để nhận trạng thái đơn hàng cập nhật từ Nhanh.vn (cập nhật realtime khi trạng thái đơn hàng thay đổi bên trong Nhanh.vn)
 
## Request

- Nhanh.vn send a POST request to your listen URL. See [common request params](/api.md#request).
- Decode data string (JSON) to get the data object: The properties of each order if **updateType** is **Status** or **CheckPayment**:
  
Param | Data type (Max-length) | Description
----------- | ---------------- | --------
id | string(20) | id của đơn hàng được đồng bộ từ website của bạn sang Nhanh.vn
status | string | Trạng thái đơn hàng xem [tại đây](https://developers.nhanh.vn/glossary.html#order-status)
reason | string | Lí do theo trạng thái:<br>WrongProduct => Đặt nhầm sản phẩm<br>HighShipFee => Phí vận chuyển cao<br>NotTransfer => Không muốn chuyển khoản<br>Duplicated => Đơn trùng<br>CannotCall => Không gọi được khách<br>SoldOut => Hết hàng<br>WaitingTransfer => Chờ chuyển khoản<br>NotLikeProduct => Khách không thích sản phẩm<br>NotPleasureDeliverer => Khách không hài lòng về nhân viên vận chuyển<br>SlowShipping => Giao hàng chậm<br>Bought => Đã mua sản phẩm tại cửa hàng<br>CustomerNotAtHome => Khách đi vắng (sẽ giao hàng vào hôm khác)<br>WrongAddress => Sai địa chỉ người nhận<br>NotBuy => Khách không muốn mua nữa<br>CannotCallSender => Không liên hệ được với người gửi<br>SellerNotSellOnline => Người gửi không bán hàng Online / Ngoại tỉnh<br>SellerNotHandoverCarrier => Người gửi không bàn giao hàng cho hãng vận chuyển<br>SellerNotProcessOrder => Người gửi không xử lý đơn hàng<br>WrongPickupAddress => Sai địa chỉ kho lấy hàng<br>WrongPrice => Sai giá sản phẩm<br>SelfShipping => Người gửi tự vận chuyển<br>CarrierPickupLate => Hãng vận chuyển lấy hàng muộn<br>CarrierLostProduct => Hãng vận chuyển làm mất hàng<br>Other => Lý do khác
carrierId | int / null | id của hãng vận chuyển 
carrierServiceId | int / null | id của dịch vụ vận chuyển
sendCarrierDateTime | string / null | Thời gian gửi đơn hàng sang hãng vận chuyển. Định dạng: yyyy-mm-dd hh-mm-ss (nếu đơn chưa gửi sang hãng vận chuyển thì giá trị sẽ là null)
weight | int | trọng lượng của đơn hàng (tính bằng gram) do doanh nghiệp khai báo.
carrierWeight | int | trọng lượng của đơn hàng (tính bằng gram) do hãng vận chuyển trả kết quả.
customerShipFee | double | Phí thu của khách
shipFee | double | Phí vận chuyển
overWeightShipFee | double | Phí vượt cân
returnFee | double | Phí chuyển hoàn (các đơn hàng không phát được, chuyển trả lại người gửi)
codFee | double | Phí thu tiền hộ (nếu đơn hàng cần thu tiền, các đơn chỉ giao hàng mà không cần thu tiền sẽ không có khoản phí này).
totalProductMoney | double | Tổng giá trị các sản phẩm trong đơn: (Số lượng * Giá) + VAT
discount | double | Chiết khấu
moneyTransfer | double | Tiền đã chuyển khoản
moneyDeposit  | double | Tiền đặt cọc
paymentForSender | double | Số tiền thanh toán cho người gửi hàng (đã trừ đi các loại phí phải trả cho hãng vận chuyển)
deliveryDate | date | Ngày giao hàng (yyyy-mm-dd)

 Sau khi nhận được kết quả từ Nhanh gửi sang, bạn cần trả lại response cho Nhanh đánh dấu trạng thái của lần đồng bộ này: 
 ```js
{
  "code": 1,
  // Nếu tình huống updateType = CheckPayment, trả thêm kết quả cho từng đơn
  "data": [
      "id": 1 // id là id đơn hàng từ website của bạn gửi sang Nhanh, 1 là check thanh toán thành công, 0 là check thanh toán không thành công
  ]
}
 ```
  - The properties if **updateType** is **Payment**:
  
Param | Data type(Max-length) | Description
----------- | ---------------- | --------
updateType | string | fixed value: Payment
paymentCode | string | Mã giao dịch chuyển tiền (Nhanh.vn thanh toán tiền trả doanh nghiệp khi đã giao hàng thành công)
paymentMoney | double | Số tiền đã chuyển
totalOrders | int | Tổng số đơn trong lần thanh toán này

  Sau khi bạn nhận được kết quả và xử lý thành công cần trả response dạng json: **{code: 1}** để Nhanh.vn đánh dấu trạng thái thanh toán đã được gửi thành công.
  
  