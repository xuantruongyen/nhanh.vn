# <a href='https://nhanh.vn' target='_blank'><img src='https://nhanh.vn/images/v4/nhanh.png'></a>

[Nhanh.vn](https://nhanh.vn) là giải pháp quản lý bán hàng trên nền tảng điện toán đám mây, đồng bộ dữ liệu với website, dịch vụ vận chuyển, giúp doanh nghiệp quản lý toàn bộ quy trình bán hàng, chăm sóc khách hàng, tăng doanh thu, giảm chi phí, phát triển kinh doanh hiệu quả hơn.

* [Phần mềm quản lý bán hàng](https://nhanh.vn)
* [Dịch vụ vận chuyển](https://nhanh.vn/dich-vu-van-chuyen)
* [Thiết kế website bán hàng](https://nhanh.vn/gioi-thieu-tinh-nang-website)
* [Phần mềm quản lý Facebook Fanpage, Zalo Page](https://crm.nhanh.vn)

<img src="https://nhanh.vn/images/v4/banner/banner22Right.png">

## Nhanh API là gì?

* API cung cấp các giải pháp để đồng bộ dữ liệu sản phẩm, đơn hàng, khách hàng, tồn kho giữa Nhanh.vn và các hệ thống website khác. Các giải pháp này phù hợp cho cả các website bình thường \(website của 1 cá nhân, công ty\) và cả các sàn thương mại điện tử có nhiều gian hàng.

* Nhanh API sử dụng RESTful và JSON format.
* PHP SDK: [https://github.com/nhanhapi/nhanh.vn](https://github.com/nhanhapi/nhanh.vn) 

* [Khởi tạo tài khoản API](api.md#get-api-account)
* [Environment](api.md#environment),  [Request](api.md#request),  [Response](api.md#response),  [Checksum](api.md#create-checksum),  [Code Sample](api.md#code-sample)

## Get data from Nhanh.vn

Dữ liệu về vận chuyển:

* [/api/shipping/carrier](shipping/carrier.md): Lấy danh sách các hãng vận chuyển đang tích hợp trên Nhanh.vn 
* [/api/shipping/location](shipping/location.md): Lấy danh sách thành phố, quận huyện ở Nhanh.vn
* [/api/shipping/multifee](shipping/multifee.md): Lấy thông tin phí vận chuyển (multi)
* [/api/shipping/fee](shipping/fee.md): Tính phí vận chuyển
* [/api/shipping/trackingframe](shipping/trackingframe.md): Tạo link url hiển thị lịch trình của đơn hàng

Dữ liệu về đơn hàng
* [/api/order/history](order/history.md): Lấy lịch sử thao tác đơn hàng

Dữ liệu về sản phẩm:

* [/api/product/category](product/category.md): Lấy danh mục sản phẩm
* [/api/product/search](product/search.md): Lấy danh sách sản phẩm
* [/api/product/detail](product/detail.md): Lấy thông tin chi tiết sản phẩm 
* [/api/product/gift](product/gift.md): Lấy danh sách quà tặng theo sản phẩm
* [/api/product/imei](product/imei.md): Lấy danh sách imei sản phẩm

Dữ liệu về khách hàng
* [/api/customer/search](customer/search.md): Lấy thông tin khách hàng

Dữ liệu về tin tức
* [api/article/categories](article/categories.md): Lấy thông tin danh mục tin tức
* [/api/article/search](article/search.md): Lấy thông tin tin tức

Dữ liệu về hoá đơn:
* [/api/bill/search](bill/search.md): Lấy danh sách hóa đơn bán hàng
* [/api/bill/imexrequirements](/bill/imexrequirements.md): Lấy danh sách sản phẩm yêu cầu xuất nhập kho
* [/api/bill/imexs](bill/imexs.md): Lấy danh sách sản phẩm xuất nhập kho

## Send data to Nhanh.vn
* [/api/store/add](store/add.md): Gửi thông tin doanh nghiệp
* [/api/product/add](product/add.md): Đồng bộ sản phẩm từ các website khác về Nhanh.vn
* [/api/order/add](order/add.md): Đồng bộ đơn hàng từ các website khác về Nhanh.vn
* [/api/order/update](order/update.md): Gửi cập nhật thông tin đơn hàng    
* [/api/customer/add](customer/add.md): Gửi thông tin khách hàng

## Listen webhooks from Nhanh.vn

* [Listen order status](order/listen.md): Nhận cập nhật trạng thái đơn hàng từ Nhanh.vn
* [Listen product data](product/listen.md): Nhận thông tin sản phẩm cập nhật từ Nhanh.vn
* [Listen inventory](product/inventory.md): Nhận cập nhật thay đổi tồn kho từ Nhanh.vn
* [Listen change level, add point, subtract](bill/listenchange): Nhận thông tin thay đổi cấp độ, tặng điểm, trừ điểm khách hàng cập nhật từ Nhanh.vn 
* [Listen info when customer add order from ](order/listen-info.md): Nhận thông tin khi khách hàng thêm hóa đơn mới từ Nhanh.vn hoặc từ website.    











