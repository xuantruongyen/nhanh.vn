# /api/shipping/trackingframe

* Tính năng này dùng để tạo link url hiển thị lịch trình của đơn hàng

  ```php
  <iframe src="https://graph.nhanh.vn/api/shipping/trackingframe?apiUsername=&orderId=&checksum=" width="800" height="600"></iframe>
  ```

  \[ Xem hình Demo bên dưới \]

![](../.gitbook/assets/pasted_image_0.png)  
Trong đó: 
```php
apiUsername: apiUsername 
orderId: id đơn hàng bên website tích hợp
checksum: md5(md5(SECRET_KEY . $data) . $data)
```

```php
$data = $apiUsername . $privateStoreId . $privateId;
checksum = md5(md5(SECRET_KEY . $data) . $data);
```

