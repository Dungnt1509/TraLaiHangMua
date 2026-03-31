# Màn hình: Popup chọn mặt hàng từ chứng từ mua hàng/dịch vụ

Popup cho phép người dùng tìm kiếm và chọn mặt hàng từ chứng từ mua hàng/dịch vụ để tạo chứng từ điều chỉnh giá hàng mua.

## Điều kiện tiên quyết

- Người dùng đã đăng nhập và có quyền tạo chứng từ điều chỉnh giá hàng mua
- Popup được gọi từ màn hình Thêm mới/ Sửa chứng từ điều chỉnh giá hàng mua khi bấm nút "Chọn chứng từ"

## Nguyên mẫu

[Đang bổ sung]

## Thành phần

### Điều kiện tìm kiếm

<div style="overflow-x:auto">

| Trường thông tin   | Control          | Field           | Max length | Bắt buộc (Y/N) | Giá trị mặc định         | Cho phép sửa (Y/N) | Mô tả                                                                      |
|:-------------------|:-----------------|:----------------|:-----------|---------------:|:-------------------------|:------------------:|:---------------------------------------------------------------------------|
| Loại nghiệp vụ     | Select           | LoaiNghiepVu    | -          |              Y | Mua hàng nhập kho        |         Y          | Mua hàng nhập kho / Mua hàng không qua kho / Mua dịch vụ                   |
| Hình thức mua hàng | Select           | HinhThucMuaHang | -          |              N | Trong nước               |         Y          | Trong nước / Nhập khẩu. Chỉ hiển thị khi Loại nghiệp vụ khác "Mua dịch vụ" |
| Nhà cung cấp       | Combogrid search | NhaCungCapId    | -          |              Y |                          |         Y          | Chọn từ danh mục nhà cung cấp **ENT_NhaCungCap**                           |
| Loại tiền          | Select           | LoaiTienId      | -          |              N | Theo đồng tiền hạch toán |         Y          | Chọn từ danh mục loại tiền tệ **ENT_LoaiTien**                             |
| Nút Tìm kiếm       | Button           | -               | -          |              - |                          |         -          | Bấm vào để tìm kiếm theo điều kiện đã chọn                                 |

</div>

### Danh sách kết quả

- Danh sách kết quả hiển thị chi tiết theo hàng hóa/dịch vụ của chứng từ mua hàng/mua dịch vụ (ENT_ChiTietChungTuMuaHang, ENT_ChiTietChungTuMuaDichVu)
- Danh sách kết quả chỉ hiển thị các hàng hóa/dịch vụ chưa được điều chỉnh toàn bộ
- Cho phép tìm kiếm chung theo số chứng từ, số hóa đơn, tên hàng hóa/dịch vụ, mã hàng hóa
- Chỉ hiển thị theo kết quả đáp ứng mọi điều kiện tìm kiếm bên trên

<div style="overflow-x:auto">

| Cột           | Control  | Field       | Max length | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Tìm kiếm nâng cao | Mô tả                                             |
|:--------------|:---------|:------------|:-----------|---------------:|:-----------------|:------------------:|:-----------------:|:--------------------------------------------------|
| Checkbox      | checkbox | -           | -          |              - |                  |         -          |         -         | Chọn để thêm vào chứng từ điều chỉnh giá hàng mua |
| Ngày chứng từ | date     | NgayChungTu | -          |              - |                  |         N          |         Y         | Ngày chứng từ mua hàng                            |
| Số chứng từ   | text     | SoChungTu   | -          |              - |                  |         N          |         Y         | Số chứng từ mua hàng/dịch vụ                      |
| Số hóa đơn    | text     | SoHoaDon    | -          |              - |                  |         N          |         Y         | Số hóa đơn, nếu không có thì bỏ trống             |
| Mã hàng       | text     | MaHang      | -          |              - |                  |         N          |         Y         | Mã hàng hóa/dịch vụ                               |
| Tên hàng      | text     | TenHang     | -          |              - |                  |         N          |         Y         | Tên hàng hóa/dịch vụ                              |
| ĐVT           | text     | DonViTinh   | -          |              - |                  |         N          |         N         | Đơn vị tính                                       |
| Số lượng      | number   | SoLuong     | -          |              - |                  |         N          |         N         | Số lượng hàng hóa/dịch vụ                         |
| Đơn giá       | number   | DonGia      | -          |              - |                  |         N          |         N         | Đơn giá hàng hóa/dịch vụ                          |
| Thành tiền    | number   | ThanhTien   | -          |              - |                  |         N          |         N         | Thành tiền = Số lượng × Đơn giá                   |

</div>

### Chức năng

<div style="overflow-x:auto">

| Tên               | Loại        | Mô tả                                                                                                                             |
|:------------------|:------------|:----------------------------------------------------------------------------------------------------------------------------------|
| Nút Xác nhận      | button      | Bấm vào để thêm các dòng đã chọn (được tick checkbox) vào danh sách chi tiết điều chỉnh của chứng từ điều chỉnh giá hàng mua. BR1 |
| Nút Hủy           | button      | Bấm vào để đóng popup, không lưu lựa chọn                                                                                         |
| Tìm kiếm nâng cao | button/icon | Bấm vào hiển thị thêm các điều kiện tìm kiếm nâng cao                                                                             |
| Nút Làm mới       | button/icon | Bấm vào để làm mới danh sách, tải lại dữ liệu mới nhất                                                                            |

</div>

**BR1**

- Cần chọn ít nhất 1 hàng hóa/dịch vụ, nếu không nút xác nhận sẽ bị disable
- Sau khi bấm xác nhận, thông tin sẽ được auto-fill từ popup vào chứng từ điều chỉnh giá hàng mua:
    - Mã nhà cung cấp, Tên nhà cung cấp, Mã số thuế, Địa chỉ
    - Loại nghiệp vụ, Hình thức mua hàng
    - Thông tin hàng hóa/dịch vụ: Mã, Tên, ĐVT, Số lượng, Đơn giá, Thành tiền
    - Thuế suất, tiền thuế, tài khoản thuế, nhóm HHDV mua vào
    - Các thông tin khác: Số lô, hạn sử dụng, mã kho, đơn vị, vụ việc, nhóm CP, đối tượng THCP
    - Nếu chọn mua hàng không qua kho/dịch vụ thì điều chỉnh giá trị hàng nhập kho = false và = true với Mua hàng nhập kho

**BR2**

- Nếu người dùng mở lại popup này, hệ thống hiển thị lại các giá trị đã đưa vào phiếu
- Đồng bộ với những hàng hóa/dịch vụ đã chọn và thêm vào chứng từ điều chỉnh. Ví dụ nếu xóa trong chứng từ => Xóa trong popup