# /api/order/addcomplain
Tính năng này dùng để lấy khiếu lại đơn hàng từ website của bạn và trả lời khiếu nại khi đơn hàng có khiếu lại(Khi website của bạn nhận khiếu nại đơn hàng, website của bạn sẽ gửi thông tin này sang Nhanh.vn.Đội chăm sóc đơn hàng của Nhanh.vn sẽ trả lời khiếu nại và phản hồi lại website của bạn).

## Request

- See [common request params](/api.md#request)

- The data structure of an add complain: 

Key | Data type | Mandatory | Description
---- | ------|------|-----
id | int | Yes | ID đơn hàng bên website của bạn
reason | string | No | Lý do 
complain | string | Yes | Nội dung khiếu nại

## Response: 

- See: [Response](/api.md#response)




