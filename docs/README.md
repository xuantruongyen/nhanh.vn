# Introduction

[Nhanh.vn](https://nhanh.vn) là giải pháp quản lý bán hàng trên nền tảng điện toán đám mây, đồng bộ dữ liệu với website, dịch vụ vận chuyển, giúp doanh nghiệp quản lý toàn bộ quy trình bán hàng, chăm sóc khách hàng, tăng doanh thu, giảm chi phí, phát triển kinh doanh hiệu quả hơn.

* [Phần mềm quản lý bán hàng](https://nhanh.vn)
* [Dịch vụ vận chuyển](https://nhanh.vn/dich-vu-van-chuyen)
* [Thiết kế website bán hàng](https://nhanh.vn/gioi-thieu-tinh-nang-website)
* [Phần mềm quản lý Facebook Fanpage](https://vpage.nhanh.vn)

### Nhanh API là gì?

* API cung cấp các giải pháp để đồng bộ dữ liệu sản phẩm, đơn hàng, khách hàng, tồn kho giữa Nhanh.vn và các hệ thống website khác. Các giải pháp này phù hợp cho cả các website bình thường \(website của 1 cá nhân, công ty\) và cả các sàn thương mại điện tử có nhiều gian hàng.
* Nhanh API sử dụng RESTful và JSON format.
* PHP SDK: [https://github.com/nhanhapi/nhanh.vn](https://github.com/nhanhapi/nhanh.vn)
* [Khởi tạo API Account](getting-started/api.md#get-api-account), [Environment](getting-started/api.md#environment), [Request](getting-started/api.md#request), [Response](getting-started/api.md#response), [Checksum](getting-started/api.md#create-checksum), [Code Sample](getting-started/api.md#code-sample)

### Các tình huống phổ biến

#### Đồng bộ sản phẩm

Nhanh.vn hỗ trợ đồng bộ sản phẩm 2 chiều:

1. Bạn dùng Nhanh.vn trước, sau đó muốn lấy dữ liệu sản phẩm sang các hệ thống khác: Đồng bộ sản phẩm từ Nhanh.vn về hệ thống của bạn =&gt; nên dùng id sản phẩm bên Nhanh.vn làm key đồng bộ.
2. Bạn có website từ trước, sau đó mới dùng Nhanh.vn: Bạn có thể đồng bộ sản phẩm từ website về Nhanh =&gt; nên dùng id sản phẩm bên website làm key đồng bộ.

   khi đồng bộ sản phẩm từ website cũ về Nhanh, Nhanh sẽ trả về id sản phẩm trên Nhanh, bên web sau đó có thể lưu lại idNhanh này và tất cả các API khác sau đó dùng idNhanh làm key đồng bộ

#### Đồng bộ tồn kho

* Tồn kho chỉ được đồng bộ từ Nhanh.vn sang các hệ thống khác, Nhanh.vn không nhận cập nhật tồn kho từ bên ngoài. 
* Khi tồn kho trên Nhanh.vn có thay đổi, hệ thống của bạn sẽ nhận được 1 webhooks \(xem thêm mục [Listen Inventory](listen-webhooks-from-nhanh.vn/listen-2).

#### Đồng bộ đơn hàng

* Nhanh.vn hỗ trợ đồng bộ đơn hàng từ các hệ thống khác về, thường dùng khi bạn có website từ trước:
  * Khi khách đặt hàng: Đồng bộ thông tin đơn hàng về Nhanh.vn.
  * Khi khách hủy đơn hoặc thanh toán online cho đơn hàng: Cập nhật thông tin đơn hàng
  * Khi nhân viên xử lý các đơn hàng ở Nhanh.vn, Nhanh.vn sẽ gửi webhooks về hệ thống của bạn để cập nhật trạng thái đơn hàng, lịch trình vận đơn.
* Nhanh.vn hỗ trợ các API về [tính phí vận chuyển](get-data-from-nhanh.vn/fee.md), và các cài đặt [gửi Email](https://nhanh.vn/manual/item/view?id=449), [gửi SMS](https://nhanh.vn/manual/item/view?id=450) để thông báo cho khách hàng về thông tin đơn hàng.

### Get data from Nhanh.vn

Dữ liệu về vận chuyển:

* [/api/shipping/carrier](get-data-from-nhanh.vn/carrier.md): Lấy danh sách các hãng vận chuyển đang tích hợp trên Nhanh.vn 
* [/api/shipping/location](get-data-from-nhanh.vn/location.md): Lấy danh sách thành phố, quận huyện ở Nhanh.vn
* [/api/shipping/multifee](get-data-from-nhanh.vn/multifee.md): Tính phí vận chuyển cho nhiều đơn hàng cùng lúc.
* [/api/shipping/fee](get-data-from-nhanh.vn/fee.md): Tính phí vận chuyển cho một đơn hàng.
* [/api/shipping/trackingframe](get-data-from-nhanh.vn/trackingframe.md): Tạo link url hiển thị lịch trình của đơn hàng

Dữ liệu về đơn hàng

* [/api/order/index](get-data-from-nhanh.vn/list.md): Lấy danh sách đơn hàng
* [/api/order/history](get-data-from-nhanh.vn/history.md): Lấy lịch sử thao tác đơn hàng

Dữ liệu về sản phẩm:

* [/api/product/category](get-data-from-nhanh.vn/category.md): Lấy danh mục sản phẩm
* [/api/product/search](get-data-from-nhanh.vn/search.md): Lấy danh sách sản phẩm
* [/api/product/detail](get-data-from-nhanh.vn/detail.md): Lấy thông tin chi tiết sản phẩm 
* [/api/product/gift](get-data-from-nhanh.vn/gift.md): Lấy danh sách quà tặng theo sản phẩm
* [/api/product/imei](get-data-from-nhanh.vn/imei.md): Lấy danh sách imei sản phẩm
* [/api/product/imeisold](get-data-from-nhanh.vn/imeisold.md): Tra cứu imei sản phẩm theo ngày

Dữ liệu về khách hàng

* [/api/customer/search](get-data-from-nhanh.vn/search-1.md): Lấy danh sách khách hàng
* [/api/integrated-elastix](get-data-from-nhanh.vn/integrated-elastix.md): Lấy tên khách hàng để hiển thị ở phần mềm Call Center \(Tổng đài\) khi có khách gọi đến.

Dữ liệu về tin tức

* [/api/article/categories](get-data-from-nhanh.vn/categories.md): Lấy danh mục tin tức
* [/api/article/search](get-data-from-nhanh.vn/search-2.md): Lấy danh sách tin tức

Dữ liệu về hoá đơn:

* [/api/bill/search](get-data-from-nhanh.vn/search-3.md): Lấy danh sách hóa đơn bán hàng
* [/api/bill/imexs](get-data-from-nhanh.vn/imexs.md): Lấy danh sách sản phẩm xuất nhập kho
* [/api/bill/imexrequirements](get-data-from-nhanh.vn/imexrequirements.md): Lấy danh sách sản phẩm yêu cầu xuất nhập kho

### Send data to Nhanh.vn

* [/api/store/add](send-data-to-nhanh.vn/add.md): Gửi thông tin doanh nghiệp
* [/api/product/add](send-data-to-nhanh.vn/add-1.md): Đồng bộ sản phẩm từ các website khác về Nhanh.vn
* [/api/order/add](send-data-to-nhanh.vn/add-2.md): Đồng bộ đơn hàng từ các website khác về Nhanh.vn
* [/api/order/update](send-data-to-nhanh.vn/update.md): Gửi cập nhật thông tin đơn hàng    
* [/api/order/addcomplain](send-data-to-nhanh.vn/addcomplain.md): Gửi khiếu nại từ website về Nhanh.vn
* [/api/customer/add](send-data-to-nhanh.vn/add-3.md): Gửi thông tin khách hàng
* [/api/store/configwebhooks](send-data-to-nhanh.vn/link.md): Link webhooks config cho shop

### Listen webhooks from Nhanh.vn

* [Listen order status](listen-webhooks-from-nhanh.vn/listen.md): Nhận cập nhật trạng thái đơn hàng từ Nhanh.vn
* [Listen product data](listen-webhooks-from-nhanh.vn/listen-1.md): Nhận thông tin sản phẩm cập nhật từ Nhanh.vn
* [Listen inventory](https://github.com/nhanhapi/nhanh.vn/tree/61337548cfd92eb09522219d6702a6b66b4edb9f/docs/product/inventory.md): Nhận cập nhật thay đổi tồn kho từ Nhanh.vn
* [Listen change level, add point, subtract](https://github.com/nhanhapi/nhanh.vn/tree/61337548cfd92eb09522219d6702a6b66b4edb9f/docs/bill/listenchange/README.md): Nhận thông tin thay đổi cấp độ, tặng điểm, trừ điểm khách hàng cập nhật từ Nhanh.vn 
* [Listen info when customer add order from](listen-webhooks-from-nhanh.vn/listen-info.md): Nhận thông tin khi khách hàng thêm hóa đơn mới từ Nhanh.vn hoặc từ website.    
* [Listen complain](listen-webhooks-from-nhanh.vn/listen-complain.md): Nhận thông tin về khiếu nại đơn hàng từ Nhanh.vn

