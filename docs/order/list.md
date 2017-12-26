# /api/order/index

* Tính năng này dùng để lấy danh sách đơn hàng của doanh nghiệp.

## Request

* See [common request params](/api.md#request)

* The search param - \(Data array\)

| Param |  | Mandatory | Description |
| --- | --- | --- | --- |
| page | Int | No | Phân trang \(giá trị mặc định là 1\) |
| icpp | Int | No | Số lượng sản phẩm trên 1 trang. Mặc định là 10. Tối đa không quá 20. |
| fromDate | string | No | Định dạng: Ngày/Tháng/Năm. Ngày tạo đơn hàng. |
| toDate | string | No | Định dạng: Ngày/Tháng/Năm. Ngày tạo đơn hàng. |
| id | Int | No | ID đơn hàng |
| customerMobile |string(255)	|Yes	|Mobile của người nhận hàng|
|status	|string	|No	|Trạng thái của đơn hàng, có thể là các giá trị:<br>New // đơn hàng mới<br>Confirmed // CSKH đã xác nhận<br>StoreConfirmed // chủ doanh nghiệp đã xác nhận<br>Canceled // Khách hủy<br>Aborted // Hệ thống hủy<br>Nếu không set giá trị gì thì Nhanh.vn sẽ lấy mặc định là New |
| fromDeliveryDate | string | No | Định dạng: Ngày/Tháng/Năm. Ngày giao hàng |
| toDeliveryDate | string | No | Định dạng: Ngày/Tháng/Năm. Ngày giao hàng |
| carrierId |int |	No | id hãng vận chuyển (Lấy từ [/api/shipping/fee](https://developers.nhanh.vn/shipping/fee.html)) |
| carrierCode | varchar(36) | No | Mã vận đơn HVC |
| type	|string	 |No |Loại đơn hàng, giá trị có thể là: “Shipping” (Chuyển hàng) hoặc “Shopping” (Khách tới mua tại cửa hàng).“PreOrder”(Khách đặt hàng trước).Giá trị mặc định là Shipping.|
| shippingType | tinyint(3) | No | Loại chuyển hàng:<br>- [G] Chuyển hàng tận nhà <br> -[Đ] Đổi sản phẩm <br> -[T] Khách trả lại hàng |
|customerCityName |string(255)	|Yes	|Tên thành phố của người nhận hàng (Lấy từ [/api/shipping/location](https://developers.nhanh.vn/shipping/location.html))|
|customerDistrictName	|string(255)	|Yes	|Tên quận huyện của người nhận hàng (Lấy từ [/api/shipping/location](https://developers.nhanh.vn/shipping/location.html))|


## Response

JSON decode the response to get the structure:

| Key | Data Type\(Max-length\) | Description |
| --- | --- | --- |
| code | int | 1 = success or 0 = failed |
| messages | \[ \] | is an array of error messages if code = 0 |
| data | \[ \] | Mảng danh sách đơn hàng |

```js
data = [
    totalPage: Tổng số trang,
    page: Trang hiện tại,
    Orders: [
        id: ID đơn hàng,
        depotId : Cửa hàng,
        customerMobile : Mobile người nhận hàng,
        customerCityId : Thành phố,
        customerDistrictId : Quận huyện,
        carrierId : Hãng vận chuyển,
        carrierServiceId : Dịch vụ vân chuyển
        moneyDepositAccountId : Tiền gửi,
        moneyTransferAccountId : Tiền chuyển khoản
        
    ],
    ….
    [...]
]
```



