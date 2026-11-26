# Ecopark Bicycle Parking — Bàn giao Thành viên 3

**Dự thảo ngày 26/11/2026.** Nội dung dựa trên phân công Messenger, repo nền Ecopark và nhánh Thành viên 2. Các quy tắc còn mở và môi trường Chương 5 cần xác nhận trước khi chốt báo cáo.

| Tệp | Sử dụng |
|---|---|
| [Chương 4](chapter-4-design.md) | Đọc, góp ý nội dung và xem sơ đồ trong ngữ cảnh |
| [Chương 4 LaTeX](chapter-4-design.tex) | Ghép vào báo cáo Inscrive cùng các PNG trong `figures/` |
| [Nguồn 13 sơ đồ](figures/ecopark-design.drawio) | Mở bằng diagrams.net để chỉnh sửa sơ đồ |
| [ERD và từ điển dữ liệu](database/database-design.md) | Thành viên 4 dùng để đối chiếu schema và lập kiểm thử |
| [Truy vết UC](uc-design-traceability.md) | Đối chiếu mã của Thành viên 1 và 2 với thiết kế |
| [Đầu vào và câu hỏi mở](design-assumptions.md) | Kiệt, Minh và Thành viên 4 rà quyết định còn thiếu |

Bản hiện tại mô tả bốn UC lõi (gửi yêu cầu UC007, bàn giao UC010, ghi nhận trả và lập phiếu UC011, tính phí UC012). Mỗi UC có biểu đồ lớp và sequence. Bộ hình còn có hai sơ đồ kiến trúc, một biểu đồ lớp tổng hợp, một ERD và một sơ đồ trạng thái xe/lượt thuê.

## Ghép vào Inscrive

Chép `chapter-4-design.tex` và thư mục `figures/` vào dự án. Tại vị trí Chương 4 gọi `\input{chapter-4-design}`. Bản LaTeX dùng `graphicx` và cấp tiêu đề của lớp `report` hoặc `book`. Nếu dự án dùng `article`, đổi các cấp tiêu đề theo mẫu đang dùng. Giữ thứ tự ảnh và dùng hệ thống đánh số của tài liệu chính.

Khi rà với Minh, xác nhận lifeline và thống nhất bản sequence cuối để ghép báo cáo. Khi Thành viên 4 xác nhận môi trường triển khai, cập nhật mục 4.1.2 và sơ đồ tương ứng. Các câu hỏi theo mã trong tài liệu nhóm cho biết vị trí cần sửa sau khi nhóm chốt.
