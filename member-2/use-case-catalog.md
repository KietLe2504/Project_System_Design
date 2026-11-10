# Danh mục ca sử dụng · Ecopark Bicycle Parking

Mã và tên theo [biểu đồ tổng quan](../member-1/use-case-overview.md). Ưu tiên lấy mức cao nhất trong các [FR liên quan](../member-1/functional-requirements.md). Mọi đặc tả đang ở dạng dự thảo.

| ID | Tên | Actor chính | Actor phụ | Mục tiêu | FR liên quan | Ưu tiên | Trạng thái |
|---|---|---|---|---|---|---|---|
| UC001 | Đăng ký tài khoản | Khách hàng | — | Tạo tài khoản khách hàng | FR-01, FR-03 | Cao | Draft |
| UC002 | Đăng nhập | Khách hàng, Nhân viên bãi xe, Quản trị viên | — | Mở hoặc kết thúc phiên truy cập theo quyền | FR-01 | Cao | Draft |
| UC003 | Cập nhật hồ sơ | Khách hàng | — | Xem và sửa phần hồ sơ được phép | FR-02, FR-03 | Cao | Draft |
| UC004 | Khai báo hồ sơ cư dân | Khách hàng | — | Nộp hồ sơ để được xét tư cách cư dân | FR-24 | Trung bình | Draft |
| UC005 | Tra cứu bãi xe | Khách hàng. Nhân viên bãi xe, Quản trị viên xem danh sách theo FR-04 | — | Xem thông tin bãi và tìm bãi theo vị trí | FR-04, FR-05 | Cao | Draft |
| UC006 | Tra cứu xe khả dụng | Khách hàng | — | Tìm xe đang sẵn sàng tại bãi | FR-06 | Cao | Draft |
| UC007 | Gửi yêu cầu thuê | Khách hàng | — | Ghi nhận yêu cầu và giữ xe theo phương án Q-04 | FR-07 | Cao | Draft |
| UC008 | Hủy yêu cầu thuê | Khách hàng | — | Hủy yêu cầu còn đủ điều kiện | FR-08 | Trung bình | Draft |
| UC009 | Xem lịch sử thuê | Khách hàng | — | Xem lượt thuê và phiếu của mình | FR-15, FR-16 | Cao | Draft |
| UC010 | Bàn giao xe | Nhân viên bãi xe | Khách hàng | Xác minh và ghi nhận bàn giao để bắt đầu lượt thuê | FR-09, FR-10 | Cao | Draft |
| UC011 | Ghi nhận trả xe | Nhân viên bãi xe | Khách hàng | Nhận xe, hoàn tất lượt thuê và lập phiếu | FR-11, FR-15 | Cao | Draft |
| UC012 | Tính phí lượt thuê | Được gọi bởi UC011 | — | Tính phí và các khoản áp dụng | FR-12, FR-13, FR-14 | Cao | Draft, FR-13 cần đối chiếu Q-07 |
| UC013 | Tra cứu xe | Nhân viên bãi xe, Quản trị viên | — | Tìm xe và xem trạng thái/bãi hiện tại | FR-17 | Cao | Draft |
| UC014 | Cập nhật trạng thái xe | Nhân viên bãi xe, Quản trị viên | — | Cập nhật trạng thái hoặc vị trí xe hợp lệ | FR-18 | Cao | Draft |
| UC015 | Xác minh hồ sơ cư dân | Quản trị viên, vai trò khác nếu Q-08 cho phép | — | Ghi nhận hồ sơ đạt hoặc bị từ chối | FR-24 | Trung bình | Draft |
| UC016 | Quản lý bãi xe | Quản trị viên | — | Thêm, sửa và ngừng hoạt động bãi theo quyền | FR-19 | Trung bình | Draft |
| UC017 | Quản lý tài khoản | Quản trị viên | — | Cấp tài khoản nhân viên, phân công bãi, khóa/mở khóa | FR-20 | Trung bình | Draft |
| UC018 | Xem thống kê | Quản trị viên | — | Theo dõi hoạt động theo kỳ và bãi | FR-21 | Trung bình | Draft |
| UC019 | Xuất báo cáo | Quản trị viên | — | Xuất kết quả thống kê nếu được duyệt | FR-22 | Thấp | Pending scope, Q-13 |
| UC020 | Tra cứu nhật ký thay đổi | Quản trị viên | — | Tra cứu các thao tác quan trọng nếu được duyệt | FR-23 | Thấp | Pending scope, Q-14 |

UC011 gọi UC012 theo quan hệ `«include»`. UC011 lập phiếu và UC009 hiển thị lại phiếu của khách. UC019 chỉ mở rộng UC018 nếu chức năng xuất được duyệt. UC002 mô tả đăng xuất như một nhánh kết thúc phiên để bao phủ FR-01. Cần đồng bộ actor xem danh sách bãi trong sơ đồ tổng quan theo FR-04.
