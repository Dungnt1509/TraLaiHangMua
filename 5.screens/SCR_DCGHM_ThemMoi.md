# Màn hình: Thêm mới Chứng từ điều chỉnh giá hàng mua

## Điều kiện tiên quyết

- Người dùng đã đăng nhập hệ thống
- Người dùng có quyền thêm mới chứng từ điều chỉnh giá hàng mua

## Nguyên mẫu

[Đang bổ sung]

## Form thông tin chính

### Section 1 (ENT_ChungTuDieuChinhGiaHangMua) - Thông tin chung

| Trường thông tin                   | Control       | Field                                      | Max length | Bắt buộc (Y/N) | Giá trị mặc định   | Cho phép sửa (Y/N) | Mô tả                                                                                                                                                                       |
|:-----------------------------------|:--------------|:-------------------------------------------|:-----------|---------------:|:-------------------|-------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Chọn chứng từ                      | Button        | -                                          | -          |              - |                    |                  - | Mở popup chọn chứng từ mua hàng/dịch vụ (**SCR_DCGHM_PopupChonChungTu**)                                                                                                    |
| Lý do điều chỉnh                   | Select search | LyDoDieuChinh                              | -          |              Y | Giảm giá hàng mua  |                  Y | Giảm giá hàng mua/Tăng giá hàng mua/Điều chỉnh tăng & giảm giá hàng mua                                                                                                     |
| Điều chỉnh giá trị hàng nhập kho   | Checkbox      | DieuChinhGiaTriHangNhapKho                 | -          |              N | True               |                  Y | Điều chỉnh giá trị hàng nhập kho (true/false)                                                                                                                               |
| Trạng thái hóa đơn                 | Select        | ChungTuDieuChinhGiaHangMua.TrangThaiHoaDon | -          |              Y | Đã có hóa đơn      |                  Y | Đã có hóa đơn / Chưa có hóa đơn / Không có hóa đơn.                                                                                                                         |
| Điều chỉnh công nợ/Thanh toán ngay | Radio         | ThanhToanNgay                              | -          |              Y | Điều chỉnh công nợ |                  Y | Điều chỉnh công nợ/Thanh toán ngay                                                                                                                                          |
| Hình thức thanh toán               | Select search | HinhThucThanhToan                          | -          |              Y | Theo lựa chọn      |                  Y | Hiển thị nếu ThanhToanNgay = true. Theo LyDoDieuChinh: Tăng → Phiếu chi/Ủy nhiệm chi/Séc tiền mặt/Séc chuyển khoản; Giảm → Phiếu thu/Giấy báo có; Tăng & Giảm → Tất cả. BR9 |

### Section 2

#### Tab hóa đơn (ENT_HoaDonDieuChinh)

- Hiển thị nếu: TrangThaiHoaDon = "Đã có hóa đơn"

<div style="overflow-x:auto">

| Trường thông tin | Control          | Field         | Max length | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                               |
|:-----------------|:-----------------|:--------------|:-----------|---------------:|:-----------------|-------------------:|:----------------------------------------------------|
| Mẫu số hóa đơn   | Textbox          | MauSoHoaDonId | 50         |              N |                  |                  Y | Chọn từ danh mục mẫu số hóa đơn **ENT_MauSoHoaDon** |
| Ký hiệu hóa đơn  | Textbox          | KyHieuHoaDon  | 50         |              N |                  |                  Y |                                                     |
| Số hóa đơn       | Textbox          | SoHoaDon      | 50         |              N |                  |                  Y |                                                     |
| Ngày hóa đơn     | Date             | NgayHoaDon    | -          |              N | Ngày hiện tại    |                  Y |                                                     |
| Mã nhà cung cấp  | Combogrid search | NhaCungCapId  | -          |              Y |                  |                  Y | Chọn từ danh mục nhà cung cấp **ENT_NhaCungCap**    |
| Tên nhà cung cấp | Textbox          | TenNhaCungCap | 255        |              Y | Auto-fill        |                  N | Auto-fill từ Nhà cung cấp                           |
| Mã số thuế       | Textbox          | MaSoThue      | 50         |              N | Auto-fill        |                  Y | Auto-fill từ Nhà cung cấp, cho phép sửa             |
| Địa chỉ          | Textbox          | DiaChi        | 500        |              N | Auto-fill        |                  Y | Auto-fill từ Nhà cung cấp, cho phép sửa             |
| Diễn giải        | Textarea         | MoTa          | 500        |              N |                  |                  Y |                                                     |

</div>

#### Tab chứng từ điều chỉnh công nợ (ENT_ChungTuDieuChinhGiaHangMua)

- Hiển thị nếu: ThanhToanNgay = false (Điều chỉnh công nợ)

<div style="overflow-x:auto">

| Trường thông tin   | Control          | Field         | Max length | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                                 |
|:-------------------|:-----------------|:--------------|:-----------|---------------:|:-----------------|-------------------:|:------------------------------------------------------|
| Số chứng từ        | Textbox          | SoChungTu     | 50         |              Y |                  |                  Y | Validate quy tắc trùng theo BR1                       |
| Ngày chứng từ      | Date             | NgayChungTu   | -          |              Y | Ngày hiện tại    |                  Y |                                                       |
| Ngày hạch toán     | Date             | NgayHachToan  | -          |              Y | Ngày hiện tại    |                  Y | BR2                                                   |
| Diễn giải          | Textarea         | MoTa          | 500        |              N |                  |                  Y | Auto-fill: Điều chỉnh giá hàng mua từ TenNhaCungCap   |
| Mã nhà cung cấp    | Combogrid search | NhaCungCapId  | -          |              Y |                  |                 Y* | Chọn từ danh mục nhà cung cấp **ENT_NhaCungCap**. BR5 |
| Tên nhà cung cấp   | Textbox          | TenNhaCungCap | 255        |              Y | Auto-fill        |                  N | Auto-fill từ Nhà cung cấp                             |
| Mã số thuế         | Textbox          | MaSoThue      | 50         |              N | Auto-fill        |                  Y | Auto-fill từ Nhà cung cấp, cho phép sửa               |
| Địa chỉ            | Textbox          | DiaChi        | 500        |              N | Auto-fill        |                  Y | Auto-fill từ Nhà cung cấp, cho phép sửa               |
| Nhân viên mua hàng | Combogrid search | NhanVienId    | -          |              N |                  |                  Y | Chọn từ danh mục nhân viên **ENT_NhanVien**           |

</div>

#### Tab phiếu thu (ENT_ChungTuThuTien)

- Hiển thị nếu: ThanhToanNgay = true AND HinhThucThanhToan = "Phiếu thu"

<div style="overflow-x:auto">

| Trường thông tin | Control                   | Field                        | Max length | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                                             |
|:-----------------|:--------------------------|:-----------------------------|:-----------|---------------:|:-----------------|-------------------:|:------------------------------------------------------------------|
| Số chứng từ      | Textbox                   | ChungTuThuTien.SoChungTu     | 50         |              Y |                  |                  Y | BR1                                                               |
| Ngày chứng từ    | Date                      | ChungTuThuTien.NgayChungTu   |            |              Y | Ngày hiện tại    |                  Y |                                                                   |
| Ngày hạch toán   | Date                      | ChungTuThuTien.NgayHachToan  |            |              Y | Ngày hiện tại    |                  Y | BR2                                                               |
| Lý do nộp        | Textarea                  | ChungTuThuTien.MoTa          | 500        |              N |                  |                  Y | Auto-fill: Thu tiền điều chỉnh giá hàng mua từ [Tên nhà cung cấp] |
| Mã nhà cung cấp  | Combogrid search + button | ChungTuThuTien.NhaCungCapId  | 50         |              Y |                  |                 Y* | Chọn từ **ENT_NhaCungCap**. BR5                                   |
| Tên nhà cung cấp | Textbox                   | ChungTuThuTien.TenNhaCungCap | 255        |              Y | Auto-fill        |                  N | Auto-fill từ Nhà cung cấp                                         |
| Người nộp        | Textbox                   | ChungTuThuTien.NguoiNop      | 255        |              N |                  |                  Y |                                                                   |
| Địa chỉ          | Textbox                   | ChungTuThuTien.DiaChi        | 500        |              N | Auto-fill        |                  Y | Auto-fill từ Mã nhà cung cấp                                      |

</div>

#### Tab Giấy báo có (ENT_ChungTuThuTien)

- Hiển thị nếu: ThanhToanNgay = true AND HinhThucThanhToan = "Giấy báo có" (cho trường hợp Giảm giá)

<div style="overflow-x:auto">

| Trường thông tin    | Control                   | Field                             | Max length | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                                             |
|:--------------------|:--------------------------|:----------------------------------|:-----------|---------------:|:-----------------|-------------------:|:------------------------------------------------------------------|
| Số chứng từ         | Textbox                   | ChungTuThuTien.SoChungTu          | 50         |              Y | Auto (BR2)       |                  Y | BR1                                                               |
| Ngày chứng từ       | Date                      | ChungTuThuTien.NgayChungTu        |            |              Y | Ngày hiện tại    |                  Y |                                                                   |
| Ngày hạch toán      | Date                      | ChungTuThuTien.NgayHachToan       |            |              Y | Ngày hiện tại    |                  Y | BR2                                                               |
| Lý do nộp           | Textarea                  | ChungTuThuTien.MoTa               | 500        |              N |                  |                  Y | Auto-fill: Thu tiền điều chỉnh giá hàng mua từ [Tên nhà cung cấp] |
| Mã nhà cung cấp     | Combogrid search + button | ChungTuThuTien.NhaCungCapId       | 50         |              Y |                  |                 Y* | Chọn từ **ENT_NhaCungCap**. BR5                                   |
| Tên nhà cung cấp    | Textbox                   | ChungTuThuTien.TenNhaCungCap      | 255        |              Y | Auto-fill        |                  N | Auto-fill từ Nhà cung cấp                                         |
| Người nộp           | Textbox                   | ChungTuThuTien.NguoiNop           | 255        |              N |                  |                  Y |                                                                   |
| Địa chỉ             | Textbox                   | ChungTuThuTien.DiaChi             | 500        |              N | Auto-fill        |                  Y | Auto-fill từ Mã nhà cung cấp                                      |
| Tài khoản nhận tiền | Combogrid search + button | ChungTuThuTien.TaiKhoanNganHangId | 50         |              Y |                  |                  Y | Chọn từ danh mục tài khoản ngân hàng **ENT_TaiKhoanNganHang**     |
| Ngân hàng nhận tiền | Textbox                   | ChungTuThuTien.TenNganHang        | -          |              N | Auto-fill        |                  Y | Auto-fill từ tài khoản ngân hàng đã chọn                          |

</div>

#### Tab phiếu chi (ENT_ChungTuChiTien)

- Hiển thị nếu: ThanhToanNgay = true AND HinhThucThanhToan = "Phiếu chi"

<div style="overflow-x:auto">

| Trường thông tin | Control                   | Field                        | Max length | Bắt buộc (Y/N) | Giá trị mặc định                 | Cho phép sửa (Y/N) | Mô tả                        |
|:-----------------|:--------------------------|:-----------------------------|:-----------|---------------:|:---------------------------------|-------------------:|:-----------------------------|
| Mã nhà cung cấp  | Combogrid search + button | ChungTuChiTien.NhaCungCapId  | 50         |              Y |                                  |                  Y | Chọn từ **ENT_NhaCungCap**   |
| Tên nhà cung cấp | Textbox                   | ChungTuChiTien.TenNhaCungCap | 255        |              Y | Auto-fill                        |                  Y | Auto-fill từ Mã nhà cung cấp |
| Địa chỉ          | Textbox                   | ChungTuChiTien.DiaChi        | 500        |              N | Auto-fill                        |                  Y | Auto-fill từ Mã nhà cung cấp |
| Nội dung chi     | Textarea                  | ChungTuChiTien.MoTa          | 500        |              N | Chi tiền điều chỉnh giá hàng mua |                  Y |                              |
| Người nhận       | Textbox                   | ChungTuChiTien.NguoiNhanTien | 100        |              N |                                  |                  Y |                              |
| Ngày hạch toán   | Date                      | ChungTuChiTien.NgayHachToan  |            |              Y | Ngày hiện tại                    |                  Y | BR2                          |
| Ngày chứng từ    | Date                      | ChungTuChiTien.NgayChungTu   |            |              Y | Ngày hiện tại                    |                  Y |                              |
| Số chứng từ      | Textbox                   | ChungTuChiTien.SoChungTu     | 50         |              Y | BR3                              |                  Y |                              |

</div>

#### Tab Ủy nhiệm chi (ENT_ChungTuChiTien)

- Hiển thị nếu: ThanhToanNgay = true AND HinhThucThanhToan = "Ủy nhiệm chi"

<div style="overflow-x:auto">

| Trường thông tin    | Control                   | Field                                | Max length | Bắt buộc (Y/N) | Giá trị mặc định                 | Cho phép sửa (Y/N) | Mô tả                                                      |
|:--------------------|:--------------------------|:-------------------------------------|:-----------|---------------:|:---------------------------------|-------------------:|:-----------------------------------------------------------|
| Mã nhà cung cấp     | Combogrid search + button | ChungTuChiTien.NhaCungCapId          | 50         |              Y |                                  |                  Y | Chọn từ **ENT_NhaCungCap**                                 |
| Tên nhà cung cấp    | Textbox                   | ChungTuChiTien.TenNhaCungCap         | 255        |              Y | Auto-fill                        |                  Y | Auto-fill từ Mã nhà cung cấp                               |
| Địa chỉ             | Textbox                   | ChungTuChiTien.DiaChi                | 500        |              N | Auto-fill                        |                  Y | Auto-fill từ Mã nhà cung cấp                               |
| Nội dung thanh toán | Textarea                  | ChungTuChiTien.MoTa                  | 500        |              N | Chi tiền điều chỉnh giá hàng mua |                  Y |                                                            |
| Tài khoản chi       | Combogrid search + button | ChungTuChiTien.TaiKhoanNganHangChiId | 50         |              Y |                                  |                  Y | Tài khoản ngân hàng chi (chọn từ **ENT_TaiKhoanNganHang**) |
| Tên ngân hàng       | Textbox                   | ChungTuChiTien.TenNganHangChi        | 255        |              N | Auto-fill                        |                  Y | Auto-fill từ Ngân hàng chi                                 |
| Tài khoản nhận      | Combogrid search + button | ChungTuChiTien.TaiKhoanNganHangThuId | 50         |              N |                                  |                  Y | Chọn từ **ENT_TaiKhoanNganHang**                           |
| Tên ngân hàng nhận  | Textbox                   | ChungTuChiTien.TenNganHangThu        | 255        |              N | Auto-fill                        |                  Y | Auto-fill từ Tài khoản nhận                                |
| Ngày hạch toán      | Date                      | ChungTuChiTien.NgayHachToan          |            |              Y | Ngày hiện tại                    |                  Y | BR2                                                        |
| Ngày chứng từ       | Date                      | ChungTuChiTien.NgayChungTu           |            |              Y | Ngày hiện tại                    |                  Y |                                                            |
| Số chứng từ         | Textbox                   | ChungTuChiTien.SoChungTu             | 50         |              Y |                                  |                  Y |                                                            |

</div>

#### Tab Séc chuyển khoản (ENT_ChungTuChiTien)

- Hiển thị nếu: ThanhToanNgay = true AND HinhThucThanhToan = "Séc chuyển khoản"

Giống Tab Ủy nhiệm chi.

#### Tab Séc tiền mặt (ENT_ChungTuChiTien)

- Hiển thị nếu: ThanhToanNgay = true AND HinhThucThanhToan = "Séc tiền mặt"

<div style="overflow-x:auto">

| Trường thông tin    | Control                   | Field                                | Max length | Bắt buộc (Y/N) | Giá trị mặc định                 | Cho phép sửa (Y/N) | Mô tả                                                      |
|:--------------------|:--------------------------|:-------------------------------------|:-----------|---------------:|:---------------------------------|-------------------:|:-----------------------------------------------------------|
| Mã nhà cung cấp     | Combogrid search + button | ChungTuChiTien.NhaCungCapId          | 50         |              Y |                                  |                  Y | Chọn từ **ENT_NhaCungCap**                                 |
| Tên nhà cung cấp    | Textbox                   | ChungTuChiTien.TenNhaCungCap         | 255        |              Y | Auto-fill                        |                  Y | Auto-fill từ Mã nhà cung cấp                               |
| Địa chỉ             | Textbox                   | ChungTuChiTien.DiaChi                | 500        |              N | Auto-fill                        |                  Y | Auto-fill từ Mã nhà cung cấp                               |
| Nội dung thanh toán | Textarea                  | ChungTuChiTien.MoTa                  | 500        |              N | Chi tiền điều chỉnh giá hàng mua |                  Y |                                                            |
| Tài khoản chi       | Combogrid search + button | ChungTuChiTien.TaiKhoanNganHangChiId | 50         |              Y |                                  |                  Y | Tài khoản ngân hàng chi (chọn từ **ENT_TaiKhoanNganHang**) |
| Tên ngân hàng       | Textbox                   | ChungTuChiTien.TenNganHangChi        | 255        |              N | Auto-fill                        |                  Y | Auto-fill từ Ngân hàng chi                                 |
| Người lĩnh tiền     | Textbox                   | ChungTuChiTien.NguoiLinhTien         | 100        |              N |                                  |                  Y |                                                            |
| Số giấy tờ          | Textbox                   | ChungTuChiTien.SoGiayTo              | 12         |              N |                                  |                  Y | Validate 12 số không dấu cách và ký tự                     |
| Ngày cấp            | Date                      | ChungTuChiTien.NgayCap               |            |              N |                                  |                  Y |                                                            |
| Nơi cấp             | Textbox                   | ChungTuChiTien.NoiCap                | 255        |              N |                                  |                  Y |                                                            |
| Nội dung thanh toán | Textarea                  | ChungTuChiTien.MoTa                  | 500        |              N | Chi tiền điều chỉnh giá hàng mua |                  Y |                                                            |
| Ngày hạch toán      | Date                      | ChungTuChiTien.NgayHachToan          |            |              Y | Ngày hiện tại                    |                  Y | BR2                                                        |
| Ngày chứng từ       | Date                      | ChungTuChiTien.NgayChungTu           |            |              Y | Ngày hiện tại                    |                  Y |                                                            |
| Số chứng từ         | Textbox                   | ChungTuChiTien.SoChungTu             | 50         |              Y | BR3                              |                  Y |                                                            |

</div>

### Section 3

#### Thông tin khác

| Trường thông tin        | Control       | Field               | Max length | Bắt buộc (Y/N) | Giá trị mặc định         | Cho phép sửa (Y/N) | Mô tả                                                                                                                                     |
|:------------------------|:--------------|:--------------------|:-----------|---------------:|:-------------------------|-------------------:|:------------------------------------------------------------------------------------------------------------------------------------------|
| Loại tiền               | Select search | LoaiTienId          | -          |              Y | Theo đồng tiền hạch toán |                 Y* | Chọn từ danh mục loại tiền tệ **ENT_LoaiTien**. BR5                                                                                       |
| Tỷ giá                  | Numeric       | TyGia               | -          |              Y | Auto-fill                |                  Y | Auto-fill từ loại tiền, chỉ hiện nếu loại tiền khác đồng tiền hạch toán                                                                   |
| Tự động tính Thành tiền | Checkbox      | TuDongTinhThanhTien | -          |              N | true                     |                  Y | Nếu tích: Số lượng × Đơn giá = Thành tiền (tính ngược lại). Nếu không tích: không thực hiện logic này. Luôn validate SL × ĐG = TT khi lưu |

#### Tab chi tiết điều chỉnh

##### Trường hợp chọn "Giảm giá hàng mua" hoặc "Tăng giá hàng mua"

Hiển thị 1 grid chi tiết điều chỉnh:

<div style="overflow-x:auto">

| Cột                       | Control                   | Field                      | Max length | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                                                                                                                                                |
|:--------------------------|:--------------------------|:---------------------------|:-----------|---------------:|:-----------------|-------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mã hàng                   | Combogrid search + button | MaHangId                   |            |              Y |                  |                  Y | Chọn từ danh mục hàng hóa **ENT_VatTu**                                                                                                                              |
| Tên hàng                  | Textlabel                 | TenHang                    |            |              N | Auto-fill        |                  N | Auto-fill từ mã hàng                                                                                                                                                 |
| Kho                       | Combogrid search + button | MaKhoId                    |            |             Y* | Auto-fill        |                 Y* | Chọn 1 từ danh mục kho **ENT_Kho**, ẩn cột nếu DieuChinhGiaTriHangNhapKho = False. Cho phép thêm nhanh, bấm thêm nhanh mở popup **SCR_DMKho_ThemMoi**. Tuân theo BR7 |
| TK Nợ                     | Combogrid search + button | TaiKhoanNo                 |            |              Y | Auto-fill        |                  Y | Chọn từ danh mục hệ thống tài khoản **ENT_HeThongTaiKhoan**. Cho phép thêm nhanh, bấm thêm nhanh mở popup **SCR_HeThongTaiKhoan_ThemMoi**                            |
| TK Có                     | Combogrid search + button | TaiKhoanCo                 |            |              Y | Auto-fill        |                  Y | Chọn từ danh mục hệ thống tài khoản **ENT_HeThongTaiKhoan**. Cho phép thêm nhanh, bấm thêm nhanh mở popup **SCR_HeThongTaiKhoan_ThemMoi**                            |
| Đơn vị tính               | Select                    | DonViTinhId                |            |              Y | Auto-fill        |                  Y | Auto-fill từ Hàng hóa, cho phép sửa. Chọn từ danh mục đơn vị tính **ENT_DonViTinh**                                                                                  |
| Số lượng                  | Number                    | SoLuong                    |            |              Y | null             |                  Y | Nhập số lượng , > 0. Nếu checkbox "Tự động tính" tích: update lại Thành tiền = SoLuong × DonGia. Nếu không tích: không update lại                                    |
| Đơn giá                   | Number                    | DonGia                     |            |              Y | Auto-fill        |                  Y | >= 0. Nếu checkbox "Tự động tính" tích: update lại Thành tiền = SoLuong × DonGia. Nếu không tích: không update lại                                                   |
| Thành tiền                | Number                    | ThanhTien                  |            |              Y | Auto-calc        |                  N | Nếu checkbox "Tự động tính" tích: = SoLuong × DonGia (không cho phép sửa). Nếu không tích: cho phép nhập thủ công, chỉnh sửa update lại Đơn giá, >= 0                |
| Thành tiền (quy đổi)      | Number                    | ThanhTienQuyDoi            |            |              Y | Auto-calc        |                  Y | = ThanhTien × TyGia, cho phép sửa, không ảnh hưởng tiền nguyên tệ, >= 0                                                                                              |
| Thuế suất GTGT            | Select                    | ThueSuatGTGTId             |            |              N |                  |                  Y | Chọn từ danh mục thuế suất **ENT_ThueSuatGTGT**                                                                                                                      |
| Tiền thuế GTGT            | Number                    | TienThueGTGT               |            |              N | Auto-calc        |                  N | = ThanhTien × ThueSuatGTGT, cho phép sửa không update lại thuế suất, >= 0                                                                                            |
| Tiền thuế GTGT (quy đổi)  | Number                    | TienThueGTGTQuyDoi         |            |              N | Auto-calc        |                  Y | = TienThueGTGT × TyGia, cho phép sửa, không ảnh hưởng tiền nguyên tệ, >= 0                                                                                           |
| Nhóm HHDV mua vào         | Select                    | TinhChatThueGTGTId         |            |              N |                  |                  Y | Chọn từ danh mục tính chất thuế GTGT **ENT_TinhChatThueGTGT**                                                                                                        |
| TK Thuế GTGT              | Combogrid search + button | TaiKhoanThueGTGTId         |            |              N | Auto-fill        |                  Y | Chọn từ danh mục hệ thống tài khoản **ENT_HeThongTaiKhoan**. Cho phép thêm nhanh, bấm thêm nhanh mở popup **SCR_HeThongTaiKhoan_ThemMoi**                            |
| Tổng thanh toán           | Number                    | TongThanhToan              |            |              Y | Auto-calc        |                  N | = Thành tiền + Tiền thuế GTGT                                                                                                                                        |
| Tổng thanh toán (quy đổi) | Number                    | TongThanhToanQuyDoi        |            |              Y | Auto-calc        |                  Y | = Thành tiền quy đổi + Tiền thuế GTGT quy đổi, cho phép sửa, >= 0                                                                                                    |
| Ngày chứng từ             | Textlabel                 | ChungTuMuaHang.NgayChungTu |            |              N |                  |                  N | Auto-fill từ mã hàng được lựa chọn từ chứng từ. Chỉ hiển thị cột này nếu đã chọn từ chứng từ                                                                         |
| Số chứng từ               | Textlabel                 | ChungTuMuaHang.SoChungTu   |            |              N |                  |                  N | Auto-fill từ mã hàng được lựa chọn từ chứng từ. Chỉ hiển thị cột này nếu đã chọn từ chứng từ                                                                         |
| Số hóa đơn                | Textlabel                 | ChungTuMuaHang.SoHoaDon    |            |              N |                  |                  N | Auto-fill từ mã hàng được lựa chọn từ chứng từ. Chỉ hiển thị cột này nếu đã chọn từ chứng từ                                                                         |
| Số lô                     | Textbox                   | SoLo                       |            |              N | Auto-fill        |                  Y |                                                                                                                                                                      |
| Hạn sử dụng               | Date                      | HanSuDung                  |            |              N | Auto-fill        |                  Y |                                                                                                                                                                      |
| Đơn vị                    | Combogrid search          | DonViId                    |            |              N |                  |                  Y | Chọn từ danh mục đơn vị **ENT_DonVi**                                                                                                                                |
| Khoản mục chi phí         | Combogrid search          | KhoanMucChiPhiId           |            |              N |                  |                  Y | Chọn từ danh mục khoản mục chi phí **ENT_KhoanMucChiPhi**                                                                                                            |
| Vụ việc                   | Combogrid search          | VuViecId                   |            |              N |                  |                  Y | Chọn từ danh mục vụ việc **ENT_CongTrinh**                                                                                                                           |
| Đối tượng THCP            | Combogrid search          | DoiTuongTHCPId             |            |              N |                  |                  Y | Chọn từ danh mục đối tượng tập hợp chi phí **ENT_DoiTuongTHCP**                                                                                                      |

</div>

##### Nút chức năng

<div style="overflow-x:auto">

| Chức năng     | Loại   | Mô tả                                                                                                                                                          |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Thêm dòng     | Button | Hiện cuối tab, bấm vào thêm mới 1 dòng trong danh sách chi tiết điều chỉnh. Trường hợp cấu hình **Phương pháp tính giá** là "Đích danh" ẩn nút thêm dòng tự do |
| Xóa dòng      | Button | Hiện trên mỗi dòng được thêm, bấm vào xóa dòng tương ứng                                                                                                       |
| Nhân bản dòng | Button | Hiện trên mỗi dòng được thêm, bấm vào nhân bản dòng tương ứng                                                                                                  |

</div>

##### Trường hợp chọn "Điều chỉnh tăng & giảm giá hàng mua"

Hiển thị 2 grid riêng biệt, dạng đóng/mở được:

**Grid 1: Danh sách điều chỉnh TĂNG** ▼

<div style="overflow-x:auto">

| Cột                       | Control                   | Field               | Max length | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                    |
|:--------------------------|:--------------------------|:-------------------|:-----------|---------------:|:-----------------|-------------------:|:-----------------------------------------|
| (Cột giống Grid đơn ở trên)                                                                                                                                 |

</div>

- Nút chức năng: Thêm dòng, Xóa dòng, Nhân bản dòng (riêng cho grid Tăng)

**Grid 2: Danh sách điều chỉnh GIẢM** ▼

<div style="overflow-x:auto">

| Cột                       | Control                   | Field               | Max length | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                    |
|:--------------------------|:--------------------------|:-------------------|:-----------|---------------:|:-----------------|-------------------:|:-----------------------------------------|
| (Cột giống Grid đơn ở trên)                                                                                                                                 |

</div>

- Nút chức năng: Thêm dòng, Xóa dòng, Nhân bản dòng (riêng cho grid Giảm)

#### Tab hạch toán

- Hạch toán theo mô tả trong use case thêm mới

#### Tab tham chiếu

- Giống các phần khác

### Section 5: Tổng hợp

#### Tổng hợp tiền tệ

- Hiển thị thêm đuôi theo cách đọc tiền đã cấu hình của tenant, giá trị tuân theo loại tiền hạch toán.

**Trường hợp chỉ TĂNG hoặc chỉ GIẢM:**

<div style="overflow-x:auto">

| Hạng mục        | Control | Field             | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                              |
|:----------------|:--------|:------------------|---------------:|:-----------------|-------------------:|:---------------------------------------------------|
| Tổng tiền hàng  | Number  | TongTienHangHoa   |              Y | Auto-calc        |                  N | = Σ(ThanhTien) của tất cả dòng chi tiết điều chỉnh |
| Tiền thuế GTGT  | Number  | TongTienThueGTGT  |              N | Auto-calc        |                  N | = Σ(Tiền thuế) của tất cả dòng chi tiết điều chỉnh |
| Tổng thanh toán | Number  | TongTienThanhToan |              Y | Auto-calc        |                  N | = Tổng tiền hàng + Tiền thuế GTGT                  |

</div>

**Trường hợp TĂNG & GIẢM đồng thời:**

- Giá trị âm thể hiện số tiền đang giảm đi và ngược lại

<div style="overflow-x:auto">

| Hạng mục        | Control | Field             | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                                                                          |
|:----------------|:--------|:------------------|---------------:|:-----------------|-------------------:|:-----------------------------------------------------------------------------------------------|
| Tổng tiền hàng  | Number  | TongTienHang      |              Y | Auto-calc        |                  N | = Σ(ThanhTien) của tất cả dòng trong grid TĂNG - Σ(ThanhTien) của tất cả dòng trong grid giảm  |
| Tiền thuế GTGT  | Number  | TongTienThueTGTT  |              N | Auto-calc        |                  N | = Σ(Tiền thuế) của tất cả dòng trong grid TĂNG -  Σ(Tiền thuế) của tất cả dòng trong grid giảm |
| Tổng thanh toán | Number  | TongTienThanhToan |              Y | Auto-calc        |                  N | = (Tổng tiền hàng TĂNG - Tổng tiền hàng GIẢM) + (Tiền thuế GTGT TĂNG - Tiền thuế GTGT GIẢM)    |

</div>

#### Tổng hợp tiền tệ (theo quy đổi)

- Hiển thị nếu loại tiền được chọn khác loại tiền hạch toán.
- Hiển thị thêm đuôi ở tiêu đề và tiền theo cách đọc tiền đã cấu hình của tenant, giá trị tuân theo loại tiền hạch toán.
- **Lưu ý:** Tổng hợp bằng cách cộng các field quy đổi của từng dòng (đã được tính và làm tròn tại dòng đó), KHÔNG nhân tổng VND với tỷ giá.

**Trường hợp chỉ TĂNG hoặc chỉ GIẢM:**

<div style="overflow-x:auto">

| Hạng mục        | Control | Field                   | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                                       |
|:----------------|:--------|:------------------------|---------------:|:-----------------|-------------------:|:------------------------------------------------------------|
| Tổng tiền hàng  | Number  | TongTienHangHoaQuyDoi   |              Y | Auto-calc        |                  Y | = Σ(ThanhTienQuyDoi) của tất cả dòng chi tiết điều chỉnh    |
| Tiền thuế GTGT  | Number  | TongTienThueGTGTQuyDoi  |              N | Auto-calc        |                  Y | = Σ(TienThueGTGTQuyDoi) của tất cả dòng chi tiết điều chỉnh |
| Tổng thanh toán | Number  | TongTienThanhToanQuyDoi |              Y | Auto-calc        |                  Y | = TongTienHangHoaQuyDoi + TongTienThueQuyDoi                |

</div>

**Trường hợp TĂNG & GIẢM đồng thời:**

<div style="overflow-x:auto">

| Hạng mục        | Control | Field                   | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Mô tả                                                                                                          |
|:----------------|:--------|:------------------------|---------------:|:-----------------|-------------------:|:---------------------------------------------------------------------------------------------------------------|
| Tổng tiền hàng  | Number  | TongTienHangQuyDoi      |              Y | Auto-calc        |                  N | = Σ(ThanhTienQuyDoi) của tất cả dòng trong grid TĂNG - Σ(ThanhTienQuyDoi) của tất cả dòng trong grid giảm      |
| Tiền thuế GTGT  | Number  | TongTienThueTGTTQuyDoi  |              N | Auto-calc        |                  N | = Σ(Tiền thuế quy đổi) của tất cả dòng trong grid TĂNG -  Σ(Tiền thuế quy đổi) của tất cả dòng trong grid giảm |
| Tổng thanh toán | Number  | TongTienThanhToanQuyDoi |              Y | Auto-calc        |                  N | = (Tổng tiền hàng TĂNG - Tổng tiền hàng GIẢM) + (Tiền thuế GTGT TĂNG - Tiền thuế GTGT GIẢM)                    |

</div>

## Chức năng

<div style="overflow-x:auto">

| Nút           | Mô tả                               | Action                                  |
|:--------------|:------------------------------------|:----------------------------------------|
| In            | Nút in chứng từ đang thêm mới       | In chứng từ                             |
| Lưu nháp      | Nút lưu chứng từ nhưng không ghi sổ | Lưu nháp chứng từ theo UC_DCGHM_ThemMoi |
| Lưu và ghi sổ |                                     | Lưu chứng từ và ghi sổ UC_DCGHM_ThemMoi |
| Hủy/Đóng      |                                     | Hiện popup xác nhận đóng                |

</div>

## Rule

**BR1**: Quy tắc check trùng số chứng từ: Kiểm tra theo: Số chứng từ + Loại chứng từ trong cùng 1 quyển chứng từ của tenant

**BR2**: Ngày hạch toán phải lớn hơn hoặc bằng Ngày chứng từ.

**BR3**: Áp dụng quy tắc làm tròn trong cấu hình của tenant.

**BR4**: Các thông tin trong combogrid hiển thị theo quy tắc trong business rules chung.

**BR5**: Các trường thông tin được đánh dấu mã này sẽ không được phép sửa nếu như dữ liệu đã được auto-fill sau khi chọn hàng hóa từ chứng từ gốc.

**BR6**: Validate Số lượng × Đơn giá = Thành tiền khi lưu (dù checkbox Tự động tính có bật hay không)

**BR7**:
- Trường hợp vật tư được chọn là dịch vụ, trường Kho sẽ không bắt buộc và bị disable.
- Trường hợp vật tư được là loại hàng hóa, trường Kho là bắt buộc, cho phép sửa và được auto-fill theo hàng hóa đã chọn từ chứng từ

**BR8**:
- Hiển thị các cột tiền quy đổi nếu: Loại tiền được chọn khác loại tiền hạch toán
- Các field này **cho phép sửa trực tiếp** mà không ảnh hưởng đến field tiền nguyên tệ
- Giá trị được sinh từ loại tiền và tỷ giá, nhưng người dùng có thể điều chỉnh nếu cần
- Khi sửa tỷ giá, hệ thống auto-recalc lại các field quy đổi (trừ khi người dùng đã sửa thủ công)
- Khi sửa field tiền nguyên tệ, hệ thống auto-recalc lại field quy đổi (trừ khi người dùng đã sửa thủ công)

**BR9**: Hình thức thanh toán cho nghiệp vụ điều chỉnh:
   - Tăng giá hàng mua → Chỉ chọn option chi tiền: Phiếu chi, Ủy nhiệm chi, Séc tiền mặt, Séc chuyển khoản
   - Giảm giá hàng mua → Chỉ chọn option thu tiền: Phiếu thu, Giấy báo có
   - Điều chỉnh tăng & giảm → Cho phép chọn 1 trong all, khi lưu validate Tổng tiền thanh toán âm/dương để xác định tạo chứng từ thu hay chi

**BR10**: Hiển thị các cột tiền quy đổi nếu: Loại tiền được chọn khác loại tiền hạch toán

**BR11**: Trường hợp Tăng & Giảm đồng thời, hiển thị 2 grid riêng biệt dạng đóng/mở. Trường hợp chỉ Tăng hoặc chỉ Giảm, hiển thị 1 grid không cần dạng đóng/mở

**BR12**: Trường hợp không có hóa đơn, không hiển thị các cột liên quan tới thuế: thuế suất, tiền thuế gtgt, nhóm HHDV mua vào, tk thuế gtgt

**BR13**: Checkbox "Tự động tính Thành tiền":
   - Nếu tích: Số lượng × Đơn giá = Thành tiền (tự động tính, không cho phép sửa Thành tiền)
   - Nếu không tích: Cho phép nhập thủ công Thành tiền, khi sửa Thành tiền sẽ update lại Đơn giá
   - Luôn validate Số lượng × Đơn giá = Thành tiền khi lưu (dù checkbox có bật hay không)
