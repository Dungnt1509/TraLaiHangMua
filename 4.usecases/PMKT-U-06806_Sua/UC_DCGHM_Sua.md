# Use Case: UC_DCGHM_Sua - Chỉnh sửa chứng từ điều chỉnh giá hàng mua

## User Story

- Là **Kế toán**, tôi muốn chỉnh sửa thông tin chứng từ điều chỉnh giá hàng mua để cập nhật các thông tin sai sót hoặc bổ sung thông tin còn thiếu
- Tôi cần chỉ được phép chỉnh sửa chứng từ ở trạng thái "Chưa ghi sổ" để đảm bảo tính toàn vẹn dữ liệu đã ghi sổ
- Tôi cần hệ thống validate đầy đủ các điều kiện trước khi lưu

## Acceptance criteria

- Cho phép chỉnh sửa toàn bộ thông tin chứng từ ở trạng thái "Chưa ghi sổ"
- Validate đầy đủ các trường bắt buộc và điều kiện nghiệp vụ
- Hỗ trợ lưu nháp (giữ nguyên trạng thái "Chưa ghi sổ") và lưu ghi sổ
- Khi đóng form có dữ liệu chưa lưu, hiển thị popup xác nhận
- Phân quyền: Chỉ người dùng có quyền mới hiển thị chức năng chỉnh sửa

## Tác nhân chính

- Kế toán

## Tiền điều kiện

- Người dùng đã đăng nhập hệ thống
- Người dùng có quyền chỉnh sửa chứng từ điều chỉnh giá hàng mua (Permission: `DDCGHM.EDIT`)
- Chứng từ ở trạng thái "Chưa ghi sổ"

## Luồng chính

1. Người dùng chọn nút "Chỉnh sửa" từ màn hình chi tiết (**SCR_DCGHM_ChiTiet**) hoặc màn hình danh sách (**SCR_DCGHM_DanhSach**)
2. Hệ thống mở màn hình Chỉnh sửa chứng từ điều chỉnh giá hàng mua (**SCR_DCGHM_Sua**)
3. Hệ thống hiển thị thông tin hiện tại của chứng từ
4. Người dùng chỉnh sửa các thông tin cần thiết
5. Người dùng thêm, xóa, sửa các dòng chi tiết điều chỉnh trong tab Chi tiết điều chỉnh
6. Hệ thống tự động tính toán và hiển thị thông tin tổng hợp
7. Hệ thống tự động tính toán và hiển thị tab Hạch toán
8. Tùy theo hình thức thanh toán, người dùng nhập thông tin cho các tab tương ứng trong Section 2
9. Người dùng chọn nút "Lưu và ghi sổ"
10. Hệ thống validate dữ liệu (xem mục **Ngoại lệ**)
11. Nếu không vi phạm các điều kiện ngoại lệ, hệ thống lưu thông tin chứng từ với trạng thái "Đã ghi sổ"
12. Hệ thống gọi use case **UC_DCGHM_GhiSo** để ghi sổ chứng từ
13. Hệ thống hiển thị thông báo thành công
14. Hệ thống đóng màn hình và quay lại danh sách/chi tiết
15. Kết thúc

## Luồng phụ

### Lưu nháp

1-9. Giống luồng chính
9. Người dùng chọn nút "Lưu nháp" thay vì "Lưu và ghi sổ"
10. Hệ thống validate theo mục ngoại lệ
11. Nếu không vi phạm các điều kiện ngoại lệ, hệ thống cập nhật thông tin chứng từ ở trạng thái "Chưa ghi sổ"
12. Hệ thống hiển thị thông báo thành công
13. Hệ thống đóng màn hình và quay lại danh sách/chi tiết
14. Kết thúc

### Đóng form

1. Người dùng chọn nút "Hủy/Đóng" hoặc nhấn ESC
2. Nếu dữ liệu chưa thay đổi: Đóng form và quay lại danh sách/chi tiết
3. Nếu dữ liệu đã thay đổi nhưng chưa lưu: Hệ thống hiển thị popup xác nhận
4. Nếu người dùng xác nhận: Đóng form và quay lại danh sách/chi tiết
5. Nếu hủy: Ở lại form và đóng popup

## Ngoại lệ

| Trường hợp                         | Xử lý                                                    | Message                                                |
|:-----------------------------------|:---------------------------------------------------------|:-------------------------------------------------------|
| Chứng từ đã ghi sổ                | Không hiển thị nút chỉnh sửa, thông báo lỗi nếu cố gắng   | Chỉ được chỉnh sửa chứng từ chưa ghi sổ                 |
| Thiếu trường bắt buộc              | Hiển thị lỗi tại trường, focus vào trường                | Trường thông tin này là bắt buộc                       |
| Đơn giá < 0                        | Hiển thị lỗi tại dòng                                    | Đơn giá phải lớn hơn hoặc bằng 0                       |
| Thành tiền < 0                     | Hiển thị lỗi tại dòng                                    | Thành tiền phải lớn hơn hoặc bằng 0                    |
| Ngày hạch toán < Ngày chứng từ     | Hiển thị lỗi                                             | Ngày hạch toán phải lớn hơn hoặc bằng ngày chứng từ    |
| Lỗi khi lưu                        | Hiển thị lỗi, rollback                                   | Lỗi hệ thống, vui lòng thử lại                         |
| Dữ liệu thay đổi khi đóng form     | Hiển thị popup xác nhận                                  | Dữ liệu đã thay đổi, bạn có muốn đóng không?           |
| Dữ liệu chi tiết                   | Phải có ít nhất 1 dòng chi tiết điều chỉnh               | Hiển thị thông báo "Chưa có dữ liệu chi tiết điều chỉnh" |

## Hậu điều kiện

- **Lưu nháp thành công**: Chứng từ được cập nhật với trạng thái "Chưa ghi sổ"
- **Lưu và ghi sổ thành công**: Chứng từ được ghi sổ (**UC_DCGHM_GhiSo**)
- **Thất bại**: Hiển thị thông báo lỗi, dữ liệu được rollback

## Rule

**BR1**: Quy tắc check trùng số chứng từ: Kiểm tra theo Số chứng từ + Loại chứng từ trong cùng 1 quyển chứng từ của tenant (chỉ áp dụng khi ghi sổ)

**BR2**: Công thức tính giá quy đổi: Số tiền x Tỷ giá

**BR3**: Áp dụng quy tắc làm tròn trong cấu hình của tenant

**BR4**: Hình thức thanh toán cho nghiệp vụ điều chỉnh:
   - Tăng giá hàng mua → Chỉ chọn option chi tiền: Phiếu chi, Ủy nhiệm chi, Séc tiền mặt, Séc chuyển khoản
   - Giảm giá hàng mua → Chỉ chọn option thu tiền: Phiếu thu, Giấy báo có
   - Điều chỉnh tăng & giảm → Cho phép chọn 1 trong all, khi lưu validate Tổng tiền thanh toán âm/dương để xác định tạo chứng từ thu hay chi

## Phân quyền chi tiết

| Vai trò | Quyền         | Mô tả                                                 |
|:--------|:--------------|:------------------------------------------------------|
| Kế toán | `DDCGHM.EDIT` | Có quyền chỉnh sửa chứng từ điều chỉnh giá hàng mua |

## Liên kết

- Form/Screen: [SCR_DCGHM_Sua.md](../../5.screens/SCR_DCGHM_Sua.md)
- Use case liên quan: **UC_DCGHM_GhiSo**, **UC_DCGHM_XemChiTiet**, **UC_DCGHM_XemDanhSach**
- Entity liên quan: **ENT_ChungTuDieuChinhGiaHangMua**, **ENT_ChiTietChungTuDieuChinhGiaHangMua**, **ENT_HoaDonDieuChinh**, **ENT_ChungTuThuTien**, **ENT_ChungTuChiTien**, **ENT_NhaCungCap**, **ENT_VatTu**
