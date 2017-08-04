# /api/article/categories 

- Tính năng này được sử dụng để lấy toàn bộ danh mục tin tức của doanh nghiệp trên Nhanh.vn.

- The POST params:

Key | Data type | Mandatory | Description
------ | ----- | --------- | -------
version | string | Yes | 1.0
apiUsername | string | Yes | _YOUR_API_USERNAME_
storeId | string(20) | No | required for e-commerce platforms
data | string | No | <p></p>
checksum | string | Yes | <p></p>

- The response: JSON decode the response to get the structure:

Key | Data Type(Max-length) | Description
------------ | ---------- | ----------
code | int | 1 = success or 0 = failed
messages | [ ] | is an array of error messages if code = 0
data | [ ] | is an array of product category (multi-level)

```js
data = [
	{
		id: int
		name: string
		status: int
		parentId: int
		childs: [ // child categories
			{
				id: int
				name: string
				status: int
				parentId: int
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


