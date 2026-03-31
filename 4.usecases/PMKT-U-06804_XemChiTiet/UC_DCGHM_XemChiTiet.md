# Use Case: UC_DCGHM_XemChiTiet - Xem chi tiết chứng từ điều chỉnh giá hàng mua

## User Story

- Là **Kế toán**, tôi muốn xem chi tiết chứng từ điều chỉnh giá hàng mua để kiểm tra thông tin, trạng thái và thực hiện các thao tác liên quan
- Tôi cần thực hiện các tác vụ như ghi sổ, bỏ ghi sổ, chỉnh sửa trực tiếp từ màn hình chi tiết

## Acceptance criteria

- Hiển thị đầy đủ thông tin chứng từ
- Hiển thị các nút chức năng theo trạng thái chứng từ và quyền của người dùng
- Cho phép chuyển sang màn hình Sửa để chỉnh sửa thông tin
- Cho phép thực hiện Ghi sổ/Bỏ ghi sổ trực tiếp từ màn hình chi tiết

## Tác nhân chính

- Kế toán

## Tiền điều kiện

- Người dùng đã đăng nhập hệ thống
- Người dùng có quyền xem chi tiết chứng từ điều chỉnh giá hàng mua (Permission: `DDCGHM.VIEW`)

## Luồng chính

1. Người dùng chọn một chứng từ từ màn hình danh sách (**SCR_DCGHM_DanhSach**)
2. Người dùng bấm nút "Xem" hoặc double-click vào số chứng từ
3. Hệ thống mở màn hình Xem chi tiết (**SCR_DCGHM_ChiTiet**)
4. Hệ thống hiển thị đầy đủ thông tin chứng từ
5. Hệ thống hiển thị các nút chức năng theo trạng thái và quyền
6. Người dùng chọn nút "Hủy/Đóng" hoặc nhấn ESC
7. Hệ thống đóng màn hình và quay lại danh sách
8. Kết thúc

## Luồng phụ

### Ghi sổ từ màn hình chi tiết

1-5. Giống luồng chính
6. Nếu chứng từ ở trạng thái "Chưa ghi sổ":
   - Người dùng bấm nút "Ghi sổ"
   - Hệ thống gọi use case **UC_DCGHM_GhiSo**
   - Sau khi ghi sổ thành công, refresh màn hình

### Bỏ ghi sổ từ màn hình chi tiết

1-5. Giống luồng chính
6. Nếu chứng từ ở trạng thái "Đã ghi sổ":
   - Người dùng bấm nút "Bỏ ghi sổ"
   - Hệ thống gọi use case **UC_DCGHM_BoGhiSo**
   - Sau khi bỏ ghi sổ thành công, refresh màn hình

### Chỉnh sửa từ màn hình chi tiết

1-5. Giống luồng chính
6. Nếu chứng từ ở trạng thái "Chưa ghi sổ":
   - Người dùng bấm nút "Chỉnh sửa"
   - Hệ thống mở màn hình Sửa (**SCR_DCGHM_Sua**) với thông tin chứng từ
   - Người dùng chỉnh sửa và lưu (theo use case **UC_DCGHM_Sua**)
   - Sau khi lưu thành công, quay lại màn hình chi tiết

## Ngoại lệ

| Trường hợp          | Xử lý                    | Messages                         |
|:--------------------|:-------------------------|:---------------------------------|
| Không có quyền      | Không hiển thị tính năng |                                  |
| Lỗi khi tải dữ liệu | Hiển thị thông báo lỗi   | "Lỗi hệ thống, vui lòng thử lại" |

## Hậu điều kiện

- **Thành công**: Hiển thị đầy đủ thông tin chứng từ
- **Thất bại**: Hiển thị thông báo lỗi

## Phân quyền chi tiết

| Vai trò | Quyền           | Mô tả                                              |
|:--------|:----------------|:---------------------------------------------------|
| Kế toán | `DDCGHM.VIEW`   | Có quyền xem chi tiết chứng từ điều chỉnh giá hàng mua |

## Liên kết

- Activity Diagram: [AD_DCGHM_XemChiTiet.puml](AD_DCGHM_XemChiTiet.puml)
- Form/Screen: [SCR_DCGHM_ChiTiet.md](../../5.screens/SCR_DCGHM_ChiTiet.md)
- Use case liên quan: **UC_DCGHM_XemDanhSach**, **UC_DCGHM_Sua**, **UC_DCGHM_GhiSo**, **UC_DCGHM_BoGhiSo**
- Entity liên quan: **ENT_ChungTuDieuChinhGiaHangMua**, **ENT_ChiTietChungTuDieuChinhGiaHangMua**, **ENT_HoaDonDieuChinh**, **ENT_ChungTuThuTien**, **ENT_ChungTuChiTien**, **ENT_NhaCungCap**, **ENT_VatTu**
