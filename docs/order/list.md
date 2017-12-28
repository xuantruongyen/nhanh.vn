# /api/order/index

* Tính năng này dùng để lấy danh sách đơn hàng.

## Request

* See [common request params](/api.md#request)

* The search param - \(Data array\)

| Param | Data Type (Max-length) | Mandatory | Description |
| --- | --- | --- | --- |
| page | int | No | Phân trang \(giá trị mặc định là 1\) |
| fromDate | string | No | Ngày tạo đơn hàng: Định dạng yyyy-mm-dd. |
| toDate | string | No | Ngày tạo đơn hàng: Định dạng yyyy-mm-dd. |
| id | int | No | ID đơn hàng trên Nhanh.vn |
| customerMobile |string |Yes	| điện thoại của người nhận hàng |
|statuses |string | No | Trạng thái đơn hàng xem [tại đây](https://developers.nhanh.vn/glossary.html#order-status) |
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
    "totalRecords": int, // Tổng số bản ghi tất cả các trang
    "page": int, // Trang hiện tại
    "orders": [ // Danh sách đơn hàng trang hiện tại
        [
            // Đơn hàng 1
            "id": int, // ID đơn hàng
            "depotId" : int,// Mã kho
            "depotName": string, // Tên Cửa hàng
            "typeId" : int,//mã loại đơn hàng
            "type": string, // Loại đơn hàng (Shipping | Shopping)
            "shippingTypeId" : int,//Mã loại chuyển hàng
            "shippingType": string, // Loại chuyển hàng
            "serviceId": int,// Mã dịch vụ vận chuyển
            "carrierId": int,// Mã hãng vận chuyển
            "carrierCode": string,// Mã hãng vận chuyển
            "carrierName": string, // Tên hãng vận chuyển
            "carrierServiceName": string, // Dịch vụ vân chuyển
            "moneyDiscount": double, // Tiền chiết khấu           
            "moneyDeposit": double, // Tiền đặt cọc
            "moneyTransfer": double, // Tiền chuyển khoản
            "description": string, // ghi chú của khách hàng
            "privateDescription" string, // ghi chú của CSKH
            "customerId": int,// Mã khách hàng
            "customerName": string, // Tên khách hàng
            "customerMobile": string, // Họ tên khách hàng
            "customerEmail": string, // Email khách hàng
            "customerAddress": string, // Địa chỉ khách hàng
            "customerCityId": int,// Mã tỉnh
            "customerCity": string, // Thành phố
            "customerDistrictId": int,// Mã quận/huyện
            "customerDistrict": string, // Quận huyện
            "createdByUserName": string,//user name tạo đơn hàng
            "createdByName" : string,// Người tạo đơn
            "createdDateTime": string, // Thời gian tạo đơn hàng
            "deliveryDate": string, // Thời gian giao đơn hàng
            "statusCode": string,// Mã trạng thái
            "statusName": string, // Trạng thái đơn hàng
            "calcTotalMoney" : double,// Tổng thu của khách
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
        "productId": int,//Mã sản phẩm
        "productName" : string, // Tên sản phẩm
        "productCode" : int, // Mã sản phẩm
        "productBarcode" : string, // Mã vạch sản phẩm
        "price" : double, // Giá sản phẩm
        "quantity" : double, // Số lượng sản phẩm
        "weight" : int , // Trọng lượng sản phẩm
        "discount" : double, // Chiết khấu theo sản phẩm
        "description" : string, // Mô tả sản phẩm
    ],
    [
        // Sản phẩm 2
    ],
    // ...
[
```





