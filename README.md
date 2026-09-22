# [BTTH] Rà soát thiết kế CSDL đăng ký lớp tập Sportzone

> 👤 **Học viên:** Đỗ Hoàng Sơn | **Mã SV:** PTIT-HCM-066
> 🏫 **Môn học:** IT105-K25-Phan-tich-thi-t-k-h-th-ng

---

## Phần 1 — Xác định Entity/Attribute/Khóa chính

Dưới đây là bảng phân tích các thực thể, thuộc tính cần lưu trữ và khóa chính tương ứng sau khi rà soát cấu trúc CSDL của SportZone:

| Entity | Attribute cần lưu | Khóa chính (PK) |
| --- | --- | --- |
| LOP_TAP | MaLop, TenLop, HocPhi | MaLop |
| HOI_VIEN | TenHoiVien, SoDienThoai | TenHoiVien (hoặc MaHoiVien phát sinh) |
| HUAN_LUYEN_VIEN | TenHLV | TenHLV (hoặc MaHLV phát sinh) |

## Phần 2 — Xác định quan hệ và Khóa ngoại

Phân tích các mối quan hệ giữa các thực thể dựa trên quy tắc nghiệp vụ thực tế tại trung tâm thể thao:

| Cặp Entity | Loại quan hệ | Khóa ngoại đặt ở Entity nào (nếu N-N thì nêu tên bảng trung gian) |
| --- | --- | --- |
| HUAN_LUYEN_VIEN — LOP_TAP | 1-N | Đặt MaHLV làm khóa ngoại ở bảng LOP_TAP |
| HOI_VIEN — LOP_TAP | N-N | Sử dụng bảng trung gian DANG_KY (chứa MaPhieu, MaLop, TenHoiVien) |

## Phần 3 — Xử lý 2 lỗi chuẩn hóa ở mục 4

Tiến hành tách bảng để loại bỏ các vi phạm dạng chuẩn, đảm bảo tính toàn vẹn dữ liệu và tránh dị thường khi thêm/sửa/xóa:

| Lỗi ở mục 4 | Vi phạm dạng chuẩn nào | Tách thành bảng nào, gồm cột gì |
| --- | --- | --- |
| TenLop, HocPhi chỉ phụ thuộc MaLop | 2NF | Tách ra bảng LOP_TAP gồm các cột: MaLop, TenLop, HocPhi, MaHLV |
| SoDienThoai phụ thuộc TenHoiVien | 3NF | Tách ra bảng HOI_VIEN gồm các cột: TenHoiVien, SoDienThoai |

---

## 📁 Danh sách tệp tin nộp bài trong Repository
- 📝 `bt1.docx`: Báo cáo tài liệu phân tích nghiệp vụ hoàn chỉnh.
