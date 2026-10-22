# M1-08 — Bảng truy vết yêu cầu (Requirements Traceability Matrix)

**Phiên bản:** v0.1 — 2026-10-21 · **Trạng thái:** Draft (bản ban đầu)

Cột *UC liên quan* là **ánh xạ đề xuất** của thành viên 1, chờ thành viên 2 xác nhận. Cột *Thiết kế* và *Test case* để trống cho tới khi thành viên 3, 4 bàn giao. Không đánh dấu "Hoàn tất" khi chưa có bằng chứng từ thành viên phụ trách.

Trạng thái: `Draft` · `UC mapped` (TV2 xác nhận UC) · `Designed` (TV3 bàn giao) · `Tested` (TV4 có kết quả) · `Done` · `Pending scope`.

## 1. Truy vết yêu cầu chức năng

| FR ID | Yêu cầu | Quy tắc liên quan | UC liên quan (đề xuất) | Thành phần thiết kế | Test case | Trạng thái |
|---|---|---|---|---|---|---|
| FR-01 | Đăng ký và đăng nhập | BR-04 | UC001, UC002 | Chờ TV3 | Chờ TV4 | Draft |
| FR-02 | Xem/cập nhật hồ sơ | BR-04 | UC003 | Chờ TV3 | Chờ TV4 | Draft |
| FR-03 | Kiểm tra thông tin định danh | BR-04 | UC001, UC003 | Chờ TV3 | Chờ TV4 | Draft |
| FR-04 | Xem danh sách bãi xe | — | UC005 | Chờ TV3 | Chờ TV4 | Draft |
| FR-05 | Tìm bãi gần người dùng | BR-13 | UC005 | Chờ TV3 | Chờ TV4 | Draft |
| FR-06 | Xem và lọc xe khả dụng | BR-02 | UC006 | Chờ TV3 | Chờ TV4 | Draft |
| FR-07 | Gửi yêu cầu thuê | BR-02, BR-07, BR-09 | UC007 | Chờ TV3 | Chờ TV4 | Draft |
| FR-08 | Hủy yêu cầu thuê | BR-07 | UC008 | Chờ TV3 | Chờ TV4 | Draft |
| FR-09 | Kiểm tra điều kiện bàn giao | BR-05, BR-06, BR-08, BR-14 | UC010 | Chờ TV3 | Chờ TV4 | Draft |
| FR-10 | Ghi nhận bàn giao xe | BR-02, BR-06 | UC010 | Chờ TV3 | Chờ TV4 | Draft |
| FR-11 | Ghi nhận trả xe | BR-12, BR-17 | UC011 | Chờ TV3 | Chờ TV4 | Draft |
| FR-12 | Tính phí thuê | BR-09 | UC012 | Chờ TV3 | Chờ TV4 | Draft |
| FR-13 | Tính phụ thu trả muộn | BR-10 | UC012 | Chờ TV3 | Chờ TV4 | Draft |
| FR-14 | Áp dụng ưu đãi cư dân | BR-11 | UC012 | Chờ TV3 | Chờ TV4 | Draft |
| FR-15 | Tạo phiếu thuê/trả | BR-08 | UC011, UC009 | Chờ TV3 | Chờ TV4 | Draft |
| FR-16 | Lịch sử thuê | — | UC009 | Chờ TV3 | Chờ TV4 | Draft |
| FR-17 | Tra cứu xe | BR-01, BR-14 | UC013 | Chờ TV3 | Chờ TV4 | Draft |
| FR-18 | Cập nhật trạng thái/vị trí xe | BR-02, BR-03, BR-14 | UC014 | Chờ TV3 | Chờ TV4 | Draft |
| FR-19 | Quản lý bãi xe | BR-16 | UC016 | Chờ TV3 | Chờ TV4 | Draft |
| FR-20 | Quản lý tài khoản | BR-14 | UC017 | Chờ TV3 | Chờ TV4 | Draft |
| FR-21 | Thống kê | BR-15 | UC018 | Chờ TV3 | Chờ TV4 | Draft |
| FR-22 | Xuất báo cáo | — | UC019 | — | — | Pending scope (Q-13) |
| FR-23 | Nhật ký thay đổi | — | UC020 | — | — | Pending scope (Q-14) |
| FR-24 | Xác minh hồ sơ cư dân | BR-11 | UC004, UC015 | Chờ TV3 | Chờ TV4 | Draft |

## 2. Truy vết yêu cầu phi chức năng

| NFR ID | Thuộc tính | FR/UC chịu ảnh hưởng | Cách đánh giá | Test / bằng chứng | Trạng thái |
|---|---|---|---|---|---|
| NFR-01 | Bảo mật, phân quyền | Mọi UC; trọng tâm UC010, UC014, UC016, UC017 | Test phân quyền theo vai trò | Chờ TV4 | Draft |
| NFR-02 | Quyền riêng tư | FR-02, FR-09, FR-16 | Rà soát trường dữ liệu; test truy cập chéo | Chờ TV4 | Draft (Q-03) |
| NFR-03 | Toàn vẹn dữ liệu | FR-07, FR-10, FR-11 | Test bàn giao đồng thời | Chờ TV4 | Draft |
| NFR-04 | Tính nhất quán | FR-10, FR-11, FR-18 | Test lỗi giữa giao dịch | Chờ TV4 | Draft |
| NFR-05 | Khả dụng / xử lý lỗi | FR-01, FR-07, FR-11 | Test kịch bản lỗi | Chờ TV4 | Draft |
| NFR-06 | Hiệu năng | FR-04, FR-06, FR-17 | Đo thời gian phản hồi | Chờ TV4 | Cần thống nhất ngưỡng |
| NFR-07 | Dễ sử dụng | UC005 → UC011 | Checklist + thử nghiệm người dùng | Chờ TV4 | Draft |
| NFR-08 | Tương thích | Toàn hệ thống | Test trình duyệt/kích thước | Chờ TV4 | Draft (Q-12) |
| NFR-09 | Khả năng bảo trì | FR-12, FR-13, FR-14 | Rà soát mã nguồn, README | Chờ TV3/TV4 | Draft |
| NFR-10 | Sao lưu/khôi phục | Toàn hệ thống | Thử sao lưu và khôi phục | — | Pending scope |

## 3. Kiểm tra độ phủ (cập nhật mỗi lần nhận bàn giao)

| Kiểm tra | Kết quả v0.1 |
|---|---|
| FR chưa có UC | Không có (theo ánh xạ đề xuất) |
| UC không truy về FR nào | Không có |
| FR chưa có thiết kế | Tất cả — chờ TV3 |
| FR chưa có test case | Tất cả — chờ TV4 |
| Mục đang tranh luận / chờ phạm vi | FR-22, FR-23, NFR-10; các quy tắc BR-01 → BR-17 đều Open |
