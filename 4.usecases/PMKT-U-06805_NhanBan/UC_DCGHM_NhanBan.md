# Use Case: UC_DCGHM_NhanBan - Nhân bản chứng từ điều chỉnh giá hàng mua

## User Story

- Là **Kế toán**, tôi muốn nhân bản (copy) chứng từ điều chỉnh giá hàng mua đã có để tạo chứng từ mới nhanh chóng, không cần nhập lại toàn bộ thông tin
- Tôi cần hệ thống tự động sao chép toàn bộ thông tin từ chứng từ gốc và sinh số chứng từ mới

## Acceptance criteria

- Hỗ trợ nhân bản từ màn hình danh sách chứng từ điều chỉnh giá hàng mua
- Khi nhân bản, hệ thống tự động mở màn hình Thêm mới (**SCR_DCGHM_ThemMoi**) với dữ liệu được sao chép từ chứng từ gốc
- **Dữ liệu được sao chép**: Toàn bộ thông tin chứng từ (Lý do điều chỉnh, Điều chỉnh giá trị hàng nhập kho, Điều chỉnh công nợ/Thanh toán ngay, Hình thức thanh toán, Loại tiền, Tỷ giá, Chi tiết điều chỉnh, Hạch toán, Tham chiếu)
- **Dữ liệu KHÔNG sao chép**: Số chứng từ (sẽ tự động sinh mới), các thông tin liên quan đến hóa đơn (Mẫu số, Ký hiệu, Số hóa đơn, Ngày hóa đơn)
- Số chứng từ mới được sinh theo quy tắc sinh số chứng từ
- Trạng thái chứng từ mới: "Chưa ghi sổ"

## Tác nhân chính

- Kế toán

## Tiền điều kiện

- Người dùng đã đăng nhập hệ thống
- Người dùng có quyền xem danh sách chứng từ điều chỉnh giá hàng mua (Permission: `DDCGHM.VIEW`)
- Người dùng có quyền nhân bản chứng từ điều chỉnh giá hàng mua (Permission: `DDCGHM.COPY`)

## Luồng chính

1. Người dùng đang ở màn hình danh sách chứng từ điều chỉnh giá hàng mua (**SCR_DCGHM_DanhSach**)
2. Người dùng chọn nút "Nhân bản" trên dòng chứng từ cần nhân bản
3. Hệ thống kiểm tra quyền nhân bản chứng từ
4. Hệ thống lấy dữ liệu chi tiết của chứng từ được chọn
5. Hệ thống mở màn hình Thêm mới chứng từ điều chỉnh giá hàng mua (**SCR_DCGHM_ThemMoi**)
6. Hệ thống điền dữ liệu của chứng từ gốc vào màn hình Thêm mới
7. Hệ thống sinh số chứng từ mới theo quy tắc trong business rules chung
8. Hệ thống KHÔNG điền các thông tin liên quan đến hóa đơn (Mẫu số, Ký hiệu, Số hóa đơn, Ngày hóa đơn)
9. Người dùng tiếp tục thao tác thêm mới (có thể chỉnh sửa thông tin trước khi lưu)
10. Kết thúc

## Luồng phụ

Không có

## Ngoại lệ

| Trường hợp                | Xử lý                    | Messages                         |
|:--------------------------|:-------------------------|:---------------------------------|
| Không có quyền nhân bản   | Không hiển thị tính năng |                                  |
| Sao chép dữ liệu thất bại | Hiển thị thông báo lỗi   | "Lỗi hệ thống, vui lòng thử lại" |

## Hậu điều kiện

- **Nhân bản thành công**: Màn hình Thêm mới được mở với dữ liệu đã được sao chép, sẵn sàng lưu
- **Nhân bản thất bại**: Hiển thị thông báo lỗi tương ứng

## Rule

**BR1**: Số chứng từ mới được sinh theo quy tắc sinh số chứng từ trong business rules chung

**BR2**: Khi nhân bản, hệ thống không sao chép các thông tin liên quan đến hóa đơn (Mẫu số, Ký hiệu, Số hóa đơn, Ngày hóa đơn) vì mỗi chứng từ điều chỉnh phải liên kết với hóa đơn riêng biệt

**BR3**: Chứng từ nhân bản luôn ở trạng thái "Chưa ghi sổ", kể cả chứng từ gốc đã ghi sổ

## Phân quyền chi tiết

| Vai trò | Quyền         | Mô tả                                                 |
|:--------|:--------------|:------------------------------------------------------|
| Kế toán | `DDCGHM.COPY` | Có quyền nhân bản chứng từ điều chỉnh giá hàng mua |

## Liên kết

- Form/Screen: [SCR_DCGHM_DanhSach.md](../../5.screens/SCR_DCGHM_DanhSach.md), [SCR_DCGHM_ThemMoi.md](../../5.screens/SCR_DCGHM_ThemMoi.md)
- Use case liên quan: **UC_DCGHM_XemDanhSach**, **UC_DCGHM_ThemMoi**
- Entity liên quan: **ENT_ChungTuDieuChinhGiaHangMua**, **ENT_ChiTietChungTuDieuChinhGiaHangMua**, **ENT_HoaDonDieuChinh**, **ENT_ChungTuThuTien**, **ENT_ChungTuChiTien**, **ENT_NhaCungCap**, **ENT_VatTu**
