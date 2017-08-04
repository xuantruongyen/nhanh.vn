# /api/shipping/carrier

- Tính năng này dùng để lấy danh sách các hãng vận chuyển đang được tích hợp với Nhanh.vn. Nhanh.vn đang kết nối với Viettel Post, Vietnam Post, Giaohangnhanh, Giaohangtietkiem... để hỗ trợ dịch vụ vận chuyển và giao hàng thu tiền tận nhà. Tình huống chủ doanh nghiệp chỉ muốn dùng một vài hãng vận chuyển nào đó, thì website của bạn có thể sử dụng tính năng này để lọc các **carrierId** (id của các hãng vận chuyển) được trả về từ API “Get shipping fee”.

- API này set data mặc định là “carriers”.
```json
[
  {
		id: int // 2
		name: string // “Viettel Post”,
		logo: string // absolute path of carrier’s logo
		businessName: string // “Tổng công ty cổ phần Bưu chính Viettel”,	
		services: [
			{
				id: int // 2
				name: string // Giao nhanh liên tỉnh
 			},
			...
		]
	},
	...
]
```




