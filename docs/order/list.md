# /api/order/index

* Tính năng này dùng để lấy danh sách đơn hàng.

## Request

* See [common request params](/api.md#request)

* The search param - \(Data array\)

| Param |  | Mandatory | Description |
| --- | --- | --- | --- |
| page | int | No | Phân trang \(giá trị mặc định là 1\) |
| fromDate | string | No | Định dạng: yyyy-mm-dd. Ngày tạo đơn hàng. |
| toDate | string | No | Định dạng: yyyy-mm-dd. Ngày tạo đơn hàng. |
| id | int | No | ID đơn hàng |
| customerMobile |string |Yes	|Mobile của người nhận hàng|
|status	|string	| No | Trạng thái đơn hàng xem [tại đây](https://developers.nhanh.vn/glossary.html#order-status) |
| fromDeliveryDate | string | No | Định dạng: yyyy-mm-dd. Ngày giao hàng |
| toDeliveryDate | string | No | Định dạng: yyyy-mm-dd. Ngày giao hàng |
| carrierId |int |	No | id hãng vận chuyển (Lấy từ [/api/shipping/fee](https://developers.nhanh.vn/shipping/fee.html)) |
| carrierCode | string(36) | No | Mã vận đơn HVC |
| type	|string	 |No |Loại đơn hàng, giá trị có thể là: “Shipping” (Chuyển hàng) hoặc “Shopping” (Khách tới mua tại cửa hàng).“PreOrder”(Khách đặt hàng trước).Giá trị mặc định là Shipping.|
| shippingType | int | No | Loại chuyển hàng:<br>- [G] Chuyển hàng tận nhà <br> - [Đ] Đổi sản phẩm <br> - [T] Khách trả lại hàng |
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
        customerName : Tên khách hàng,
        customerMobile : Mobile người nhận hàng,
        customerCityId : Thành phố,
        customerDistrictId : Quận huyện,
        carrierId : Hãng vận chuyển,
        carrierServiceId : Dịch vụ vân chuyển
        moneyDepositAccountId : Tiền đặt cọc,
        moneyTransferAccountId : Tiền chuyển khoản,
        productName : Tên sản phẩm,
        productCode : Mã sản phẩm,
        productBarCode : Mã vạch sản phẩm,
        price : Giá,
        quantity : Số lượng,
        weight : Trọng lượng,
        discount : Chiết khấu,
        description : Mô tả
    ],
    ….
    [...]
]
```



