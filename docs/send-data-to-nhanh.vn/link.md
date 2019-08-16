# /api/store/configwebhooks

Config webhooks listen data send from Nhanh.vn

## Request

* You can send a POST request to change your listen URL. See [common request params](../getting-started/api.md#request)
* The data structure of an config:

| Key | Data type | Mandatory | Description |
| :--- | :--- | :--- | :--- |
| uriListenProductAdd | string | No | Link nhận thông báo thêm sản phẩm |
| uriListenInventory | string | No | Link nhận cập nhật tồn kho |
| uriListenNewNotification | string | No | Link nhận thông báo đơn hàng mới, tặng điểm, trừ điểm hoặc thay đổi cấp độ khách hàng |
| uriListenOrderStatus | string | No | Link nhận cập nhật trạng thái đơn hàng |


  ```javascript
  {
    uriListenProductAdd: "https://example.com/api/listen-product",
    uriListenInventory: "https://example.com/api/listen-inventory",
    uriListenNewNotification: "", // Để trống nếu bạn không cần Nhanh.vn gửi dữ liệu này
    uriListenOrderStatus: "https://example.com/api/listen-order-status"
  }
  ```
  
