# HCM-KS26-CNTT2_Nhap-mon-CNTT_Session11_Ex08
---

## 1. Phân tích lỗi và nguyên nhân

- **Hàng 1 gộp ô (Vi phạm Quy tắc 1):** Hàng đầu tiên phải là tiêu đề (không Merge Cells). Việc gộp ô khiến AutoFilter nhận diện sai vị trí tiêu đề, làm hỏng chức năng lọc.
- **Hàng trống giữa bảng (Vi phạm Quy tắc 4):** AutoFilter chỉ quét vùng dữ liệu liên tục. Hàng trống làm đứt gãy bảng, khiến hệ thống bỏ sót toàn bộ 120 báo cáo viên bên dưới.
- **Hàng "Tổng số" chèn ngang (Vi phạm Quy tắc 2 & 5):** Dòng thống kê phải đặt ngoài bảng. Việc chèn vào giữa làm rác kết quả lọc và phá vỡ cấu trúc "1 hàng = 1 bản ghi".
- **Ô 'Trần Thị Bình  ' có khoảng trắng (Vi phạm Quy tắc 3):** Máy tính so sánh chuỗi theo mã ASCII. Khoảng trắng được tính là 1 ký tự độc lập (mã 32). Do đó, chuỗi có khoảng trắng ở cuối hoàn toàn khác biệt với chuỗi chuẩn, khiến Filter lọc không khớp.

---

## 2. Quy trình sửa lỗi và thiết lập lọc

**Bước 1: Chuẩn hóa cấu trúc bảng**
- Bôi đen Hàng 1, tắt **Merge Cells** và chỉnh lại tiêu đề cho từng cột.
- Xóa bỏ toàn bộ các hàng trống đang cắt ngang bảng.
- Cắt (Cut) dòng "Tổng số" và dán (Paste) xuống dưới cùng, sau bản ghi cuối cùng của danh sách.

**Bước 2: Làm sạch dữ liệu bằng TRIM()**
1. Tạo cột phụ cạnh cột *Họ và Tên*, nhập công thức: `=TRIM(B4)`
2. Kéo công thức xuống hết danh sách.
3. Copy toàn bộ cột phụ $\rightarrow$ Click chuột phải vào cột *Họ và Tên* gốc $\rightarrow$ Chọn **Paste Special** $\rightarrow$ **Values** (dán đè giá trị). Xóa cột phụ.

**Bước 3: Lọc đa điều kiện (CNTT & Điểm ≥ 8.0)**
1. Chọn một ô bất kỳ trong bảng, nhấn `Ctrl + Shift + L` để bật AutoFilter mới.
2. Tại cột *Khoa / Viện*: Bỏ Select All, chỉ tích chọn **CNTT**.
3. Tại cột *Điểm Xét Duyệt*: Chọn **Filter by condition** $\rightarrow$ **Greater than or equal to** ($\ge$) $\rightarrow$ Nhập `8.0`.

```
