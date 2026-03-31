# Use Case: UC_DCGHM_BoGhiSo - Bỏ ghi sổ chứng từ điều chỉnh giá hàng mua

## User Story

- Là **Kế toán**, tôi muốn bỏ ghi sổ chứng từ điều chỉnh giá hàng mua để hoàn tác các nghiệp vụ đã ghi nhận khi ghi sổ (bút toán, giá trị tồn kho, công nợ)
- Tôi cần hệ thống tự động rollback các thay đổi và đưa chứng từ về trạng thái "Chưa ghi sổ" để có thể chỉnh sửa lại
- Tôi cần hệ thống kiểm soát điều kiện để đảm bảo chỉ bỏ ghi sổ được khi chứng từ chưa đối trừ

## Acceptance criteria

- Validate trước khi bỏ ghi sổ: chứng từ hình thức "Điều chỉnh công nợ" chưa đối trừ thủ công
- Hiển thị popup xác nhận trước khi bỏ ghi sổ
- Rollback đầy đủ các nghiệp vụ: xóa bút toán hạch toán, bỏ qua báo cáo, hoàn tác giá trị tồn kho, hoàn tác công nợ/cập nhật quỹ
- Cập nhật trạng thái chứng từ → "Chưa ghi sổ"
- Phân quyền: Chỉ người dùng có quyền mới hiển thị chức năng bỏ ghi sổ

## Tác nhân chính

- Kế toán

## Tiền điều kiện

- Người dùng đã đăng nhập hệ thống
- Người dùng có quyền bỏ ghi sổ chứng từ điều chỉnh giá hàng mua (Permission: `DDCGHM.UNPOST`)

## Luồng chính

1. Người dùng truy cập màn hình danh sách hoặc chi tiết
2. Hệ thống kiểm tra quyền bỏ ghi sổ
3. Nếu không có quyền → Không hiển thị tính năng bỏ ghi sổ, kết thúc
4. Nếu có quyền → Người dùng bấm nút "Bỏ ghi sổ"
5. Hệ thống hiển thị popup xác nhận: "Bạn có chắc muốn bỏ ghi sổ chứng từ này không?"
6. Nếu người dùng chọn "Hủy" → Đóng popup, kết thúc
7. Nếu người dùng chọn "Xác nhận" → Hệ thống validate dữ liệu (xem mục **Validate trước khi bỏ ghi sổ**)
8. Nếu validate fail → Hiển thị thông báo lỗi, không bỏ ghi sổ
9. Nếu validate pass → Hệ thống thực hiện bỏ ghi sổ:
10. Xóa bút toán hạch toán đã sinh khi ghi sổ
11. Bỏ qua chứng từ trên các báo cáo
12. Nếu Điều chỉnh giá trị hàng nhập kho = true:
    - Hoàn tác giá trị tồn kho: Giá trị mới = Giá trị hiện tại ∓ Σ(Thành tiền quy đổi) ngược hướng với ghi sổ
    - Hoàn tác giá vốn hàng tồn kho
13. Hoàn tác công nợ theo hình thức:
    - Điều chỉnh công nợ
      - Nếu đã đối trừ trực tiếp → Hoàn tác công nợ cho chứng từ gốc
      - Hoàn tác công nợ của nhà cung cấp (TĂNG/GIẢM ngược với ghi sổ)
    - Thanh toán ngay
      - Cập nhật quỹ tiền mặt tiền gửi (hoàn ứng chứng từ thu/chi đã sinh)
14. Cập nhật trạng thái chứng từ → "Chưa ghi sổ"
15. Hệ thống hiển thị thông báo bỏ ghi sổ thành công
16. Nếu gọi từ màn hình Chi tiết: Refresh màn hình
17. Nếu gọi từ màn hình danh sách: Refresh danh sách
18. Kết thúc

## Luồng phụ

Không có

## Ngoại lệ

| Trường hợp                                            | Xử lý                    | Messages                                            |
|:------------------------------------------------------|:-------------------------|:----------------------------------------------------|
| Chứng từ hình thức "Điều chỉnh công nợ" đã đối trừ thủ công | Hiển thị thông báo lỗi   | "Chứng từ đã đối trừ thủ công, không thể bỏ ghi sổ" |
| Không có quyền                                        | Không hiển thị tính năng |                                                     |
| Lỗi hệ thống khi bỏ ghi sổ                            | Hiển thị lỗi, rollback   | "Lỗi hệ thống, vui lòng thử lại"                    |

## Hậu điều kiện

- **Bỏ ghi sổ thành công**:
  - Chứng từ chuyển sang trạng thái "Chưa ghi sổ"
  - Xóa bút toán hạch toán đã sinh
  - Bỏ qua chứng từ trên các báo cáo
  - Hoàn tác giá trị tồn kho (nếu Điều chỉnh giá trị hàng nhập kho = true)
  - Hoàn tác công nợ theo hình thức (hoàn tác cho chứng từ gốc nếu đã đối trừ trực tiếp, hoặc cập nhật quỹ tiền mặt)
  - Hiển thị thông báo thành công
- **Bỏ ghi sổ thất bại**: Hiển thị thông báo lỗi, giữ nguyên trạng thái chứng từ

## Rule

**BR1**: Chứng từ hình thức "Điều chỉnh công nợ" đã đối trừ thủ công:
   - Chứng từ đã được đối trừ thủ công bởi người dùng
   - Không thể bỏ ghi sổ khi đã đối trừ thủ công

**BR2**: Nếu chứng từ hình thức "Điều chỉnh công nợ" đã đối trừ trực tiếp:
   - Hoàn tác công nợ cho chứng từ gốc khi bỏ ghi sổ

**BR3**: Công thức hoàn tác giá trị tồn kho:
- Giảm giá (ghi sổ): Hoàn tác bằng cách cộng lại giá trị
- Tăng giá (ghi sổ): Hoàn tác bằng cách trừ lại giá trị

## Phân quyền chi tiết

| Vai trò | Quyền          | Mô tả                                            |
|:--------|:---------------|:-------------------------------------------------|
| Kế toán | `DDCGHM.UNPOST` | Có quyền bỏ ghi sổ chứng từ điều chỉnh giá hàng mua |

## Liên kết

- Activity Diagram: [AD_DCGHM_BoGhiSo.puml](AD_DCGHM_BoGhiSo.puml)
- Use case liên quan: **UC_DCGHM_GhiSo**, **UC_DCGHM_XemChiTiet**, **UC_DCGHM_XemDanhSach**
- Epic liên quan: **PMKT-E-00543_DoiTruChungTu** (đối trừ chứng từ)
- Entity liên quan: **ENT_ChungTuDieuChinhGiaHangMua**, **ENT_ChiTietChungTuDieuChinhGiaHangMua**, **ENT_HoaDonDieuChinh**, **ENT_ChungTuThuTien**, **ENT_ChungTuChiTien**, **ENT_NhaCungCap**, **ENT_VatTu**, **ENT_ButToanHachToan**
