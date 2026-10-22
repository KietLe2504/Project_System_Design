# CHƯƠNG 1. ĐẶT VẤN ĐỀ

**Phiên bản:** v0.1 — 2026-10-21 · **Trạng thái:** Draft

## 1.1. Bối cảnh và hiện trạng

Ecopark là khu đô thị có diện tích rộng, nhiều tuyến đường nội khu và không gian xanh, trong đó xe đạp là phương tiện phù hợp cho việc di chuyển ngắn và hoạt động tham quan. Dịch vụ cho thuê xe đạp được tổ chức tại nhiều bãi xe phân bố ở các khu vực khác nhau. Để vận hành dịch vụ này, đơn vị quản lý cần nắm được nhiều loại thông tin: danh sách bãi xe và vị trí của từng bãi; danh sách xe cùng mã định danh, trạng thái và bãi đang chứa xe; thông tin khách hàng thuê xe; các lượt thuê đang diễn ra và đã kết thúc; các khoản phí, phụ thu và ưu đãi đã áp dụng.

Trạng thái của từng xe (đang rảnh, đang được thuê, cần sửa chữa) là thông tin cốt lõi. Nếu không biết chính xác xe nào đang rảnh, khách hàng có thể đến một bãi đã hết xe; nhân viên có thể giao nhầm một xe đang hỏng hoặc đang thuộc một lượt thuê khác; bộ phận điều hành không có căn cứ để điều chuyển xe giữa các bãi hay lên kế hoạch sửa chữa.

Khi các hoạt động tra cứu xe, bàn giao, nhận trả, tính phụ thu và tổng hợp số liệu được thực hiện thủ công (sổ ghi chép, bảng tính riêng ở từng bãi) hoặc trên dữ liệu phân tán, có thể phát sinh các khó khăn như: thông tin xe giữa các bãi không đồng bộ; thời điểm giao/trả xe ghi nhận thiếu chính xác dẫn đến sai lệch khi tính phí và phụ thu trả muộn; khó kiểm tra một khách hàng có đủ điều kiện ưu đãi cư dân hay không; mất nhiều thời gian để tổng hợp số liệu theo ngày, tháng hoặc theo bãi.

Do đó, cần một hệ thống dùng chung, trong đó dữ liệu bãi, xe, lượt thuê và tài khoản được quản lý tập trung, giúp khách hàng, nhân viên bãi xe và bộ phận điều hành cùng làm việc trên một nguồn thông tin thống nhất và được cập nhật theo từng nghiệp vụ.

> Ghi chú: các khó khăn nêu trên là những vấn đề hợp lý có thể phát sinh theo bài toán, không phải mô tả sự cố thực tế của một tổ chức cụ thể.

## 1.2. Mục tiêu hệ thống

Xét theo góc nhìn nghiệp vụ, hệ thống hướng tới các mục tiêu sau:

1. Hỗ trợ khách hàng tìm bãi xe và xe có thể thuê.
2. Hỗ trợ khách hàng gửi và theo dõi yêu cầu thuê xe.
3. Hỗ trợ nhân viên bãi xe xác minh điều kiện thuê và thực hiện giao/nhận xe.
4. Tính phí thuê và phụ thu theo quy tắc đã được thống nhất.
5. Áp dụng ưu đãi cư dân khi hồ sơ cư dân đáp ứng điều kiện xác minh.
6. Quản lý trạng thái, vị trí và lịch sử sử dụng của xe.
7. Cung cấp thống kê hoạt động cho quản trị viên/điều hành.

## 1.3. Mô tả sơ bộ chức năng

Các chức năng của hệ thống được chia thành các nhóm sau (chi tiết từng yêu cầu ở Chương 3, mục Danh mục yêu cầu chức năng):

1. **Tài khoản và hồ sơ khách hàng:** đăng ký, đăng nhập, xem và cập nhật hồ sơ; kiểm tra các thông tin định danh bắt buộc.
2. **Tra cứu bãi xe và xe:** xem danh sách bãi, vị trí bãi, tìm bãi gần người dùng, xem và lọc xe còn khả dụng.
3. **Yêu cầu thuê:** chọn xe và thời lượng, gửi yêu cầu thuê, hủy yêu cầu khi chưa được bàn giao.
4. **Bàn giao xe:** nhân viên kiểm tra yêu cầu, giấy tờ và điều kiện bàn giao; ghi nhận giao xe.
5. **Trả xe và tính phí:** nhân viên tiếp nhận xe trả, ghi nhận tình trạng xe; hệ thống tính phí thuê, phụ thu và tạo phiếu thuê/trả.
6. **Ưu đãi cư dân:** xác minh hồ sơ cư dân và áp dụng ưu đãi khi đủ điều kiện.
7. **Quản lý vận hành:** quản lý bãi xe, xe, trạng thái/vị trí xe và tài khoản.
8. **Thống kê và lịch sử:** lịch sử thuê của khách hàng, thống kê theo kỳ cho quản trị viên.

Hai chức năng *xuất báo cáo* và *nhật ký thay đổi (audit log)* đang chờ nhóm trưởng quyết định có đưa vào phạm vi hay không (xem [scope.md](scope.md), PD-01, PD-02).

## 1.4. Giải pháp sơ bộ

Nhóm đề xuất xây dựng một hệ thống phần mềm quản lý dịch vụ thuê xe đạp, gồm:

- **Giao diện dành cho khách hàng:** tra cứu bãi và xe, gửi/hủy yêu cầu thuê, xem lượt thuê đang diễn ra, lịch sử thuê và phiếu thuê/trả.
- **Giao diện vận hành dành cho nhân viên bãi xe và quản trị viên:** xử lý yêu cầu thuê, giao xe, nhận trả xe, cập nhật trạng thái xe; quản lý bãi, xe, tài khoản và xem thống kê.
- **Dữ liệu tập trung:** thông tin bãi, xe, lượt thuê, tài khoản và các khoản phí được lưu trữ và quản lý tại một nơi, bảo đảm mọi bên nhìn thấy cùng một trạng thái.

Nền tảng triển khai (web responsive hay web kèm ứng dụng mobile) đang chờ nhóm trưởng xác nhận (Q-12). Trong khi chờ, báo cáo dùng cách gọi chung là "hệ thống" và "giao diện khách hàng / giao diện vận hành".

## 1.5. Cấu trúc báo cáo

> Cần đối chiếu lại với `group-project-guideline.docx` trước khi chốt tên chương.

- **Chương 1 — Đặt vấn đề:** giới thiệu bối cảnh, nhu cầu, mục tiêu, chức năng và giải pháp sơ bộ.
- **Chương 2 — Phân tích nghiệp vụ:** mô tả vai trò nghiệp vụ, các quy trình thuê xe, trả xe, quản lý đội xe và các đối tượng nghiệp vụ.
- **Chương 3 — Đặc tả yêu cầu:** trình bày danh mục yêu cầu chức năng, phi chức năng, biểu đồ Use Case tổng quan và đặc tả chi tiết các Use Case.
- **Chương 4 — Phân tích và thiết kế hệ thống:** trình bày các biểu đồ UML ở mức thiết kế (trình tự, lớp, trạng thái…), kiến trúc và thiết kế cơ sở dữ liệu.
- **Chương 5 — Cài đặt hệ thống:** mô tả công nghệ, cấu trúc mã nguồn và môi trường triển khai.
- **Chương 6 — Kiểm thử:** trình bày kế hoạch, các test case và kết quả kiểm thử.
- **Chương 7 — Kết luận:** tổng kết kết quả đạt được, hạn chế và hướng phát triển.
