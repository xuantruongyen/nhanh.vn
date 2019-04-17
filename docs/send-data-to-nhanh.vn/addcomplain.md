# api/order/addcomplain

Tính năng này dùng để đồng bộ khiếu nại giữa đơn hàng của bạn và đơn hàng trên Nhanh.vn.

## Request

* See [common request params](../getting-started/api.md#request)
* The data structure of an add complain:

| Key | Data type | Mandatory | Description |
| :--- | :--- | :--- | :--- |
| id | int | Yes | ID đơn hàng bên website của bạn |
| reason | int | No | Lý do khiếu nại :  6 - Lý do khác   7 - Chậm chuyển tiền   8 - Báo hàng hoàn   9 - Báo phát lại   10 - Yêu cầu miễn giảm cước vận chuyển, bồi thường   33 - Báo lưu kho tại bưu cục   34- Yêu cầu cập nhật lại trạng thái   35 - Báo hủy đơn   36- Thay đổi thông tin đơn hàng, đổi tiền thu hộ COD   37- Báo gom đơn |
| description | string | Yes | Nội dung khiếu nại |

## Response:

```javascript
{
    "code": 1, // 1 is success, 0 is error
    "messages": [ ], // error messages if code is 0
    "data": [
        "complainId" => 5174985, 
        // complainId: ID khiếu nại trả về. Khi Nhanh.vn trả kết quả phản hồi khiếu nại sẽ kèm thêm complainId này.
    ]
}
```

Xem thêm kết quả phản hồi khiếu nại [tại đây](../listen-webhooks-from-nhanh.vn/listen-complain.md)

