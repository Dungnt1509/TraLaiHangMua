# Màn hình: Danh sách chứng từ điều chỉnh giá hàng mua

Màn hình chính để xem và quản lý danh sách chứng từ điều chỉnh giá hàng mua của tenant.

## Điều kiện tiên quyết

- Người dùng đã đăng nhập và có quyền xem danh sách chứng từ điều chỉnh giá hàng mua

## Nguyên mẫu

[Đang bổ sung]

## Thành phần

### Bảng danh sách

- Nếu chưa ghi sổ thì highlight dòng chứng từ lên

<div style="overflow-x:auto">

| Trường thông tin           | Control       | Field                   | Max length | Bắt buộc (Y/N) | Giá trị mặc định | Cho phép sửa (Y/N) | Tìm kiếm (Y/N) | Mô tả                                                                                                                                    |
|:---------------------------|:--------------|:------------------------|:-----------|---------------:|:-----------------:|:-------------------|:--------------:|:-----------------------------------------------------------------------------------------------------------------------------------------|
| Checkbox                   | checkbox      | -                       | -          |              - |                - | -                  |       N        | Chọn để thực hiện thao tác hàng loạt                                                                                                   |
| STT                        | text          | -                       | -          |              - |                - | -                  |       N        | Số thứ tự                                                                                                                               |
| Ngày hạch toán             | date          | NgayHachToan            | -          |              - |                - | -                  |       Y        | Ngày hạch toán chứng từ điều chỉnh giá hàng mua                                                                                          |
| Số chứng từ                | text/link     | SoChungTu               | -          |              - |                - | -                  |       Y        | Số chứng từ điều chỉnh giá hàng mua, click để xem chi tiết                                                                               |
| Số hóa đơn                 | text          | SoHoaDon                | -          |              - |                - | -                  |       Y        | Hiển thị số hóa đơn, nếu không có thì bỏ trống                                                                                           |
| Nhà cung cấp               | text          | TenNhaCungCap           | -          |              - |                - | -                  |       Y        | Tên nhà cung cấp trên chứng từ điều chỉnh giá hàng mua (ChungTuDieuChinhGiaHangMua.TenNhaCungCap)                                  |
| Lý do điều chỉnh           | text          | LyDoDieuChinh           | -          |              - |                - | -                  |       Y        | Lý do điều chỉnh: Giảm giá hàng mua / Tăng giá hàng mua / Điều chỉnh tăng & giảm giá hàng mua                                         |
| Tổng tiền thanh toán (VNĐ) | number        | TongTienThanhToanQuyDoi | -          |              - |                - | -                  |       N        | Tổng tiền thanh toán quy đổi                                                                                                             |
| Trạng thái hóa đơn        | badge/text    | TrangThaiHoaDon        | -          |              - |                - | -                  |       Y        | Đã có hóa đơn / Chưa có hóa đơn / Không có hóa đơn                                                                                      |
| Hình thức thanh toán       | badge/text    | ThanhToanNgay           | -          |              - |                - | -                  |       Y        | Điều chỉnh công nợ / Thanh toán ngay                                                                                                   |
| Trạng thái chứng từ        | badge/text    | TrangThaiChungTu        | -          |              - |                - | -                  |       Y        | Đã ghi sổ / Chưa ghi sổ                                                                                                                  |
| Chức năng                  | action column | -                       | -          |              - |                - | -                  |       N        | Các nút/icon: Xem, Sửa, Bỏ ghi, Ghi sổ, Nhân bản, Xóa                                                                                   |

</div>

### Chức năng trên từng dòng

<div style="overflow-x:auto">

| Tên          | Loại        | Mô tả                                                                                                                           |
|:-------------|:------------|:----------------------------------------------------------------------------------------------------------------------------------|
| Nút Xem      | button/icon | Bấm vào hiển thị popup xem chi tiết chứng từ (**SCR_DCGHM_XemChiTiet**). Chỉ hiển thị khi có quyền xem chi tiết                        |
| Nút Sửa      | button/icon | Bấm vào hiển thị popup sửa thông tin (**SCR_DCGHM_Sua**). Chỉ hiển thị khi chứng từ chưa ghi sổ và có quyền sửa chứng từ            |
| Nút Bỏ ghi   | button/icon | Bấm vào hiển thị popup xác nhận bỏ ghi sổ (**AD_DCGHM_BoGhiSo**). Chỉ hiển thị khi chứng từ đã ghi sổ và có quyền bỏ ghi sổ           |
| Nút Ghi sổ   | button/icon | Bấm vào hiển thị popup xác nhận ghi sổ (**AD_DCGHM_GhiSo**). Chỉ hiển thị khi chứng từ chưa ghi sổ và có quyền ghi sổ               |
| Nút Nhân bản | button/icon | Bấm vào nhân bản chứng từ (**AD_DCGHM_NhanBan**). Chỉ hiển thị khi có quyền nhân bản chứng từ                                       |
| Nút Xóa      | button/icon | Bấm vào hiển thị popup xác nhận xóa (**AD_DCGHM_Xoa**). Chỉ hiển thị khi chứng từ ở trạng thái chưa ghi sổ và có quyền xóa chứng từ |

</div>

### Các nút chức năng khác

<div style="overflow-x:auto">

| Tên                   | Loại        | Mô t                                                                                                                                                          |
|:----------------------|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nút Thêm mới          | button      | Bấm vào hiển thị popup thêm mới (**SCR_DCGHM_ThemMoi**). Chỉ hiển thị khi có quyền thêm mới chứng từ                                                        |
| Nút Tìm kiếm          | button/icon | Bấm vào để tìm kiếm theo điều kiện (**AD_DCGHM_TimKiem**)                                                                                                   |
| Nút Xóa bộ lọc        | button/icon | Bấm vào để xóa điều kiện tìm kiếm, hiển thị danh sách mặc định                                                                                              |
| Nút Làm mới danh sách | button/icon | Bấm vào để làm mới danh sách, tải lại dữ liệu mới nhất mà không xóa bộ lọc                                                                                |
| Nút Xóa hàng loạt     | button      | Bấm vào xóa nhiều chứng từ đã chọn (**AD_DCGHM_Xoa**). Chỉ hiển thị khi có quyền xóa, đã chọn ít nhất 1 chứng từ. Disable nút này nếu chọn chứng từ đã ghi sổ |

</div>

### Sắp xếp

- Mặc định: Theo thời gian tạo chứng từ từ mới tới cũ nhất
- Click vào tiêu đề cột để sắp xếp theo thứ tự tăng dần/giảm dần
