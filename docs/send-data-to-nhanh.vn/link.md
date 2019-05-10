# /api/store/configwebhooks

Config webhooks listen URL

## Request

* You can send a POST request to change your listen URL. See [common request params](../getting-started/api.md#request)
* The data structure of an config:

| Key | Data type | Mandatory | Description |
| :--- | :--- | :--- | :--- |
| uriListenProductAdd | string |  | Link thêm sản phẩm |
| uriListenInventory | string |  | Link tồn kho |
| uriListenOrderStatus | string |  | Link trạng thái đơn hàng |

