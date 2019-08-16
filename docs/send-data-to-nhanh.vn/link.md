# /api/store/configwebhooks

Config webhooks listen data send from Nhanh.vn

## Request

* You can send a POST request to change your listen URL. See [common request params](../getting-started/api.md#request)
* The data structure of an config:

| Key | Data type | Mandatory | Description |
| :--- | :--- | :--- | :--- |
| uriListenProductAdd | string |  | Link nhận thông báo thêm sản phẩm |
| uriListenInventory | string |  | Link nhận cập nhật tồn kho |
| uriListenOrderStatus | string |  | Link nhận cập nhật trạng thái đơn hàng |
| uriListenNewOrder | string |  | Link nhận thông báo đơn hàng mới |

