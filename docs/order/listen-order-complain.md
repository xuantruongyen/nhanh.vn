# Listen order complain

Website của bạn cần đăng kí một URL để nhận phản hồi khiếu nại đơn hàng cập nhật từ Nhanh.vn

## Request {#request}

* Nhanh.vn send a POST request to your listen URL. See
  [common request params](https://developers.nhanh.vn/api.html#request)
  .
* Decode data string \(JSON\) to get the data object:

Param	| Data type (Max-length)|Description
----|---- |----
id|string(20)|id của đơn hàng khiếu nại được đồng bộ từ website của bạn sang Nhanh.vn
complainId| int | ID khiếu nại trả về
answer | string | Nội dung trả lời khiếu nại







