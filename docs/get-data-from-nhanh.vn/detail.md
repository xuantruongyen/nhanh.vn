# /api/product/detail

* Tính năng này dùng để lấy thông tin chi tiết của sản phẩm. Nếu sản phẩm được đồng bộ từ Nhanh.vn sang website của bạn, đôi khi bạn sẽ muốn lấy thêm thông tin chi tiết của sản phẩm đó.

## Request

* See [common request params](../getting-started/api.md#request)
* The search param: data = array \( [NhanhProductId](https://github.com/nhanhapi/nhanh.vn/blob/master/src/get/product.php) \)

## Response

JSON decode the response to get the structure:

| Key | Data Type\(Max-length\) | Description |
| :--- | :--- | :--- |
| code | int | 1 = success or 0 = failed |
| messages | \[ \] | is an array of error messages if code = 0 |
| data | \[ \] | is an array of the parent and all child products \(if the requested has child products\) |

```javascript
data = [
    {
        // all properties are listed in the table below
    },
    ... 
]
```

| Key | Data Type\(Max-length\) | Description |
| :--- | :--- | :--- |
| idNhanh | bigint\(20\) | ID sản phẩm trên Nhanh.vn |
| merchantCategoryId | int | ID danh mục sản phẩm trên các site tích hợp  \(tính năng này hiện chỉ phục vụ cho các sàn TMĐT\) |
| merchantProductId | int | ID sản phẩm phi độc quyền \(tính năng này chỉ phục vụ cho các sàn TMĐT\) |
| categoryId | int | ID danh mục sản phẩm trên Nhanh.vn |
| parentId | bigint\(20\) | ID sản phẩm cha trên Nhanh.vn |
| code | string\(255\) | Mã sản phẩm |
| barcode | string\(255\) | Mã vạch sản phẩm |
| name | string\(255\) | Tên sản phẩm |
| otherName | string\(255\) | Tên khác của sản phẩm |
| importPrice | double | Giá nhập |
| oldPrice | double | Giá cũ |
| price | double | Giá bán lẻ |
| wholesalePrice | double | Giá bán buôn |
| vat | int | % thuế giá trị gia tăng \(VD: 10\) |
| image | string\(255\) | Đường dẫn tuyệt đối của ảnh đại diện |
| images | array | Đường dẫn tuyệt đối của các ảnh khách của sản phẩm |
| status | string | Trạng thái của sản phẩm: Active \| Inactive \| OutOfStock |
| previewLink | string | Link chi tiết của sản phẩm trên website \(if status is Active\) |
| description | string | Mô tả ngắn của sản phẩm |
| highlight | array | Đặc điểm nội bật của sản phẩm |
| content | string | Bài viết chi tiết của sản phẩm |
| showHot | int | \(Giá trị 0 \| 1\) Sản phẩm được đánh dấu là sản phẩm hot |
| showNew | int | \(Giá trị 0 \| 1\) Sản phẩm được đánh dấu là sản phẩm mới |
| showHome | int | \(Giá trị 0 \| 1\) Sản phẩm được đánh dấu hiển thị ở trang chủ |
| width | int | in cm |
| height | int | in cm |
| warrantyAddress | string | Địa chỉ bảo hành |
| warrantyPhone | string | Số điện thoại bảo hành |
| warranty | int | Số tháng bảo hành |
| warrantyContent | string | Nội dung bảo hành |
| length | int | in cm |
| shippingWeight | int | in gram |
| createdDateTime | datetime | Định dạng: yyyy-mm-dd hh:mm:ss |
| inventory | array | Thông tin tồn kho: xem ở bảng Inventory bên dưới |
| attributes | array |  |

### Inventory

```javascript
[
    // Tổng tồn trong tất cả các kho
    "remain": int // số lượng tồn kho
    "shipping": int // số lượng đang giao hàng
    "holding": int // số lượng đang tạm giữ
    "damage": int // số lượng lỗi
    "available": int // số lượng có thể bán (sử dụng để hiển  thị trên website,chặn đặt hàng khi hết số tồn hoặc vượt quá số tồn).
    // Tồn tại từng kho
    "depots": [
        "depotId" => [
        "remain": int // số lượng tồn kho
        "shipping": int //  số lượng đang giao hàng
        "holding": int // số lượng đang tạm giữ
        "damage": int //  số lượng lỗi
        "available": int // số lượng có thể bán (sử dụng để hiển thị trên website, chặn đặt hàng khi hết số tồn hoặc vượt quá số tồn).
        ],
        "depotId" => [
        ...
        ],
    ...
    ]
]
```

