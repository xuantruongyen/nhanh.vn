# /api/product/category

- Tính năng này được sử dụng để lấy toàn bộ danh mục sản phẩm trên Nhanh.vn.

- The POST params:

Key | Data type | Mandatory | Description
---------- | ----------- | ---------- | -----------
version | string | Yes | 1.0
apiUsername | string | Yes | _YOUR_API_USERNAME_
storeId | string(20) | No | required for e-commerce platforms
data | string | Yes | Fixed string: productcategory
checksum |  string | Yes | <p></p>

- The response: JSON decode the response to get the structure:

Key | Data Type(Max-length) | Description
-------- | -------------- | -----------
code | int | 1 = success or 0 = failed
messages | [ ] | is an array of error messages if code = 0
data | [ ] | is an array of product category (multi-level)

Mảng đệ quy toàn bộ danh mục của doanh nghiệp
```js
data = [
	{
		id: int // id danh mục
		parentId: int // id danh mục cha
		code: string // Mã danh mục
		name: string // Tên danh mục
		childs: [ // array mảng các danh mục con
			{
				id: int
				parentId: int
				code: string
				name: string
				childs: [
					...
				]
			},
			... 
		]
	},
	...
     ]
```



