# /api/article/search 

- Tính năng này được sử dụng để lấy danh sach bài viết trên Nhanh, phân trang tối đa 50 tin tức/page, hỗ trợ lấy theo id bài viết > id bài viết truyền lên, hỗ trợ lọc bài viết theo danh mục.

- The POST params:

Key | Data type | Mandatory | Description
------ | --------- | -------- | -------
version | string | Yes | 1.0
apiUsername | string | Yes | _YOUR_API_USERNAME_
storeId | string(20) | No | required for e-commerce platforms
data | string | Yes | The json encoded string of search params array (see the table structure below), data không thể để null; nếu không tìm kiếm theo một tiêu chí nào data sẽ là một mảng rỗng.
checksum | string | Yes | <p></p>

- Cấu trúc data đẩy lên
```js
data = [
	page: int, //page load
	icpp: int, //số records / page
	lastId: int // lọc bài viết lấy từ bài viết có id >  lastId
	categoryId: int // lọc theo category id
]
```
- Response:

Key | Data Type(Max-length) | Description
------- | ------ | -----------
code | int | 1 = success or 0 = failed
messages | [ ] | is an array of error messages if code = 0
data | [ ] | is an array of product category (multi-level)

```json
data = [
	{
		totalPages: int //tổng số page
		pages: int // page hiện tại
		result: [ // Kết quả trả về
			{
				id: int //id bài viết
				[
					id: int //id bài viết
					categoryId: int // cateogry id
					status: int // Trạng thái
					title: string // tiêu đề bài viêt
					intro: string // giới thiệu ngắn gọn bài viết
					content: string // Nội dung bài viết
				]
			},
			...
		]
},
…
```

