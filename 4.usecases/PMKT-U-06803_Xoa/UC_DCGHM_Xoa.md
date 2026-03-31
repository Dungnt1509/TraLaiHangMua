# Use Case: UC_DCGHM_Xoa - Xóa chứng từ điều chỉnh giá hàng mua

## User Story

- Là **Kế toán**, tôi muốn xóa một hoặc nhiều chứng từ điều chỉnh giá hàng mua để loại bỏ các chứng từ không cần sử dụng nữa
- Tôi cần hệ thống chỉ cho phép xóa chứng từ ở trạng thái "Chưa ghi sổ" để đảm bảo tính toàn vẹn dữ liệu
- Tôi cần xóa được nhiều chứng từ cùng lúc để thao tác nhanh hơn

## Acceptance criteria

- Cho phép xóa một hoặc nhiều chứng từ cùng lúc
- Chỉ cho phép xóa chứng từ ở trạng thái "Chưa ghi sổ"
- Hiển thị popup xác nhận trước khi xóa
- Xóa thành công: xóa chứng từ và các dữ liệu liên quan
- Phân quyền: Chỉ người dùng có quyền mới hiển thị chức năng xóa

## Tác nhân chính

- Kế toán

## Tiền điều kiện

- Người dùng đã đăng nhập hệ thống
- Người dùng có quyền xóa chứng từ điều chỉnh giá hàng mua (Permission: `DDCGHM.DELETE`)

## Luồng chính

1. Người dùng vào màn hình danh sách (**SCR_DCGHM_DanhSach**)
2. Người dùng chọn một hoặc nhiều chứng từ cần xóa:
   - Xóa 1 chứng từ: Bấm nút "Xóa" trên dòng chứng từ
   - Xóa nhiều chứng từ: Chọn checkbox ở các dòng, sau đó bấm nút "Xóa đã chọn"
3. Hệ thống hiển thị popup xác nhận **SCR_DCGHM_Xoa**
4. Nếu người dùng chọn "Hủy" → Đóng popup, kết thúc
5. Nếu người dùng chọn "Xác nhận" → Hệ thống validate dữ liệu (xem mục **Validate trước khi xóa**)
6. Nếu validate fail → Hiển thị thông báo lỗi, không xóa
7. Nếu validate pass → Hệ thống thực hiện xóa:
8. Xóa toàn bộ dữ liệu được tạo lập kèm với chứng từ: **ENT_ChungTuDieuChinhGiaHangMua**, **ENT_ChiTietChungTuDieuChinhGiaHangMua**, **ENT_HoaDonDieuChinh**, **ENT_ChungTuThuTien**, **ENT_ChungTuChiTien**.
9. Hệ thống hiển thị thông báo xóa thành công
10. Refresh danh sách
11. Kết thúc

## Luồng phụ

Không có

## Ngoại lệ

| Trường hợp           | Xử lý                    | Messages                         |
|:---------------------|:-------------------------|:---------------------------------|
| Không có quyền       | Không hiển thị tính năng |                                  |
| Lỗi hệ thống khi xóa | Hiển thị lỗi, rollback   | "Lỗi hệ thống, vui lòng thử lại" |

## Hậu điều kiện

- **Xóa thành công**:
  - Chứng từ và các dữ liệu liên quan bị xóa hoàn toàn
  - Danh sách được refresh
  - Hiển thị thông báo thành công
- **Xóa thất bại**: Hiển thị thông báo lỗi, giữ nguyên dữ liệu

## Phân quyền chi tiết

| Vai trò | Quyền           | Mô tả                                         |
|:--------|:----------------|:----------------------------------------------|
| Kế toán | `DDCGHM.DELETE` | Có quyền xóa chứng từ điều chỉnh giá hàng mua |

## Liên kết

- Activity Diagram: [AD_DCGHM_Xoa.puml](AD_DCGHM_Xoa.puml)
- Form/Screen: [SCR_DCGHM_DanhSach.md](../../5.screens/SCR_DCGHM_DanhSach.md), [SCR_DCGHM_Xoa.md](../../5.screens/SCR_DCGHM_Xoa.md)
- Use case liên quan: **UC_DCGHM_XemDanhSach**
- Entity liên quan: **ENT_ChungTuDieuChinhGiaHangMua**, **ENT_ChiTietChungTuDieuChinhGiaHangMua**, **ENT_HoaDonDieuChinh**, **ENT_ChungTuThuTien**, **ENT_ChungTuChiTien**.
