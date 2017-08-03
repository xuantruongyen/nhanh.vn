# /api/bill/search 
- Tính năng này dùng lấy danh sách hóa đơn bán buôn và bán lẻ của doanh nghiệp. Hỗ trợ tìm kiếm thống qua: ID đơn hàng, thời gian tạo đơn hàng, số điện thoại khách hàng Tối đa ko quá 20 hóa đơn/ page
 
- The POST params:

Key | Data type | Mandatory | Description
-----|------------|-------------|--------
version | string | Yes | 1.0
apiUsername | string | Yes | _YOUR_API_USERNAME_
storeId | string(20) | No| Chỉ sử dụng cho các sàn thương mại điện tự với nhiều doanh nghiệp như lazada, vật giá
data |string | Yes| The json encoded string of search params array (see the table structure below), data không thể để null; nếu không tìm kiếm theo một tiêu chí nào data sẽ là một mảng rỗng.
checksum | string | Yes | <p></p>

- The search param - (Data content)

Param | | Mandatory | Description
----- | -------- | ------- |----------
page |int| No | Phân trang (giá trị mặc định là 1)
icpp | int | No | Số lượng đơn hàng trên 1 trang. Mặc định là 10. Tối đa không quá 20.
id | int | No| Tìm kiếm theo ID hóa đơn bán hàng
customerMobile | int | No|Tìm kiếm theo số điện thoại khách hàng
fromDate| date |No| Tìm kiếm ngày tạo hóa đơn >= fromeDate. Format yyyy-mm-dd (.e.g. 2015-07-16)
toDate | date | No | Tìm kiếm ngày tạo hóa đơn =< toDate Format yyyy-mm-dd (.e.g. 2015-08-16)
 
The response: JSON decode the response to get the structure:

Key |Data Type(Max-length) |Description
----- | --------- | --------
code | int |1 = success or 0 = failed
messages | [ ] |is an array of error messages if code = 0
data | [ ]| is an array of customer list

```json
data = [
        totalPages: int,
        bill: [
            {  }, // each bill item, all properties are listed in the table below
			{  }
            …
		]
]
```

Key | Data Type(Max-length) | Description
------- | ----------- | ----------
id | int | id của hóa đơn
createdDateTime | date | Ngày tạo hóa đơn
customerId |int | ID khách hàng mua hàng, có thể sử dụng để đồng bộ với ID khách hàng trong [/api/customer/search](search.html)
customerName | string | Tên khách hàng
customerMobile | int | Số điện thoại khách hàng
saleName | string | Nhân viên bán hàng
createdByName | string| Nhân viên thu ngân
discount | double | Chiết khấu hóa đơn
money | double | Tổng tiền hóa đơn
payment | double | Tổng tiền đã thanh toán
products | array | Danh sách sản phẩm theo hóa đơn [Xem bảng bên dưới]

- Products:

Key | Data Type(Max-length) | Description
---------- | ----------- | ----------
id | int | id của sản phẩm
code | string | Mã code của sản phẩm
name | string | Tên sản phẩm
quantity | int | Số lượng sản phẩm
price | int | Giá sản phẩm
discount | int | Chiết khấu của sản phẩm
imei | int | IMEI của sản phẩm. Nếu sản phẩm tồn tại IMEI sẽ hiện thêm trường này.