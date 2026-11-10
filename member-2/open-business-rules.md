# Quy tắc cần nhóm xác nhận

Nguồn là [bảng BR và Q của Thành viên 1](../member-1/business-rules.md) tại commit `62dbda6`. Bảng nguồn vẫn ghi `Open` cho các mục dưới đây. Các câu trả lời bổ sung ở cột “Người/ngày quyết định” được dùng làm đầu vào thiết kế dự thảo. Nhóm trưởng xác nhận và cập nhật trạng thái tại nguồn.

| Mã nguồn | Điểm cần chốt | Ảnh hưởng |
|---|---|---|
| Q-01, Q-08 | Q-01 nêu khách vãng lai/khách quen, FR-24 mô tả hồ sơ cư dân. Chốt quan hệ giữa hai khái niệm, minh chứng, người xét, hiệu lực, nộp lại, tỷ lệ và khoản tiền được giảm. FR-14 xét hồ sơ đã xác minh lúc tính phí. | UC004, UC012, UC015 |
| Q-02, Q-03 | Q-02 nêu SĐT. BR-04 còn đề xuất họ tên/mật khẩu và SĐT duy nhất. Q-03 nêu CCCD, tên, còn BR-05 chỉ ghi kết quả kiểm tra và loại giấy tờ. Chốt trường bắt buộc, khả năng sửa, số CCCD hay chỉ thông tin đối chiếu, quyền xem và việc lưu ảnh. | UC001–UC003, UC010, UC015, UC017 |
| Q-04 | Ghi chú nêu CCCD, một yêu cầu mỗi lần, giữ 10 phút từ lúc yêu cầu và cho đặt trước. Chốt mốc hết hạn, số yêu cầu/lượt đang mở, cạnh tranh với hủy/giao, thời điểm hết hạn khi đặt trước, đổi xe và việc đóng yêu cầu bị từ chối. | UC007, UC008, UC010 |
| Q-05 | Ghi chú nêu chuyển khoản, cọc bằng phí xe, xét hoàn nếu hủy trong 5 phút và lần thuê trước thành công, hoàn trong 3 phút, mất cọc nếu hết hạn không đến. Chốt mốc biên, lần thuê đầu, thời điểm xác nhận tiền, số tiền phải thu ở từng bước và ai thực hiện hoàn. BR-08 đề xuất phương án khác, hoàn khi trả xe không hư hỏng. | UC007, UC008, UC010–UC012 |
| Q-06 | Ghi chú chọn tính theo thời gian. BR-09 đề xuất gói giá cố định. Chốt phí xe, đơn giá, mốc giao/trả, đơn vị và cách làm tròn. Làm rõ vai trò thời lượng khách chọn trong FR-07 khi phí dùng thời lượng thực tế. | UC007, UC011–UC012 |
| Q-07 | Ghi chú nêu không phụ thu muộn, FR-13 và BR-10 mô tả tính phụ thu muộn. Chốt giữ hay bỏ FR-13. Nếu giữ, chốt mốc, đơn giá, làm tròn và ân hạn. Tỷ lệ trả muộn trong thống kê cần định nghĩa dù khoản phụ thu bị bỏ. | UC012, UC018 |
| Q-09 | Ghi chú cho trả khác bãi khi còn chỗ, BR-12 nêu mọi bãi đang hoạt động. Chốt điều kiện sức chứa, cách xác định còn chỗ tại lúc ghi nhận, và quyền nhân viên tại bãi trả. | UC011, UC016 |
| Q-10 | Ghi chú “Đánh dấu chú ý và theo dõi” chưa xác định cách lấy vị trí. Chốt cơ chế xếp khoảng cách, phương án thiếu GPS và vị trí có được dùng ngoài tìm bãi hay không. BR-13 đề xuất trình duyệt và lựa chọn thủ công. | UC005, FR-05 |
| Q-11 | Ghi chú xác nhận hướng phân công nhân viên theo bãi bởi quản trị viên. Chốt phạm vi xem xe, số bãi mỗi nhân viên, quyền xử lý khác bãi và việc quản trị viên có thêm quyền giao/trả hay không. FR-04 còn liệt kê nhân viên và quản trị viên xem danh sách bãi trong khi sơ đồ chỉ nối khách hàng với UC005. | UC005, UC010–UC011, UC013–UC017 |
| Q-12 | Ghi chú nêu web. Chốt trình duyệt/kích thước hỗ trợ theo NFR-08 để Thành viên 4 lập dữ liệu kiểm thử. | Các UC có giao diện |
| Q-13 | Ghi chú “Không” cần làm rõ áp dụng cho xuất báo cáo, in phiếu hay cả hai. FR-15 vẫn mô tả tạo và hiển thị phiếu. FR-22 hiện Pending scope. | UC009, UC011, UC019 |
| Q-14 | Chốt phạm vi nhật ký tổng quát và quyền tra cứu. FR-23 hiện Pending scope. Lịch sử trạng thái/vị trí xe thuộc FR-18. | UC014, UC020 |
| Q-15 | Ghi chú nêu phí hư hỏng phụ thuộc tình trạng trước chuyến và lịch sử xe, cùng đề xuất bồi thường 90% giá xe nếu mất. Chốt tiêu chí miễn/thu, cách tính, nguồn giá và phạm vi xử lý mất xe trước khi bổ sung luồng. | UC011, UC012, UC014 |
| Q-16 | Ghi chú nêu không phân loại xe. Chốt tiêu chí lọc còn lại và cập nhật FR-06 nếu cần. | UC006 |
| Q-17 | Ghi chú “Có” đối với xóa bãi, BR-16 đề xuất ngừng hoạt động thay xóa. Chốt điều kiện xóa và cách giữ liên kết lịch sử, xe, yêu cầu và lượt thuê. | UC005, UC011, UC014, UC016 |
| Q-18 | Ghi chú đồng ý BR-15. Chốt biên ngày/tuần/tháng và định nghĩa doanh thu, lượt thuê, tỷ lệ trả muộn để kiểm thử. | UC018 |
| Q-19, Q-20 | Ghi chú nêu mã xe duy nhất toàn hệ thống và có trạng thái Đã đặt. Chốt chuyển trạng thái, xử lý hết hạn/từ chối, bảo trì khi đang giữ và quyền đưa xe trở lại phục vụ. | UC006–UC008, UC010–UC011, UC013–UC014 |

## Phối hợp báo cáo

- Nhóm trưởng và Thành viên 1 đối chiếu đề bài/hướng dẫn báo cáo, chốt các Q và đồng bộ phạm vi FR-13, FR-22, FR-23.
- Thành viên 3 đối chiếu vai trò lifeline, đối tượng nghiệp vụ, nguồn thời gian và cách ghi nhận nhất quán. Repo tại commit đối chiếu có tài liệu Thành viên 1 và chưa có kiến trúc hoặc biểu đồ lớp của Thành viên 3.
- Thành viên 4 dùng kịch bản trong ma trận. Các mục ghi “Chờ” cần dữ liệu hoặc kết quả mong đợi sau khi chính sách được duyệt.
