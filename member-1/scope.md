# M1-01 — Phạm vi hệ thống

**Phiên bản:** v0.1 — 2026-10-21 · **Trạng thái:** Draft

## 1. Tóm tắt bài toán

Khu đô thị Ecopark có nhiều bãi xe đạp cho thuê. Người dùng (khách vãng lai và cư dân) cần biết bãi nào gần, bãi nào còn xe, rồi thuê xe và trả xe tại bãi. Nhân viên bãi xe chịu trách nhiệm kiểm tra điều kiện, giao xe và tiếp nhận xe trả. Bộ phận quản trị/điều hành cần theo dõi đội xe (xe đang rảnh, đang được thuê, cần sửa chữa), các bãi xe và số liệu hoạt động.

## 2. Mục tiêu hệ thống

Hệ thống hỗ trợ:

1. Tìm bãi xe và xe có thể thuê.
2. Tạo (và hủy) yêu cầu thuê.
3. Kiểm tra điều kiện giao xe và ghi nhận bàn giao.
4. Ghi nhận trả xe, tính phí thuê và phụ thu.
5. Áp dụng ưu đãi cho cư dân đã được xác minh.
6. Quản lý dữ liệu vận hành: bãi, xe, trạng thái/vị trí xe, tài khoản, thống kê.

## 3. Nhóm người dùng chính

| # | Nhóm người dùng | Mô tả ngắn | Ghi chú mô hình hóa |
|---|---|---|---|
| 1 | Khách hàng | Người sử dụng dịch vụ thuê xe | Actor chính |
| 2 | Cư dân Ecopark | Khách hàng có hồ sơ cư dân được xác minh, được xét ưu đãi | **[Đề xuất]** mô hình hóa là *loại hồ sơ của Khách hàng*, không phải actor riêng — xem Q-01 |
| 3 | Nhân viên bãi xe | Xử lý giao/nhận xe tại bãi được phân công | Actor chính |
| 4 | Quản trị viên / Điều hành | Quản lý bãi, xe, tài khoản; xem thống kê, báo cáo | Actor chính |

## 4. Bảng In scope / Out of scope / Pending decision

### 4.1. In scope (đề xuất đưa vào phạm vi — cần nhóm trưởng duyệt)

| Mã | Chức năng | FR liên quan |
|---|---|---|
| S-01 | Đăng ký, đăng nhập, xem/cập nhật hồ sơ khách hàng | FR-01, FR-02, FR-03 |
| S-02 | Xem danh sách bãi xe và thông tin vị trí | FR-04 |
| S-03 | Tìm bãi gần người dùng | FR-05 (cơ chế vị trí: Q-10) |
| S-04 | Xem và lọc xe có thể thuê tại bãi | FR-06 |
| S-05 | Gửi / hủy yêu cầu thuê | FR-07, FR-08 |
| S-06 | Nhân viên kiểm tra yêu cầu, giấy tờ, điều kiện và giao xe | FR-09, FR-10 |
| S-07 | Nhân viên ghi nhận trả xe và tình trạng xe | FR-11 |
| S-08 | Tính phí thuê và phụ thu trả muộn | FR-12, FR-13 |
| S-09 | Xác minh hồ sơ cư dân và áp dụng ưu đãi cư dân | FR-24, FR-14 |
| S-10 | Tạo/hiển thị phiếu thuê/trả | FR-15 |
| S-11 | Lịch sử thuê của khách hàng | FR-16 |
| S-12 | Tra cứu và cập nhật trạng thái/vị trí xe | FR-17, FR-18 |
| S-13 | Quản lý thông tin bãi xe | FR-19 |
| S-14 | Quản lý tài khoản (quản trị) | FR-20 |
| S-15 | Thống kê theo kỳ | FR-21 |

### 4.2. Out of scope (đề xuất KHÔNG thực hiện trong phạm vi môn học)

Các mục dưới đây **không** được mô tả trong báo cáo như chức năng hệ thống sẽ triển khai.

| Mã | Nội dung | Lý do đề xuất loại |
|---|---|---|
| OS-01 | Ứng dụng mobile native riêng (iOS/Android) | Chưa có quyết định; tăng khối lượng — xem Q-12 |
| OS-02 | Tích hợp cổng thanh toán trực tuyến thực tế | Phụ thuộc bên thứ ba; cần quyết định — xem Q-05 |
| OS-03 | Khóa xe thông minh / IoT, theo dõi GPS xe theo thời gian thực | Ngoài phạm vi phân tích thiết kế phần mềm quản lý |
| OS-04 | Tích hợp hệ thống quản lý cư dân của Ecopark để tự động xác minh | Không có thông tin về hệ thống bên ngoài — xem Q-08 |
| OS-05 | Kế toán, xuất hóa đơn điện tử, đối soát tài chính | Ngoài nghiệp vụ cho thuê xe |
| OS-06 | Quản lý bảo dưỡng chi tiết (phụ tùng, chi phí sửa chữa, nhà cung cấp) | Hệ thống chỉ ghi nhận trạng thái "cần sửa chữa" |
| OS-07 | Đặt xe trước theo khung giờ trong tương lai (booking) | Đề bài chỉ nêu "yêu cầu thuê"; cần xác nhận — xem Q-04 |

### 4.3. Pending decision (chờ nhóm trưởng quyết định)

| Mã | Nội dung | Câu hỏi |
|---|---|---|
| PD-01 | Xuất báo cáo (file Excel/PDF) | Q-13 |
| PD-02 | Nhật ký thay đổi quan trọng (audit log) | Q-14 |
| PD-03 | Xử lý tiền đặt cọc và hoàn cọc | Q-05 |
| PD-04 | Phương thức thanh toán (tiền mặt tại bãi / chuyển khoản / trực tuyến) | Q-05 |
| PD-05 | Phạm vi dữ liệu cá nhân được lưu (CCCD, ảnh giấy tờ, SĐT…) | Q-03 |
| PD-06 | Nền tảng triển khai: web responsive hay web + mobile | Q-12 |
| PD-07 | Cho phép trả xe khác bãi | Q-09 |
| PD-08 | Cư dân là actor riêng hay thuộc tính của khách hàng | Q-01 |

## 5. Ghi chú

- Phạm vi trên được lập từ bản phân công công việc; **chưa đối chiếu đề bài chính thức**. Khi có đề bài, mục nào mâu thuẫn sẽ được sửa và ghi vào lịch sử thay đổi.
- Mọi thay đổi phạm vi phải được thông báo cho thành viên 2–4 (theo mục 8 bản phân công).
