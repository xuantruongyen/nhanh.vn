# /api/store/depots

- Tính năng này dùng để lấy danh sách kho của doanh nghiệp. Hỗ trợ tìm kiếm thông qua ID kho.

- The POST params:

Key | Data type | Mandatory | Description
-------- | -------- | ---------- |--------
version | string | Yes | 1.0
apiUsername | string | Yes | _YOUR_API_USERNAME_
data | string | No | The json encoded string of search params array (see the table structure below); nếu không tìm kiếm theo một tiêu chí nào data sẽ là một mảng rỗng.
checksum | string | Yes | <p></p>
 
- The search param - (Data array)

Param | | Mandatory | Description
---- | ----- | ------ | ---------
id | Int | No | Tìm kiếm theo ID kho

- The response: JSON decode the response to get the structure:

Key |Data Type(Max-length) | Description 
-------- | ------- | --------
code | int | 1 = success or 0 = failed
messages | [ ] | is an array of error messages if code = 0
data | [ ] | Mảng danh sách kho của doanh nghiệp

```js
data = [
   id1: Tên kho 1,
   id2: Tên kho 2,
   [...]
]
```