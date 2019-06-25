# /api/product/imeisold

* Tính năng này dùng để tra cứu imei sản phẩm theo ngày ở trên Nhanh.vn. Dữ liệu sẽ được phân trang, mỗi trang tối đa không quá 100 sản phẩm.

  **Request**

* See [common request params](../getting-started/api.md#request)
* The search params:

| Param | Data Type | Mandatory | Description |
| :--- | :--- | :--- | :--- |
| page | int | No | Phân trang, giá trị mặc định sẽ là 1. |
| icpp | int | No | Số lượng sản phẩm trên 1 trang. Tối đa không quá 50. Mặc định nếu không set giá trị gì sẽ là 50. |
| fromDate | string | No | Ngày bán imei (từ ngày) định dạng yyyy-mm-dd|
| toDate | string | No |  Ngày bán imei (đến ngày) định dạng yyyy-mm-dd |
| ids | int | No | ID những sản phẩm /api/product/search |
| id | int | No | ID sản phẩm /api/product/search |
| brandId | int | No | Tìm theo thương hiệu |

## Response

JSON decode the response to get the structure:

| Key | Data Type\(Max-length\) | Description |
| :--- | :--- | :--- |
| code | int | 1 = success or 0 = failed |
| messages | \[ \] | is an array of error messages if code = 0 |
| data | \[ \] | is an array of product imei list |

```javascript
data = [
    [
      // imei 1 
      Imei // xem bảng imei bên dưới
    ],
    [
      // imei 2
      ... 
    ]
    
]
```

### Imei

| Key | Data Type\(Max-length\) | Description |
| :--- | :--- | :--- |
| imei | string | Imei sản phẩm trên Nhanh.vn |
| productName | string | Tên sản phẩm |
| productCode | string | Mã sản phẩm |
| productBarcode | string | Mã vạch sản phẩm |
| customer | array | Khách hàng(xem bên dưới) |

### customer
| Key | Data Type\(Max-length\) | Description |
| :--- | :--- | :--- |
| phone | string | Số điện thoại khách hàng |
| name | string | Tên khách hàng |
| email | string | Email khách hàng|
| address | string | Địa chỉ khách hàng |


