# Listen info when customer add order from Nhanh.vn 
- Website của bạn cần đăng kí một URL để nhận thông tin khi khách hàng đặt đơn hàng từ Nhanh.vn hoặc từ website của bạn. (Cập nhật realtime ngay khi khách hàng đặt đơn hàng từ Nhanh.vn hoặc từ website của bạn)

# Request
- See [common request params](/api.md#request)

<table>
  <tr>
     <th>Param</th>
     <th>Data type (Max-length)</th>
     <th>Description</th>
  </tr>
  <tr>
     <td>storeId</td>
     <td>String (20)</td>
     <td>id của gian hàng trên các sàn thương mại điện tử (các website bình thường không cần quan tâm đến tham số này).</td>
  </tr>
   <tr>
     <td>data</td>
     <td>string</td>
     <td>
     Json encoded string: json_decode chuỗi này được một mảng:
        <pre lang="xml">
        [
         “orderId”: ID đơn hàng,
         “customerMobile”: Số điện thoại khách hàng,
         “type”: addOrder,
         “totalAmount”:  Giá trị đơn hàng,
         “discount”:  Tiền chiết khấu,
         “addPoint”: Số điểm được tặng,
         “subtractPoint”: Số điểm đã sử dụng cho đơn hàng,
         “depotName”: Tên cửa hàng khách hàng mua,
         “billType”: export (mua hàng) hoặc import (trả hàng)
        ]
        </pre>
     </td>
  </tr>
   <tr>
     <td>checksum</td>
     <td>String (32)</td>
     <td>Sử dụng secretKey và data nhận về để tạo checksum và so sánh với tham số checksum.</td>
  </tr>
</table>
