# Màn hình: Xác nhận xóa chứng từ điều chỉnh giá hàng mua

Popup xác nhận khi người dùng thực hiện thao tác xóa chứng từ điều chỉnh giá hàng mua từ màn hình danh sách. Hỗ trợ cả xóa 1 chứng từ và xóa hàng loạt nhiều chứng từ.

## Điều kiện tiên quyết

- Người dùng đã đăng nhập
- Người dùng có quyền xóa chứng từ điều chỉnh giá hàng mua
- Người dùng bấm nút "Xóa" trên dòng chứng từ hoặc nút "Xóa hàng loạt" từ màn hình danh sách

## Nguyên mẫu

[Đang bổ sung]

## Thành phần

### Popup xác nhận xóa 1 chứng từ

<div style="overflow-x:auto">

| Thành phần            | Control | Field | Bắt buộc (Y/N) | Mô tả                                                                                                   |
|:----------------------|:--------|:------|:---------------|:--------------------------------------------------------------------------------------------------------|
| Thông báo             | text    | -     | -              | Hiển thị nội dung: **"Bạn có chắc chắn muốn xóa chứng từ này không? Thao tác này không thể hoàn tác."** |
| Nút Xác nhận          | button  | -     | -              | Khi bấm, hệ thống thực hiện xóa mềm chứng từ (IsDeleted = true)                                         |
| Nút Hủy               | button  | -     | -              | Khi bấm, đóng popup, không thực hiện xóa                                                                |
| Biểu tượng đóng popup | button  | -     | -              | Khi bấm, đóng popup, không thực hiện xóa                                                                |

</div>

### Popup xác nhận xóa hàng loạt

<div style="overflow-x:auto">

| Thành phần            | Control | Field | Bắt buộc (Y/N) | Mô tả                                                                                                             |
|:----------------------|:--------|:------|:---------------|:------------------------------------------------------------------------------------------------------------------|
| Thông báo             | text    | -     | -              | Hiển thị nội dung: **"Bạn có chắc chắn muốn xóa {n} chứng từ được chọn không? Thao tác này không thể hoàn tác."** |
| Danh sách chứng từ    | list    | -     | -              | Hiển thị danh sách các chứng từ xóa: Số chứng từ, Ngày hạch toán, Nhà cung cấp, Tổng tiền thanh toán              |
| Nút Xác nhận          | button  | -     | -              | Khi bấm, hệ thống thực hiện xóa mềm các chứng từ được chọn (IsDeleted = true)                                     |
| Nút Hủy               | button  | -     | -              | Khi bấm, đóng popup, không thực hiện xóa                                                                          |
| Biểu tượng đóng popup | button  | -     | -              | Khi bấm, đóng popup, không thực hiện xóa                                                                          |

</div>
