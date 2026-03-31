# Use Case: UC_DCGHM_ThemMoi - Thêm mới chứng từ điều chỉnh giá hàng mua

## User Story

- Là **Kế toán**, tôi muốn lập chứng từ điều chỉnh giá hàng mua để thực hiện ghi nhận nghiệp vụ điều chỉnh tăng/giảm giá hàng hóa đã mua cho nhà cung cấp
- Tôi cần thực hiện đồng thời việc điều chỉnh giá trị hàng tồn kho (nếu điều chỉnh giá hàng nhập kho) hoặc ghi nhận bút toán điều chỉnh chi phí, giá vốn (nếu hàng không qua kho)
- Tôi cần điều chỉnh công nợ phải trả nhà cung cấp (nếu giảm giá) hoặc gia tăng công nợ (nếu tăng giá) và điều chỉnh thuế GTGT đầu vào đã ghi nhận (nếu có)
- Lập kèm bộ chứng từ bao gồm: Chứng từ điều chỉnh giá hàng mua, Hóa đơn điều chỉnh, Phiếu thu/Phiếu chi/Giấy báo có/Ủy nhiệm chi/Séc tùy trường hợp

## Acceptance criteria

- Cho phép chọn chứng từ mua hàng/dịch vụ để điều chỉnh thông qua popup **SCR_DCGHM_PopupChonChungTu**. Người dùng chọn hàng hóa/dịch vụ, hệ thống auto-fill vào tab Chi tiết điều chỉnh.
- Cho phép thêm hàng hóa/dịch vụ thủ công bằng nút "Thêm dòng", nhập thông tin đầy đủ, hệ thống auto-calculate các trường liên quan.
- Hỗ trợ 3 loại nghiệp vụ: Mua hàng nhập kho, Mua hàng không qua kho, Mua dịch vụ
- Hỗ trợ 3 lý do điều chỉnh: Giảm giá hàng mua, Tăng giá hàng mua, Điều chỉnh tăng & giảm giá hàng mua
- Validate đầy đủ các điều kiện ngoại lệ.
- Hiển thị các tab trong Section 2 theo điều kiện trong mô tả màn hình.
- Hỗ trợ lưu nháp (trạng thái "Chưa ghi sổ") và lưu ghi sổ (trạng thái "Đã ghi sổ").
- Khi đóng form có dữ liệu chưa lưu, hiển thị popup xác nhận
- Phân quyền: Chỉ người dùng có quyền mới hiển thị chức năng thêm mới

## Tác nhân chính

- Kế toán

## Tiền điều kiện

- Người dùng đã đăng nhập hệ thống
- Người dùng có quyền thêm mới chứng từ điều chỉnh giá hàng mua (Permission: `DDCGHM.ADD`)

## Luồng chính

1. Người dùng chọn nút "Thêm mới" từ màn hình danh sách (**SCR_DCGHM_DanhSach**)
2. Hệ thống mở màn hình Thêm mới chứng từ điều chỉnh giá hàng mua (**SCR_DCGHM_ThemMoi**)
3. Người dùng chọn Loại nghiệp vụ (Mua hàng nhập kho / Mua hàng không qua kho / Mua dịch vụ), Lý do điều chỉnh (Giảm giá/Tăng giá/Tăng & Giảm)
4. **[Tùy chọn]** Người dùng bấm nút "Chọn chứng từ" để mở popup **SCR_DCGHM_PopupChonChungTu**
5. **[Tùy chọn]** Người dùng nhập điều kiện tìm kiếm và bấm "Tìm kiếm"
6. **[Tùy chọn]** Hệ thống hiển thị danh sách hàng hóa/dịch vụ từ các chứng từ mua hàng/mua dịch vụ
7. **[Tùy chọn]** Người dùng chọn các hàng hóa/dịch vụ cần điều chỉnh, bấm "Chọn"
8. **[Tùy chọn]** Hệ thống thêm các hàng hóa/dịch vụ đã chọn vào tab Chi tiết điều chỉnh
9. **[Tùy chọn]** Hoặc người dùng thêm hàng hóa/dịch vụ thủ công bằng cách bấm "Thêm dòng" và nhập thông tin trực tiếp
10. Người dùng thêm, xóa, sửa các dòng trong tab Chi tiết điều chỉnh
11. Hệ thống tự động tính toán và hiển thị thông tin tổng hợp (Tổng tiền hàng, Tiền thuế GTGT, Tổng thanh toán)
12. Hệ thống tự động tính toán và hiển thị tab Hạch toán
13. Tùy theo hình thức thanh toán, người dùng nhập thông tin cho các tab tương ứng trong Section 2
14. Người dùng chọn nút "Lưu và ghi sổ"
15. Hệ thống validate dữ liệu (xem mục **Ngoại lệ**)
16. Nếu không vi phạm các điều kiện ngoại lệ, hệ thống lưu thông tin chứng từ với trạng thái "Đã ghi sổ"
17. Hệ thống gọi use case **UC_DCGHM_GhiSo** để ghi sổ chứng từ
18. Hệ thống hiển thị thông báo thành công
19. Hệ thống đóng màn hình và quay lại danh sách
20. Kết thúc

## Luồng phụ

### Lưu nháp

1-14. Giống luồng chính
14. Người dùng chọn nút "Lưu nháp" thay vì "Lưu và ghi sổ"
15. Hệ thống validate theo mục ngoại lệ
16. Nếu không vi phạm các điều kiện ngoại lệ, hệ thống lưu thông tin chứng từ ở trạng thái "Chưa ghi sổ"
17. Hệ thống hiển thị thông báo thành công
18. Hệ thống đóng màn hình và quay lại danh sách
19. Kết thúc

### Đóng form

1. Người dùng chọn nút "Hủy/Đóng" hoặc nhấn ESC
2. Nếu dữ liệu chưa thay đổi: Đóng form và quay lại danh sách
3. Nếu dữ liệu đã thay đổi nhưng chưa lưu: Hệ thống hiển thị popup xác nhận
4. Nếu người dùng xác nhận: Đóng form và quay lại danh sách
5. Nếu hủy: Ở lại form và đóng popup

## Ngoại lệ

| Trườngheck Launched                                            | Xử lý                                                    | Message                                                |
|:------------------------------------------------------|:---------------------------------------------------------|:-------------------------------------------------------|
| Thiếu trường bắt buộc                                 | Hiển thị lỗi tại trường, focus vào trường                | Trường thông tin này là bắt buộc                       |
| Đơn giá < 0                                           | Hiển thị lỗi tại dòng                                    | Đơn giá phải lớn hơn hoặc bằng 0                       |
| Thành tiền < 0                     | Hiển thị lỗi tại dòng                                    | Thành tiền phải lớn hơn hoặc bằng 0                    |
| Ngày hạch toán < Ngày chứng từ                        | Hiển thị lỗi                                             | Ngày hạch toán phải lớn hơn hoặc bằng ngày chứng từ    |
| Lỗi khi lưu                                           | Hiển thị lỗi, rollback                                   | Lỗi hệ thống, vui lòng thử lại                         |
| Dữ liệu thay đổi khi đóng form                        | Hiển thị popup xác nhận                                  | Dữ liệu đã thay đổi, bạn có muốn đóng không?           |
| Dữ liệu chi tiết                                      | Phải có ít nhất 1 dòng chi tiết điều chỉnh               | Hiển thị thông báo "Chưa có dữ liệu chi tiết điều chỉnh" |

## Hậu điều kiện

- **Lưu nháp thành công**: Chứng từ được lưu với trạng thái "Chưa ghi sổ"
- **Lưu và ghi sổ thành công**: Chứng từ được ghi sổ (**UC_DCGHM_GhiSo**)
- **Thất bại**: Hiển thị thông báo lỗi, dữ liệu được rollback

## Rule

**BR1**: Quy tắc check trùng số chứng từ: Kiểm tra theo Số chứng từ + Loại chứng từ trong cùng 1 quyển chứng từ của tenant (chỉ áp dụng khi ghi sổ)

**BR2**: Không kiểm tra trùng hóa đơn

**BR3**: Công thức tính giá quy đổi: Số tiền x Tỷ giá

**BR4**: Áp dụng quy tắc làm tròn trong cấu hình của tenant

**BR5**: Hình thức thanh toán cho nghiệp vụ điều chỉnh:
   - Tăng giá hàng mua → Chỉ chọn option chi tiền: Phiếu chi, Ủy nhiệm chi, Séc tiền mặt, Séc chuyển khoản
   - Giảm giá hàng mua → Chỉ chọn option thu tiền: Phiếu thu, Giấy báo có
   - Điều chỉnh tăng & giảm → Cho phép chọn 1 trong all, khi lưu validate Tổng tiền thanh toán âm/dương để xác định tạo chứng từ thu hay chi

## Phân quyền chi tiết

| Vai trò | Quyền       | Mô tả                                         |
|:--------|:-------------|:------------------------------------------------|
| Kế toán | `DDCGHM.ADD` | Có quyền thêm mới chứng từ điều chỉnh giá hàng mua |

## Liên kết

- Activity Diagram: [AD_DCGHM_ThemMoi.puml](AD_DCGHM_ThemMoi.puml)
- Form/Screen: [SCR_DCGHM_ThemMoi.md](../../5.screens/SCR_DCGHM_ThemMoi.md), [SCR_DCGHM_PopupChonChungTu.md](../../5.screens/SCR_DCGHM_PopupChonChungTu.md)
- Use case liên quan: **UC_DCGHM_GhiSo**, **UC_DCGHM_XemDanhSach**
- Entity liên quan: **ENT_ChungTuDieuChinhGiaHangMua**, **ENT_ChiTietChungTuDieuChinhGiaHangMua**, **ENT_HoaDonDieuChinh**, **ENT_ChungTuThuTien**, **ENT_ChungTuChiTien**, **ENT_NhaCungCap**, **ENT_VatTu**
