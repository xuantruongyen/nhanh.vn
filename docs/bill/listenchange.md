# Listen change level, add point, subtract point updated from Nhanh.vn
- Website của bạn cần đăng kí một URL để nhận thông tin thay đổi cấp độ, tặng điểm, trừ điểm cập nhật từ Nhanh.vn (Cập nhật realtime ngay khi cấp độ, tặng điểm, trừ điểm thay đổi bên trong Nhanh.vn).

## Request

- Nhanh.vn send a POST request to your listen URL. See [common request params](/api.md#request).
- Decode data string (JSON) to get the data object:


<table>
  <tr>
     <th>Param</th>
     <th>Data type (Max-length)</th>
     <th>Description</th>
  </tr>
  <tr>
     <td>storeId</td>
     <td>String (20)</td>
     <td>id của gian hàng trên các sàn thương mại điện tử (các website bình thường không cần quan tâm đến tham số này)</td>
  </tr>
  <tr>
     <td>data</td>
     <td>string</td>
     <td>
     Json encoded string: json_decode chuỗi này được một mảng:
        <pre lang="xml">
[
       “billId”: ID hóa đơn mua (trả) hàng,
       “customerMobile”: Số điện thoại khách hàng,
       “type”: changeLevel | addBill
       “level”:  Cấp độ trước khi thay đổi,
       “addPoint”: Số điểm được tặng,
       “subtractPoint”: Số điểm bị trừ,
       “currentPoint”: Số điểm hiện tại của khách hàng,
       “currentLevel”: Cấp độ hiện tại của khách hàng,
       “depotName”: Tên cửa hàng khách hàng mua (trả) hàng
       “reason”: Lý do tặng (trừ) điểm,
       “totalAmount”: Tổng tiền hóa đơn mua,
       “billType”: export (mua hàng)  hoặc import (trả hàng)
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