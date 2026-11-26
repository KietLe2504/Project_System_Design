# Đầu vào và quyết định thiết kế cần xác nhận

Bản ngày 26/11/2026 cho nhóm PTTKHT. Trạng thái của tài liệu là dự thảo thiết kế.

## Nguồn đã dùng

| Nguồn | Cách áp dụng |
|---|---|
| `member_3_task_specification.md`, tệp Kiệt gửi trong Messenger | Cấu trúc 4.1–4.3, ERD, truy vết và phạm vi bàn giao |
| `member_1_task_specification.md` | Phạm vi giao việc. Mã FR/NFR và Q được ưu tiên đối chiếu với [tài liệu Thành viên 1](https://github.com/KietLe2504/Project_System_Design/blob/62dbda64/member-1/business-rules.md) |
| `member_2_task_specification.md` | Phạm vi giao việc. Mã UC, luồng, trạng thái và thuật ngữ ưu tiên theo [nhánh của Minh](https://github.com/KietLe2504/Project_System_Design/blob/4d9c14bb19b76ef307252a23188248446794571f/member-2/README.md) |
| Báo cáo so sánh ngày 09/10 | Bối cảnh tái sử dụng Ecopark và các mâu thuẫn đã phát hiện |
| README, `server/app.js`, `server/db.js`, `server/pricing.js` tại snapshot Ecopark | Đối chiếu hành vi cũ, stack và tên trạng thái. Snapshot thuộc bài nền |
| Bản guideline gốc, phê duyệt nghiệp vụ cuối và project Inscrive | Chưa xác minh khi hợp nhất vào báo cáo. Các quy tắc đang mở giữ nguyên trạng thái |

[Nhóm Messenger](https://www.facebook.com/messages/t/1382741250702561) · [Snapshot Ecopark](https://github.com/sontungkieu/2025.2-IT3180E-SE/tree/d82aea68d5bcda57f5eb04a7def3d763eea6d568)

## Giả định làm việc

- Web responsive, Node.js một tiến trình và SQLite là cấu hình tham chiếu theo repo cũ. Thành viên 4 xác nhận cấu hình sẽ dùng ở Chương 5.
- Giữ cấu trúc tách yêu cầu, lượt thuê, cọc và phiếu. Sơ đồ lớp dùng tên cho trách nhiệm logic để Thành viên 4 ánh xạ vào mã.
- Làm sâu bốn UC trong chuỗi thuê–trả theo ưu tiên của file Thành viên 3. Các UC khác vẫn được truy vết. Minh xác nhận danh mục cuối và rà các nhánh sequence.
- Dùng giao dịch ghi và khóa duy nhất để thực thi bất biến cạnh tranh. Đây là thiết kế mục tiêu. Kiểm thử đồng thời thuộc phần cài đặt.
- Mô hình phí giữ các thành phần ở thời điểm phát hành. Quy tắc giá và thời điểm xét cư dân được đưa vào cấu hình nghiệp vụ sau khi nhóm chốt.

## Câu hỏi gửi Kiệt và nhóm

Các mã Q theo [bảng quy tắc của nhóm](https://github.com/KietLe2504/Project_System_Design/blob/62dbda64/member-1/business-rules.md) và [bản đối chiếu Thành viên 2](https://github.com/KietLe2504/Project_System_Design/blob/4d9c14bb19b76ef307252a23188248446794571f/member-2/open-business-rules.md).

| Mã | Cần xác nhận | Ảnh hưởng |
|---|---|---|
| Q-03, Q-10 | Dữ liệu CCCD được lưu ở mức nào? Dữ liệu GPS dùng để tìm bãi hay thêm vào giao/trả? | Quyền, hồ sơ, dữ liệu vị trí |
| Q-04, Q-20 | Chốt ghi chú giữ 10 phút, giới hạn mỗi khách, đặt trước, đổi xe, từ chối và ngừng sử dụng | UC006–UC008, UC010–UC011, UC014 |
| Q-05 | Chốt cọc ở yêu cầu hay giao xe, điều kiện hoàn, xử lý mất cọc và đối trừ | UC007–UC008, UC010–UC012, ERD |
| Q-06–Q-08, Q-15 | Chốt biểu giá, ghi chú bỏ phụ thu muộn so với FR-13, mức ưu đãi cư dân và phí hư hỏng | UC011–UC012, phiếu |
| Q-09, Q-11 | Chốt trả khác bãi, sức chứa và phạm vi bãi của nhân viên | UC010–UC011 |
| Q-12 | Xác nhận web responsive, runtime, CSDL, nơi chạy demo và môi trường Chương 5 | Kiến trúc triển khai |
| Q-13, Q-14, Q-16 | Chốt xuất báo cáo/in phiếu, nhật ký tổng quát và phân loại xe | UC006, UC019–UC020, dữ liệu |
| Phối hợp | Minh rà soát lifeline và chọn phiên bản sơ đồ cuối để chèn Chương 4.3 | Chương 4 và Inscrive |
