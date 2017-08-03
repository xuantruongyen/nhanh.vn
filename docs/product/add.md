# /api/product/add

- Tính năng này dùng để gửi thông tin sản phẩm từ website của bạn sang Nhanh.vn.

- The POST params:

Param | Data type(Max-length) | Description
---- | ------------ |---------
storeId | string(20) | id của gian hàng trên các sàn thương mại điện tử (các website bình thường không cần quan tâm đến tham số này)
data | string | JSON encoded string, see structure in the table below
checksum | string(32) | use **secretKey** and received **data** param to create the checksum and compare with **checksum** param.

- The **data array**:

```
// each request can send maximum 300 products
[
	[ // product 1 ], // see the structure in the table below
	[ // product 2 ],
	...
]
```

Key | Data type | Mandatory | Description
----------- | -------- | -------- | -----------
id| string(20) | Yes | id của sản phẩm
idNhanh | bigint | No | id sản phẩm trên Nhanh.vn ([idNhanh đồng bộ từ Listen product updated from Nhanh.vn](listen.html))
parentId | string(20) | No | id của sản phẩm cha
code | string(255) | No | Mã sản phẩm
barcode | string(20) | No | Mã vạch của sản phẩm
name | string(255) | Yes | Tên sản phẩm
image | string(255) | No | Ảnh đại diện của sản phẩm. Đường dẫn ảnh là đường dẫn tuyệt đối, VD: http://example.com/images/samsung-galaxy-s-2.jpg
images | array | No | Các ảnh khác của sản phẩm, đường dẫn ảnh là địa chỉ tuyệt đối.
shippingWeight | int| No |Cân nặng cả vỏ hộp tính bằng gram, được sử dụng để tính phí vận chuyển khi đặt hàng.
vat |int  | No | % thuế giá trị gia tăng (VD: 10)
price | int | Yes | Giá bán của sản phẩm
importPrice | int | No | Giá nhập của sản phẩm
wholesalePrice | int | No | Giá bán buôn của sản phẩm
status | string | No | Trạng thái của sản phẩm: Active or Inactive
