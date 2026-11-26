# Truy vết use case đến thiết kế

Mã và phạm vi theo danh mục Thành viên 2 tại commit `4d9c14bb`. Bốn ca thuê–trả có cả biểu đồ lớp và sequence. Các ca còn lại có truy vết tới mô-đun và dữ liệu.

| UC | FR/NFR | Thành phần và lớp chính | Dữ liệu | Thiết kế |
|---|---|---|---|---|
| UC001 Đăng ký tài khoản | FR-01, 03 | AccountService, AccountRepository | users, customer_profiles | 4.1 |
| UC002 Đăng nhập | FR-01, NFR-01 | AccountService, AccountRepository | users, phiên xác thực | 4.1–4.2 |
| UC003 Cập nhật hồ sơ | FR-02, 03 | AccountService, AccountRepository | customer_profiles, users | 4.1 |
| UC004 Khai báo hồ sơ cư dân | FR-24 | AccountService, AccountRepository | customer_profiles, resident_cards | 4.1, ERD |
| UC005 Tra cứu bãi xe | FR-04, 05 | FleetService, FleetRepository | stations, bikes | 4.1 |
| UC006 Tra cứu xe khả dụng | FR-06 | FleetService, FleetRepository | bikes, stations, rental_requests | 4.1 |
| UC007 Gửi yêu cầu thuê | FR-07, NFR-03–04 | CustomerWeb, RentalService, RentalRepository, RentalRequest | customer_profiles, bikes, stations, rental_requests, cọc nếu áp dụng | 4.3.2 |
| UC008 Hủy yêu cầu thuê | FR-08, NFR-04 | RentalService, RentalRepository | rental_requests, rental_deposits nếu áp dụng | 4.2, ERD |
| UC009 Xem lịch sử thuê | FR-15, 16 | ReportingService, ReportRepository | rentals, rental_tickets | 4.1, ERD |
| UC010 Bàn giao xe | FR-09, 10, NFR-01, 03–04 | OperationsWeb, RentalService, RentalRepository, RentalRequest, Rental, Bike | staff, rental_requests, rentals, bikes, rental_deposits nếu áp dụng | 4.3.3 |
| UC011 Ghi nhận trả xe | FR-11, 15, NFR-04 | OperationsWeb, RentalService, RentalRepository, Ticket, Station | rentals, stations, bikes, rental_tickets, rental_deposits nếu áp dụng | 4.3.4 |
| UC012 Tính phí lượt thuê | FR-12, 13, 14 | RentalService, PricingService | rentals, hồ sơ cư dân và dữ liệu giá/cọc áp dụng | 4.3.5; FR-13 chờ Q-07 |
| UC013 Tra cứu xe | FR-17 | FleetService, FleetRepository | bikes, stations | 4.1 |
| UC014 Cập nhật trạng thái xe | FR-18 | FleetService, FleetRepository | bikes, stations, bike_status_logs | 4.3.6, ERD |
| UC015 Xác minh hồ sơ cư dân | FR-24 | AccountService, AccountRepository | resident_cards, customer_profiles | 4.1, ERD |
| UC016 Quản lý bãi xe | FR-19 | FleetService, FleetRepository | stations | 4.1 |
| UC017 Quản lý tài khoản | FR-20 | AccountService, AccountRepository | users, staff, customer_profiles | 4.1 |
| UC018 Xem thống kê | FR-21 | ReportingService, ReportRepository | rentals, rental_tickets, bikes, stations | 4.1, ERD |
| UC019 Xuất báo cáo | FR-22 | ReportingService, ReportRepository | kết quả thống kê | Chờ phạm vi Q-13 |
| UC020 Tra cứu nhật ký thay đổi | FR-23 | ReportingService, ReportRepository | nhật ký thao tác tổng quát | Chờ phạm vi Q-14 |

UC011 gọi UC012 để tính phí. UC011 lập phiếu, UC009 xem lại phiếu. Các nhãn điều phối yêu cầu, bàn giao và trả xe trong sequence của Thành viên 2 ánh xạ vào `RentalService`. Tính phí ánh xạ vào `PricingService`. Dữ liệu nghiệp vụ của chuỗi thuê–trả ánh xạ vào `RentalRepository`.
