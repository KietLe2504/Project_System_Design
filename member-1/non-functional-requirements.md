# M1-05 — Danh mục yêu cầu phi chức năng (NFR)

**Phiên bản:** v0.1 — 2026-10-21 · **Trạng thái:** Draft

Các NFR mô tả chất lượng hoặc ràng buộc của hệ thống. Không có cam kết định lượng nào được coi là chính thức khi chưa được nhóm trưởng duyệt; các ngưỡng số dưới đây là **đề xuất**, kèm cách đo.

Trạng thái xác nhận: **Đề xuất** (chờ duyệt) · **Cần thống nhất ngưỡng** (chưa có số đo) · **Pending scope**.

| ID | Thuộc tính chất lượng | Yêu cầu | Cách kiểm tra / đánh giá | Trạng thái xác nhận |
|---|---|---|---|---|
| NFR-01 | Bảo mật — xác thực và phân quyền | (a) Mật khẩu không được lưu dưới dạng văn bản thuần. (b) Mỗi chức năng chỉ truy cập được bởi vai trò được phép: khách hàng không truy cập chức năng vận hành; nhân viên không truy cập chức năng quản trị tài khoản/bãi; chỉ nhân viên được phân quyền mới cập nhật được xe (FR-18). | Kiểm tra CSDL (trường mật khẩu đã băm); test phân quyền: đăng nhập từng vai trò và gọi chức năng của vai trò khác → phải bị từ chối. | Đề xuất |
| NFR-02 | Quyền riêng tư | Chỉ thu thập các thông tin cá nhân cần cho nghiệp vụ (danh sách trường chốt tại Q-03). Thông tin giấy tờ chỉ hiển thị cho nhân viên xử lý yêu cầu và quản trị viên; khách hàng chỉ xem được dữ liệu của chính mình. | Rà soát danh sách trường dữ liệu so với Q-03; test: khách hàng A không xem được hồ sơ/lịch sử của khách hàng B. | Đề xuất — phụ thuộc Q-03 |
| NFR-03 | Toàn vẹn dữ liệu | Một xe không được đồng thời thuộc nhiều lượt thuê đang hoạt động; một xe không ở trạng thái "Sẵn sàng" thì không được nhận yêu cầu thuê mới. | Test đồng thời: hai nhân viên bàn giao cùng một xe gần như cùng lúc → chỉ một thao tác thành công. Kiểm tra dữ liệu: không tồn tại xe có > 1 lượt thuê đang hoạt động. | Đề xuất |
| NFR-04 | Tính nhất quán | Khi giao xe, trả xe hoặc cập nhật xe, trạng thái xe, trạng thái lượt thuê và bãi hiện tại phải được cập nhật cùng nhau; nếu một bước lỗi thì không bước nào được ghi nhận. | Test mô phỏng lỗi giữa chừng → kiểm tra dữ liệu không ở trạng thái lệch (ví dụ lượt thuê đã kết thúc nhưng xe vẫn "Đang thuê"). | Đề xuất |
| NFR-05 | Khả dụng / xử lý lỗi | Khi thao tác thất bại (mất kết nối, dữ liệu không hợp lệ, xung đột), hệ thống phải hiển thị thông báo lỗi nêu nguyên nhân và không làm mất dữ liệu người dùng đã nhập ở các biểu mẫu chính (đăng ký, gửi yêu cầu thuê, ghi nhận trả xe); người dùng có thể thử lại. | Test thủ công các kịch bản lỗi trên 3 biểu mẫu chính. | Đề xuất |
| NFR-06 | Hiệu năng | Các thao tác tra cứu thường dùng (danh sách bãi, xe tại bãi, tra cứu xe) cần phản hồi trong ngưỡng chấp nhận được. Đề xuất ngưỡng: ≤ 2 giây với dữ liệu thử nghiệm ~20 bãi, ~500 xe, ~10.000 lượt thuê, ≤ 20 người dùng đồng thời. | Đo thời gian phản hồi bằng công cụ trình duyệt hoặc công cụ kiểm thử tải trên bộ dữ liệu thử nghiệm; lấy giá trị phân vị 95. | Cần thống nhất ngưỡng |
| NFR-07 | Dễ sử dụng | Mỗi bước trong luồng tìm xe, gửi yêu cầu, bàn giao, trả xe phải hiển thị trạng thái hiện tại (ví dụ "Chờ bàn giao", "Đang thuê", "Đã trả") và thông báo kết quả thành công/thất bại. Thông báo lỗi chỉ rõ trường sai và cách sửa. | Kiểm tra theo checklist trên từng màn hình; thử nghiệm với 3–5 người dùng không thuộc nhóm thực hiện các tác vụ chính mà không cần hướng dẫn. | Đề xuất |
| NFR-08 | Tương thích | Hỗ trợ phiên bản hiện hành của các trình duyệt phổ biến (đề xuất: Chrome, Edge, Safari, Firefox) và hiển thị dùng được ở chiều rộng màn hình điện thoại (~360 px) đến máy tính. | Test trên danh sách trình duyệt/kích thước đã chốt. | Cần thống nhất — phụ thuộc Q-12 |
| NFR-09 | Khả năng bảo trì | Mã nguồn tổ chức theo cấu trúc phân lớp thống nhất, có README hướng dẫn cài đặt/chạy; biểu phí và tham số phụ thu/ưu đãi được cấu hình, không viết cứng trong mã. | Rà soát mã nguồn và tài liệu; thử: thành viên không viết module đó tự cài đặt và chạy theo README. | Đề xuất |
| NFR-10 | Sao lưu / khôi phục | Dữ liệu cần được sao lưu định kỳ và có quy trình khôi phục. Tần suất sao lưu do nhóm quyết định. | Thực hiện sao lưu và khôi phục thử trên môi trường kiểm thử, so sánh dữ liệu. | Pending scope |

## Phân biệt NFR và FR

- "Quản lý xe" là chức năng (FR-17, FR-18); "chỉ nhân viên được phân quyền mới được cập nhật xe" là ràng buộc bảo mật → NFR-01.
- "Tính phí" là chức năng (FR-12); "biểu phí có thể cấu hình, không viết cứng" là ràng buộc bảo trì → NFR-09.
