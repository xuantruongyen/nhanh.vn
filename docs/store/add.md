# /api/store/add

- Tính năng này được sử dụng cho các sàn thương mại điện tử có nhiều gian hàng, mỗi gian hàng sẽ tương ứng với 1 gian hàng ở trên Nhanh.vn. Các website bình thường không cần quan tâm tới chức năng này.

## Request
- See [common request params](/api.md#request)
- The data structure of the store: 

Key | Data type(Max-length) | Mandatory | Description
-------- | ---------- | ----------- | ---------
id | string(20) | Yes | the storeId in e-commerce platform
serviceType | string(30) | No | specify the service type of store (This feature is only available for merchant some specific merchants).The value can be:<br> fulfillment<br> gold <br>silver
name | string(255) | Yes | e.g. shopmp3 (can be the registered store name on e-commerce website: [http://vatgia.com/shopmp3](http://vatgia.com/shopmp3))
displayName | string(255) | Yes | e.g. MP3 Store (can be the business name of the store)
address | string(255) | Yes | <p></p>
email | string(255) | Yes | <p></p>
adminEmail | string(255) | No | the email address of store manager (used to check the privilege when user logins to the system)
mobile | string(12) | Yes | the mobile number
website | string(255) | No | <p></p>

## Response: 

- See: [Response](/api.md#response)


