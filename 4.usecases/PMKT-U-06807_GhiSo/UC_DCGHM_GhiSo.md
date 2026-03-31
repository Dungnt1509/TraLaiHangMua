# Use Case: UC_DCGHM_GhiSo - Ghi sổ chứng từ điều chỉnh giá hàng mua

## User Story

- Là **Kế toán**, tôi muốn ghi sổ chứng từ điều chỉnh giá hàng mua để sinh bút toán hạch toán, cập nhật giá trị hàng tồn kho (nếu điều chỉnh giá trị hàng nhập kho), cập nhật công nợ nhà cung cấp và các số liệu liên quan
- Tôi cần hệ thống tự động xử lý công nợ theo từng trường hợp (Điều chỉnh công nợ, Thanh toán ngay)
- Tôi cần hệ thống cập nhật số liệu vào chứng từ điều chỉnh, hóa đơn mua hàng gốc và các chứng từ liên quan

## Acceptance criteria

- Validate trước khi ghi sổ: có ít nhất 1 dòng chi tiết điều chỉnh, các trường bắt buộc
- Hệ thống sinh bút toán hạch toán điều chỉnh giá hàng mua
- Nếu Điều chỉnh giá trị hàng nhập kho = true: Điều chỉnh giá trị hàng tồn kho (tăng/giảm giá trị nhập kho của hàng hóa)
- Xử lý công nợ theo 2 hình thức: Điều chỉnh công nợ hoặc Thanh toán ngay với logic tương ứng
- Cập nhật trạng thái chứng từ → "Đã ghi sổ"
- Hỗ trợ cả 3 loại nghiệp vụ: Mua hàng nhập kho, Mua hàng không qua kho, Mua dịch vụ

## Tác nhân chính

- Kế toán

## Tiền điều kiện

- Người dùng đã đăng nhập hệ thống
- Người dùng có quyền ghi sổ chứng từ điều chỉnh giá hàng mua (Permission: `DDCGHM.POST`)

## Luồng chính

1. Người dùng chọn chức năng ghi sổ từ một trong 2 nơi:
   - Tại màn hình Thêm mới/Sửa (**SCR_DCGHM_ThemMoi** / **SCR_DCGHM_Sua**): Bấm nút "Lưu và ghi sổ"
   - Tại màn hình danh sách (**SCR_DCGHM_DanhSach**): Bấm nút "Ghi sổ" trên dòng chứng từ "Chưa ghi sổ"
2. Hệ thống validate dữ liệu (xem mục **Validate trước khi ghi sổ**)
3. Nếu validate fail → Hiển thị lỗi, không ghi sổ
4. Nếu validate pass → Hệ thống thực hiện ghi sổ:
5. Lưu thông tin chứng từ với trạng thái "Đã ghi sổ"
6. Sinh bút toán hạch toán điều chỉnh giá hàng mua
7. Nếu Điều chỉnh giá trị hàng nhập kho = true:
   - Điều chỉnh giá trị tồn kho: Giá trị mới = Giá trị hiện tại ± Σ(Thành tiền quy đổi) theo hướng tăng/giảm
   - Điều chỉnh giá vốn hàng tồn kho
8. Xử lý công nợ theo hình thức:
   - Điều chỉnh công nợ
     - Tăng giá: Tăng công nợ nhà cung cấp
     - Giảm giá: Giảm công nợ nhà cung cấp (hoặc đối trừ từ chứng từ khác trong **ba\PMKT-E-00543_DoiTruChungTu**)
     - Điều chỉnh tăng & giảm: Nếu tổng > 0 → Tăng công nợ, nếu tổng < 0 → Giảm công nợ
   - Thanh toán ngay
     - Không thay đổi công nợ
     - Sinh chứng từ thu tiền (Phiếu thu/Giấy báo có) hoặc chi tiền (Phiếu chi/Ủy nhiệm chi/Séc) tùy theo hướng điều chỉnh
9. Cập nhật trạng thái chứng từ → "Đã ghi sổ"
10. Hệ thống hiển thị thông báo ghi sổ thành công
11. Nếu gọi từ màn hình Thêm mới/Sửa: Đóng màn hình và quay lại danh sách
12. Nếu gọi từ màn hình danh sách: Refresh danh sách
13. Kết thúc

## Luồng phụ

Không có

## Ngoại lệ

| Trường cases | Xử lý | Messages |
|:-------------|:--------|:---------|
| Chưa có dữ liệu chi tiết | Hiển thị thông báo lỗi | "Chưa có dữ liệu chi tiết điều chỉnh" |
| Tổng tiền thanh toán = 0 | Hiển thị thông báo lỗi | "Tổng thanh toán phải khác 0" |
| Số chứng từ trùng | Hiển thị thông báo lỗi | "Số chứng từ này đã tồn tại" |
| Không có quyền | Không hiển thị tính năng | |

## Hậu điều kiện

- **Ghi sổ thành công**:
  - Chứng từ chuyển sang trạng thái "Đã ghi sổ"
  - Sinh bút toán hạch toán điều chỉnh
  - Điều chỉnh giá trị tồn kho (nếu Điều chỉnh giá trị hàng nhập kho = true)
  - Xử lý công nợ theo hình thức lựa chọn
  - Hiển thị thông báo thành công
- **Ghi sổ thất bại**: Hiển thị thông báo lỗi, rollback dữ liệu

## Rule

**BR1**: Nếu Điều chỉnh giá trị hàng nhập kho = false: Không điều chỉnh giá trị tồn kho

**BR2**: Công thức tính giá trị tồn kho mới:
- Giảm giá: Giá trị mới = Giá trị hiện tại - Σ(Thành tiền quy đổi)
- Tăng giá: Giá trị mới = Giá trị hiện tại + Σ(Thành tiền quy đổi)

**BR3**: Hình thức thanh toán cho nghiệp vụ điều chỉnh:
   - Tăng giá hàng mua → Chỉ chọn option chi tiền: Phiếu chi, Ủy nhiệm chi, Séc tiền mặt, Séc chuyển khoản
   - Giảm giá hàng mua → Chỉ chọn option thu tiền: Phiếu thu, Giấy báo có
   - Điều chỉnh tăng & Giảm → Validate Tổng tiền thanh toán âm/dương để xác định tạo chứng từ thu hay chi

## Phân quyền chi tiết

| Vai trò | Quyền        | Mô tả                                            |
|:--------|:--------------|:---------------------------------------------------|
| Kế toán | `DDCGHM.POST` | Có quyền ghi sổ chứng từ điều chỉnh giá hàng mua |

## Liên kết

- Activity Diagram: [AD_DCGHM_GhiSo.puml](AD_DCGHM_GhiSo.puml)
- Use case liên quan: **UC_DCGHM_ThemMoi**, **UC_DCGHM_Sua**, **UC_DCGHM_XemDanhSach**, **UC_DCGHM_BoGhiSo**
- Entity liên quan: **ENT_ChungTuDieuChinhGiaHangMua**, **ENT_ChiTietChungTuDieuChinhGiaHangMua**, **ENT_HoaDonDieuChinh**, **ENT_ChungTuThuTien**, **ENT_ChungTuChiTien**, **ENT_NhaCungCap**, **ENT_VatTu**
