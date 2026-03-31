# Use Case: UC_DCGHM_XemDanhSach - Xem danh sách chứng từ điều chỉnh giá hàng mua

## User Story

- Là **Kế toán**, tôi muốn xem được danh sách chứng từ điều chỉnh giá hàng mua do tổ chức tôi đã tạo lập để quản lý và theo dõi thông tin.

## Acceptance criteria

- Hiển thị bảng danh sách với các cột: Checkbox, STT, Ngày hạch toán, Số chứng từ, Số hóa đơn, Nhà cung cấp, Lý do điều chỉnh, Tổng tiền thanh toán, Trạng thái hóa đơn, Hình thức thanh toán, Trạng thái chứng từ (Đã ghi sổ, Chưa ghi sổ)
- Cột "Chức năng" hiển thị các nút: Xem, Sửa, Xóa, Nhân bản, Bỏ ghi, Ghi sổ
- Cho phép xóa hàng loạt
- Hỗ trợ phân trang
- Hỗ trợ tìm kiếm trên từng cột và tìm kiếm chung
- Hỗ trợ sắp xếp theo từng cột
- Mặc định sắp xếp theo thời gian tạo chứng từ từ mới tới cũ nhất

## Tác nhân chính

- Kế toán

## Tiền điều kiện

- Người dùng đã đăng nhập hệ thống
- Người dùng có quyền xem danh sách chứng từ điều chỉnh giá hàng mua (Permission: `DDCGHM.VIEW`)

## Luồng chính

1. Người dùng có quyền truy cập thành công vào màn hình danh sách chứng từ điều chỉnh giá hàng mua
2. Hệ thống tải danh sách chứng từ điều chỉnh giá hàng mua
3. Hệ thống hiển thị danh sách với các cột: Checkbox, STT, Ngày hạch toán, Số chứng từ, Số hóa đơn, Nhà cung cấp, Lý do điều chỉnh, Tổng tiền thanh toán, Trạng thái hóa đơn, Hình thức thanh toán, Trạng thái chứng từ (Đã ghi sổ, Chưa ghi sổ)
4. Người dùng có thể thực hiện các thao tác nếu có quyền:
   - **Tìm kiếm**: Nhập từ khóa để tìm kiếm trên từng cột và tìm kiếm chung
   - **Phân trang**: Chọn số trang hoặc số dòng/trang
   - **Sắp xếp**: Click vào tiêu đề cột để sắp xếp lại theo thứ tự tăng dần/giảm dần
   - **Thêm mới chứng từ**: Chọn nút "Thêm mới" (**AD_DCGHM_ThemMoi**)
   - **Sửa**: Chọn nút "Sửa" trên dòng dữ liệu (**AD_DCGHM_Sua**)
   - **Xóa**: Chọn nút "Xóa" trên dòng dữ liệu (**AD_DCGHM_Xoa**)
   - **Bỏ ghi**: Chọn nút tương ứng trên dòng dữ liệu (**AD_DCGHM_BoGhiSo**)
   - **Ghi sổ**: Chọn nút tương ứng trên dòng dữ liệu (**AD_DCGHM_GhiSo**)
   - **Nhân bản**: Chọn nút tương ứng trên dòng dữ liệu (**AD_DCGHM_NhanBan**)
   - **Xem chi tiết**: Chọn nút tương ứng trên dòng dữ liệu (**AD_DCGHM_XemChiTiet**)
   - **Làm mới**: Chọn nút "Làm mới" để làm mới lại danh sách
   - **Xóa hàng loạt**: Chọn 1 hoặc nhiều dòng bằng checkbox và chọn nút xóa (**AD_DCGHM_Xoa**)

5. Kết thúc

## Ngoại lệ

- Nếu người dùng không có quyền xem danh sách: Hệ thống không hiển thị chức năng
- Nếu tải dữ liệu thất bại: Hiển thị thông báo lỗi
- Nếu danh sách trống: Hiển thị thông báo danh sách trống

## Hậu điều kiện

- Nếu thành công: Người dùng xem được danh sách chứng từ điều chỉnh giá hàng mua
- Nếu thất bại: Hiển thị thông báo lỗi tương ứng

## Phân quyền chi tiết

| Vai trò         | Quyền         | Mô tả                                       |
|-----------------|---------------|----------------------------------------------|
| Người dùng      | `DDCGHM.VIEW`  | Có quyền xem danh sách chứng từ điều chỉnh giá hàng mua của tenant |

## Quy tắc hiển thị danh sách

- Mặc định: 20 dòng/trang
- Sắp xếp mặc định: Theo thời gian tạo chứng từ từ mới tới cũ nhất

## Liên kết

- Activity Diagram: [AD_DCGHM_XemDanhSach.puml](AD_DCGHM_XemDanhSach.puml)
- Form/Screen: [SCR_DCGHM_DanhSach.md](../../5.screens/SCR_DCGHM_DanhSach.md)
- Entity liên quan: **ENT_ChungTuDieuChinhGiaHangMua**, **ENT_HoaDonDieuChinh**, **ENT_ChungTuThuTien**, **ENT_ChungTuChiTien**
