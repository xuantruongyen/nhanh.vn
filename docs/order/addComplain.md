# /api/order/addcomplain
Tính năng này dùng để đồng bộ khiếu nại giữa đơn hàng của bạn và đơn hàng trên Nhanh.vn.

## Request

- See [common request params](/api.md#request)

- The data structure of an add complain: 

Key | Data type | Mandatory | Description
---- | ------|------|-----
id | int | Yes | ID đơn hàng bên website của bạn
reason | int| No | Lý do đơn hàng xem [tại đây](https://developers.nhanh.vn/glossary.html#order-reason-complain)
description | string | Yes | Nội dung khiếu nại

## Response: 

- See: [Response](/api.md#response)




