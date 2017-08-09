# Listen product data

- Mỗi website cần đăng kí 1 URL để nhận cập nhật thông tin sản phẩm từ Nhanh.vn (cập nhật realtime khi sản phẩm được thêm, sửa trong Nhanh.vn). Để sử dụng tính năng này, website của bạn phải thêm 1 trường để lưu **idNhanh** ứng với từng sản phẩm được đồng bộ từ Nhanh.vn sang, mỗi khi nhận được 1 request từ Nhanh, website sử dụng **idNhanh** để kiểm tra xem sản phẩm này đã tồn tại hay chưa để áp dụng việc thêm mới hoặc cập nhật thông tin sản phẩm tương ứng theo key **idNhanh**.

## Request

- See [common request params](/api.md#request)
- Product item’s properties:

 <table> 
    <tr>
        <th>Key</th>
        <th>Data Type(Max-length)</th>
        <th>Description</th>
    </tr>
     <tr>
        <td>idNhanh</td>
        <td>bigint(20)</td>
        <td>ID sản phẩm trên Nhanh.vn</td>
    </tr>
     <tr>
        <td>merchantCategoryId</td>
        <td>int</td>
        <td>ID danh mục sản phẩm trên các site tích hợp (tính năng này hiện chỉ phục vụ cho các sàn TMĐT)</td>
    </tr>
     <tr>
        <td>merchantProductId</td>
        <td>int</td>
        <td>ID sản phẩm phi độc quyền (tính năng này chỉ phục vụ cho các sàn TMĐT)</td>
    </tr>
     <tr>
        <td>categoryId</td>
        <td>int</td>
        <td>ID danh mục sản phẩm trên Nhanh.vn</td>
    </tr>
    <tr>
        <td>brandId</td>
        <td>int</td>
        <td>ID thương hiệu sản phẩm trên Nhanh.vn</td>
    </tr>
    <tr>
        <td>parentId</td>
        <td>bigint(20)</td>
        <td>ID sản phẩm cha trên Nhanh.vn</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>string(20)</td>
        <td>ID sản phẩm từ website của bạn gửi sang. (Nếu website của bạn có tích hợp Send product information: [/api/product/add](https://developers.nhanh.vn/product/add.html) Nhanh.vn sẽ lưu ID sản phẩm này được gửi từ website của bạn, khi thông tin sản phẩm được cập nhật trên Nhanh.vn, Nhanh API sẽ gửi dữ liệu tới website của bạn, và đây chính là id sản phẩm được gửi từ website của bạn).</td>
    </tr>
    <tr>
        <td>code</td>
        <td>string(255)</td>
        <td>Mã sản phẩm</td>
    </tr>
     <tr>
        <td>name</td>
        <td>string(255)</td>
        <td>Tên sản phẩm</td>
    </tr> 
    <tr>
        <td>price</td>
        <td>double</td>
        <td></td>
    </tr> 
    <tr>
        <td>vat</td>
        <td>int</td>
        <td>% thuế giá trị gia tăng (thường là 10)</td>
    </tr>
     <tr>
        <td>image</td>
        <td>string(255)</td>
        <td>Đường dẫn tuyệt đối của ảnh đại diện</td>
    </tr> 
    <tr>
        <td>images</td>
        <td>array</td>
        <td>Đường dẫn tuyệt đối của các ảnh khách của sản phẩm</td>
    </tr> <tr>
        <td>status</td>
        <td>string</td>
        <td>Trạng thái của sản phẩm: Active | Inactive</td>
    </tr>
    <tr>
        <td>commodityStatus</td>
        <td>string</td>
        <td>Tình trạng hàng hóa, các giá trị có thể là:<br>New: Hàng mới<br>Old: Hàng cũ</td>
    </tr>
    <tr>
        <td>commoditySource</td>
        <td>string </td>
        <td>Nguồn hàng, các giá trị có thể là:<br>Company: Hàng công ty<br>Genuine: Hàng chính hãng<br>PortableGoods: Hàng xách tay</td>
    </tr>
      <tr>
        <td>previewLink</td>
        <td>string  </td>
        <td>Link hiển thị trên website của sản phẩm này (if status is Active)</td>
    </tr>
     <tr>
        <td>description</td>
        <td>string  </td>
        <td>Mô tả ngắn của sản phẩm</td>
    </tr>
     <tr>
        <td>advantages</td>
        <td>string  </td>
        <td>Đặc điểm nổi bật của sản phẩm</td>
    </tr>
     <tr>
        <td>content</td>
        <td>string</td>
        <td>Bài viết chi tiết của sản phẩm</td>
        </tr>
     <tr>
        <td>width</td>
        <td>int</td>
        <td>in cm</td>
    </tr>
     <tr>
        <td>height</td>
        <td>int</td>
        <td>in cm</td>
    </tr>
     <tr>
        <td>height</td>
        <td>int</td>
        <td>in cm</td>
    </tr>
     <tr>
        <td>length</td>
        <td>int</td>
        <td>in cm</td>
    </tr> <tr>
        <td>shippingWeight</td>
        <td>int</td>
        <td>in gram</td>
    </tr> 
    <tr>
        <td>createdDateTime</td>
        <td>datetime</td>
        <td>Định dạng: yyyy-mm-dd hh:mm:ss</td>
    </tr>
    <tr>
        <td>inventory</td>
        <td>array</td>
        <td>        
             Xem bảng Inventory bên dưới  
        </td>
    </tr>
    <tr>
        <td>attributes</td>
        <td>array</td>
        <td>
 <pre lang="php">
[
    size => [
        id => int,
        name => string
    ],
    color => [
        id => int,
        name => string,
        parent => [ // parent color
        id => int,
        name => string
        ]
    ]
]
</pre>
</td>
</tr>
</table>

