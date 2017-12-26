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
| carrierCode | string(36) | No | Mã vận đơn hãng vận chuyển |
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
data = 
[
    "totalPages": int, // Tổng số trang
    "page": int, // Trang hiện tại
    "orders": [
        [
            // Đơn hàng 1
            "id": int, // ID đơn hàng
            "depotName": string, // Tên Cửa hàng
            "type": string, // Loại đơn hàng (Shipping | Shopping)
            "shippingType": string, // Loại chuyển hàng
            "carrierName": string, // Tên hãng vận chuyển
            "carrierServiceName": string, // Dịch vụ vân chuyển
            "moneyDiscount": double, // Tiền chiết khấu           
            "moneyDeposit": double, // Tiền đặt cọc
            "moneyTransfer": double, // Tiền chuyển khoản
            "description": string, // ghi chú của khách hàng
            "privateDescription" string, // ghi chú của CSKH
            "customerName": string, // Tên khách hàng
            "customerMobile": string, // Họ tên khách hàng
            "customerEmail": string, // Email khách hàng
            "customerAddress": string, // Địa chỉ khách hàng
            "customerCity": string, // Thành phố
            "customerDistrict": string, // Quận huyện
            "createdDateTime": string, // Thời gian tạo đơn hàng
            "deliveryDate": string, // Thời gian giao đơn hàng
            "statusName": string, // trạng thái đơn hàng
            "products": array, // Xem bảng Order Product bên dưới
        ],
        [
            // Đơn hàng 2
        ],
        // ...
    ]
]
```

### Order Product
```js
[
    [
        "productName" : string, // Tên sản phẩm
        "productCode" : int, // Mã sản phẩm
        "productBarCode" : int, // Mã vạch sản phẩm
        "price" : double, // Giá sản phẩm
        "quantity" : double, // Số lượng sản phẩm
        "weight" : int , // Trọng lượng sản phẩm
        "discount" : double, // Chiết khấu
        "description" : string, // Mô tả sản phẩm
    ],
    [
        // Sản phẩm 2
    ],
    ...
[
```





